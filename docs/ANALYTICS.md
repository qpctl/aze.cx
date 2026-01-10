# Vercel Web Analytics Setup

This document explains how Vercel Web Analytics is configured in the aze.cx project.

## Overview

Vercel Web Analytics is enabled for this project to track visitor data and page views. Since this is a minimalistic HTML/CSS/JS website with no build framework, we're using the **plain HTML implementation** of Vercel Web Analytics.

## Implementation

### Prerequisites

- The project is deployed on Vercel
- Vercel Web Analytics is enabled in the Vercel dashboard for this project

### How It Works

For plain HTML sites, Vercel Web Analytics is implemented by adding two `<script>` tags to the HTML pages:

```html
<!-- Vercel Web Analytics -->
<script>
    window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

### Files Modified

The analytics scripts have been added to the following HTML files:

- **index.html** - Main page
- **404.html** - Error page

Both files include the tracking scripts in the `<head>` section with a comment `<!-- Vercel Web Analytics -->` for easy identification.

## Enabling Web Analytics in Vercel Dashboard

To enable Web Analytics for this project:

1. Go to the [Vercel Dashboard](https://vercel.com/dashboard)
2. Select the **aze.cx** project
3. Click the **Analytics** tab
4. Click **Enable** in the dialog

**Note:** Enabling Web Analytics will add new routes (scoped at `/_vercel/insights/*`) after the next deployment.

## Viewing Analytics Data

Once the project is deployed and users have visited the site, you can view analytics data by:

1. Going to your [Vercel Dashboard](https://vercel.com/dashboard)
2. Selecting the **aze.cx** project
3. Clicking the **Analytics** tab

After a few days of visitor traffic, you'll be able to view and filter the analytics panels.

## Technical Notes

### Route Support

The plain HTML implementation of Vercel Web Analytics does **not** support automatic route tracking. If route tracking is needed in the future, the project would need to be migrated to a framework-based implementation (Next.js, React, Vue, etc.) that uses the framework-specific `@vercel/analytics` package.

### Verification

To verify that analytics are working correctly:

1. Visit any page on the site
2. Open the browser's Network tab (DevTools)
3. Look for a Fetch/XHR request to `/_vercel/insights/view`
4. If the request is present, analytics tracking is working correctly

## References

For more information about Vercel Web Analytics, see:
- [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics)
- [Privacy and Data Compliance](https://vercel.com/docs/analytics/privacy-policy)
- [Pricing and Limits](https://vercel.com/docs/analytics/limits-and-pricing)
