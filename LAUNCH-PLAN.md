# Oakridge Children Services - Website Launch Plan

## Executive Summary

This document outlines the complete strategy for launching the Oakridge Children Services website, including hosting, analytics, appointment booking, and advertising with ROI tracking.

---

## 1. Hosting Options

### Option A: Netlify (Recommended for Simplicity)
**Cost:** Free tier available, Pro at $19/month

**Pros:**
- One-click deploy from GitHub
- Automatic HTTPS/SSL certificates
- Built-in form handling (no backend needed!)
- Edge CDN for fast global loading
- Easy custom domain setup
- Automatic deploys on git push

**Setup Steps:**
1. Connect GitHub repo to Netlify
2. Configure custom domain (e.g., oakridgechildrenservices.ca)
3. Enable form handling for contact form
4. Set up redirects if needed

**Form Integration:** Add `netlify` attribute to form:
```html
<form name="contact" method="POST" data-netlify="true">
```

---

### Option B: Vercel
**Cost:** Free tier available, Pro at $20/month

**Pros:**
- Excellent performance and edge network
- Easy GitHub integration
- Built-in analytics (paid tier)
- Great for future React/Next.js migration

---

### Option C: Cloudflare Pages
**Cost:** Free tier is very generous

**Pros:**
- Unlimited bandwidth on free tier
- Cloudflare's global CDN
- DDoS protection included
- Web analytics included free

---

### Option D: Traditional Hosting (Hostinger, Bluehost, etc.)
**Cost:** $3-10/month

**Pros:**
- Familiar cPanel interface
- Email hosting included
- Good if client wants branded email (info@oakridgechildrenservices.ca)

**Cons:**
- More manual setup
- Need to configure SSL manually

---

### Recommended Hosting Decision Matrix

| Priority | Best Choice | Why |
|----------|-------------|-----|
| Simplicity + Free | Netlify | Built-in forms, easy setup |
| Performance + Free | Cloudflare Pages | Best CDN, unlimited bandwidth |
| Client wants email | Traditional Host | Bundled email included |
| Future growth (app) | Vercel | Best for React/Next.js |

---

## 2. Analytics Tracking

### Google Analytics 4 (GA4) - Essential
**Cost:** Free

The website already has analytics hooks built in! Here's what we need to add:

**Implementation:**
```html
<!-- Add to <head> section of index.html -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

**Key Events to Track (already prepared in script.js):**
- CTA button clicks
- Phone number clicks
- Email link clicks
- Form submissions
- Scroll depth
- Time on page

### Enhanced Tracking Setup

**Conversion Goals to Configure in GA4:**
1. Contact form submission
2. Phone call clicks
3. Booking completed (once integrated)
4. Email link clicks

**Custom Dimensions:**
- Traffic source (organic, paid, referral)
- Device type
- Location (for local SEO insights)

---

### Google Tag Manager (GTM) - Recommended
**Cost:** Free

**Benefits:**
- Manage all tracking codes in one place
- Easy to add/remove tracking without code changes
- Built-in triggers for form submissions, clicks, scrolls
- Perfect for managing ad pixels

**What to Track via GTM:**
- Google Analytics 4
- Google Ads conversion tracking
- Facebook Pixel
- Microsoft Ads (Bing)
- Hotjar/FullStory (heatmaps)

---

### Heatmaps & Session Recording
**Recommended:** Hotjar or Microsoft Clarity

**Microsoft Clarity (Free!):**
- Heatmaps showing where users click
- Session recordings
- Insights into user behavior
- Completely free, unlimited

**Hotjar ($0-89/month):**
- More polished interface
- User feedback widgets
- Survey capabilities

---

## 3. Consultation Booking System

### Option A: Calendly (Recommended)
**Cost:** Free basic, $10-16/user/month for premium

**Features:**
- Clients select specific available times
- Automatic timezone detection
- Email/SMS reminders
- Calendar sync (Google, Outlook, iCal)
- Buffer times between appointments
- Customizable booking page

**Integration Methods:**

**Method 1: Embed Widget (Cleanest)**
```html
<!-- Replace contact form or add alongside -->
<div class="calendly-inline-widget"
     data-url="https://calendly.com/oakridge-consultations/30min"
     style="min-width:320px;height:630px;">
</div>
<script src="https://assets.calendly.com/assets/external/widget.js"></script>
```

**Method 2: Popup Button**
```html
<button onclick="Calendly.initPopupWidget({url: 'https://calendly.com/oakridge/consultation'});return false;">
  Book Your Free Consultation
</button>
```

**Method 3: Link to Calendly Page**
- Simplest, just link to hosted Calendly page

---

### Option B: Cal.com (Open Source Alternative)
**Cost:** Free self-hosted, $15/user/month hosted

**Pros:**
- Open source
- More customizable
- Can self-host for privacy
- Similar features to Calendly

---

### Option C: Acuity Scheduling (by Squarespace)
**Cost:** $16-49/month

**Pros:**
- Robust intake forms
- Payment integration
- HIPAA compliant tier available (important for healthcare!)
- Good for multiple staff members

**Note:** For a healthcare-adjacent service like ABA therapy, HIPAA compliance may be a consideration.

---

### Option D: SimplyBook.me
**Cost:** Free basic, $10-60/month premium

**Pros:**
- Very flexible
- Good for service-based businesses
- Multiple booking options

---

### Booking System Decision Matrix

| Priority | Best Choice | Why |
|----------|-------------|-----|
| Quick & Easy | Calendly | Fastest to implement |
| Budget-conscious | Cal.com (self-host) | Free and powerful |
| HIPAA Compliance | Acuity Scheduling | Healthcare-grade security |
| Multiple staff | Acuity or Calendly Teams | Role-based booking |

---

### Recommended Booking Flow

1. **Current CTA buttons** → Link to Calendly popup
2. **Promo banner** → Direct link to booking
3. **Contact section** → Keep form for general inquiries, add booking widget
4. **Mobile floating button** → Open Calendly popup

---

## 4. Advertising & ROI Tracking

### Google Ads Setup

**Campaign Types for Local Services:**

1. **Search Campaigns (Highest Intent)**
   - Keywords: "ABA therapy Brampton", "autism therapy near me", "child behavioral therapy Brampton"
   - Expected CPC: $3-8 for therapy keywords
   - Best for capturing active searchers

2. **Local Services Ads (LSAs)**
   - Pay per lead, not per click
   - Shows at top of local searches
   - Includes Google Guarantee badge
   - Perfect for service businesses

3. **Display Retargeting**
   - Show ads to people who visited but didn't book
   - Lower cost, keeps brand top of mind

**Conversion Tracking Setup:**
```html
<!-- Google Ads Conversion Tracking -->
<script>
  gtag('event', 'conversion', {
    'send_to': 'AW-XXXXXXXXXX/XXXXXXXXXXXXX',
    'value': 1.0,
    'currency': 'CAD'
  });
</script>
```

**Track These Conversions:**
- Form submission
- Booking completed
- Phone call (use call tracking)
- Direction clicks

---

### Facebook/Instagram Ads

**Campaign Types:**

1. **Lead Generation Campaigns**
   - In-platform lead forms (no website needed)
   - Lower friction for users
   - Syncs with CRM

2. **Traffic Campaigns**
   - Drive to website
   - Requires pixel tracking

3. **Awareness Campaigns**
   - Build brand recognition locally
   - Target parents in Brampton area

**Facebook Pixel Implementation:**
```html
<!-- Add to <head> -->
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window, document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', 'XXXXXXXXXXXXXXX');
  fbq('track', 'PageView');
</script>
```

**Conversion Events to Track:**
```javascript
// On form submission
fbq('track', 'Lead');

// On booking
fbq('track', 'Schedule');

// On phone click
fbq('track', 'Contact');
```

---

### Microsoft Ads (Bing)

**Why Consider:**
- Lower competition = cheaper clicks
- Older demographic often uses Bing
- Syncs with LinkedIn for B2B

---

## 5. Proving ROI to the Client

### Setting Up the ROI Dashboard

**Option A: Google Looker Studio (Free)**
Create a custom dashboard showing:
- Total website visitors
- Conversion rate (visitors → leads)
- Cost per lead by channel
- Bookings completed
- Revenue attribution

**Data Sources to Connect:**
- Google Analytics 4
- Google Ads
- Facebook Ads
- Booking system (Calendly exports)

---

### Key Metrics to Report

**Weekly/Monthly Report Template:**

| Metric | This Period | Last Period | Change |
|--------|-------------|-------------|--------|
| Website Visitors | X | X | +X% |
| Form Submissions | X | X | +X% |
| Bookings Made | X | X | +X% |
| Phone Calls | X | X | +X% |
| Ad Spend | $X | $X | - |
| Cost Per Lead | $X | $X | -X% |
| New Clients | X | X | +X% |

---

### Attribution Tracking

**UTM Parameters for All Campaigns:**
```
?utm_source=google&utm_medium=cpc&utm_campaign=aba-therapy-brampton
?utm_source=facebook&utm_medium=paid&utm_campaign=parent-awareness
?utm_source=instagram&utm_medium=paid&utm_campaign=consultation-promo
```

**Track in Booking System:**
- Pass UTM parameters to Calendly
- Record source of each booking
- Calculate true cost per acquisition

---

### Call Tracking

**Recommended: CallRail or WhatConverts**
**Cost:** $45-100/month

**How It Works:**
1. Dynamic phone number on website
2. Tracks which ad/source generated the call
3. Records calls (with consent) for quality
4. Reports alongside digital conversions

**Alternative: Google Ads Call Tracking**
- Free with Google Ads
- Uses forwarding number
- Less detailed but adequate for start

---

### Monthly ROI Report Template

```
OAKRIDGE CHILDREN SERVICES - MARKETING ROI REPORT
Period: [Month Year]

INVESTMENT
├── Google Ads: $X,XXX
├── Facebook Ads: $XXX
├── Booking System: $XX
├── Call Tracking: $XX
└── TOTAL: $X,XXX

RESULTS
├── Website Visitors: X,XXX
├── Form Submissions: XX
├── Bookings Made: XX
├── Phone Inquiries: XX
└── TOTAL LEADS: XX

PERFORMANCE
├── Cost Per Lead: $XX.XX
├── Lead to Client Rate: XX%
├── Cost Per New Client: $XXX
└── Estimated Client LTV: $X,XXX

ROI CALCULATION
├── New Clients: X
├── Average Client Value: $X,XXX
├── Revenue Generated: $XX,XXX
├── Marketing Spend: $X,XXX
└── ROI: XXX%
```

---

## 6. Implementation Roadmap

### Phase 1: Foundation (Week 1)
- [ ] Set up hosting (Netlify recommended)
- [ ] Configure custom domain
- [ ] Set up SSL certificate
- [ ] Install Google Analytics 4
- [ ] Install Google Tag Manager
- [ ] Set up Microsoft Clarity (free heatmaps)

### Phase 2: Booking System (Week 2)
- [ ] Create Calendly account
- [ ] Configure availability and booking types
- [ ] Integrate Calendly widget into website
- [ ] Update CTA buttons to open booking
- [ ] Set up email notifications
- [ ] Test booking flow thoroughly

### Phase 3: Advertising Setup (Week 3)
- [ ] Set up Google Ads account
- [ ] Create conversion actions
- [ ] Install conversion tracking
- [ ] Set up Facebook Business Manager
- [ ] Install Facebook Pixel
- [ ] Create initial campaigns

### Phase 4: Reporting (Week 4)
- [ ] Create Looker Studio dashboard
- [ ] Connect all data sources
- [ ] Set up call tracking (optional)
- [ ] Create ROI report template
- [ ] Schedule automated reports

---

## 7. Budget Recommendations

### Minimum Viable Launch
| Item | Monthly Cost |
|------|-------------|
| Hosting (Netlify Free) | $0 |
| Domain (.ca) | ~$15/year |
| Calendly (Free) | $0 |
| Google Analytics | $0 |
| Microsoft Clarity | $0 |
| **Total** | **~$1.25/month** |

### Recommended Professional Setup
| Item | Monthly Cost |
|------|-------------|
| Hosting (Netlify Pro) | $19 |
| Domain | ~$1.25 |
| Calendly Pro | $12 |
| Call Tracking | $45 |
| Google Ads Budget | $500-1000 |
| Facebook Ads Budget | $300-500 |
| **Total** | **~$900-1,600/month** |

### Premium Setup with Full Tracking
| Item | Monthly Cost |
|------|-------------|
| Hosting (Netlify Pro) | $19 |
| Domain | ~$1.25 |
| Acuity (HIPAA) | $49 |
| Call Tracking (CallRail) | $95 |
| Hotjar | $39 |
| Google Ads Budget | $1,500 |
| Facebook/IG Budget | $750 |
| Agency Management Fee | $500+ |
| **Total** | **~$3,000+/month** |

---

## 8. Quick Wins to Implement Now

### 1. Add Google Analytics (30 min)
The site is already prepped for GA4 - just need to add the tracking code.

### 2. Add Microsoft Clarity (15 min)
Free heatmaps and session recordings - invaluable for optimization.

### 3. Add Calendly Widget (1 hour)
Replace or augment the contact form with real booking capability.

### 4. Update Form to Use Netlify (30 min)
If hosting on Netlify, just add `data-netlify="true"` to the form.

### 5. Add UTM Links to All CTAs (30 min)
Start tracking which buttons get the most clicks.

---

## Next Steps

1. **Confirm hosting choice** with client
2. **Set up domain** - need client to purchase or transfer
3. **Create accounts** - GA4, GTM, Calendly, ad platforms
4. **Implement tracking** - before launching ads
5. **Test everything** - full user journey testing
6. **Launch ads** - start with small budget, optimize
7. **Report results** - weekly for first month, then monthly

---

## Questions for Client

Before proceeding, clarify with the business owner:

1. **Domain:** Do they have a domain? Preference for .ca, .com, or both?
2. **Email:** Do they need branded email (info@domain.ca)?
3. **Booking:**
   - What appointment types? (Free consultation, assessment, ongoing sessions)
   - Available hours?
   - How much notice required?
   - Multiple staff members or just one calendar?
4. **Budget:** What's the comfortable monthly ad spend to start?
5. **HIPAA:** Do they need HIPAA-compliant booking/forms?
6. **Existing accounts:** Do they have Google Business Profile, Facebook page, etc.?

---

*Document created: December 2024*
*Last updated: Launch planning phase*
