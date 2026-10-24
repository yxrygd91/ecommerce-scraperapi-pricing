# ecommerce product data scraping: How to Pull Amazon, Walmart & eBay Product Data Without Building a Scraper — Real Credit Costs, Plan Limits, and the Cheapest Way to Start

Most people searching for ecommerce product data scraping want the same thing: reliable prices, stock status, reviews, and SKU-level data from marketplaces like Amazon, without maintaining their own proxy pool or fixing broken parsers every week. The practical answer in 2026 is a scraping API that handles the blocking layer for you. ScraperAPI is one of the credit-based options in that category — this guide walks through how it actually works for ecommerce targets, what each plan really gets you once credit costs are factored in, and the limits that only show up in the FAQ.

> **Quick picks**
> - Most readers: the 7-day free trial with **5,000 API credits, no credit card required**, is enough to test your real target URLs before paying anything. [👉 Start the free trial and test your target URLs](https://www.scraperapi.com/signup?fp_ref=coupons)
> - Serious ecommerce monitoring: **Scaling** ($475/mo, 5M credits) is the first tier with pay-as-you-go overage, so a busy promo week doesn't stall your pipeline.
> - Tight budget: the standalone free plan gives 1,000 credits with 5 concurrent connections, separate from the trial.

## Why ecommerce scraping breaks more often than general web scraping

Ecommerce scraping fails for a simple reason: retailers don't want bots reading their prices. Automated traffic now makes up more than 53% of all web traffic according to the 2026 Imperva Bad Bot Report, and retailers respond with layers that check TLS fingerprints, IP reputation, browser signals, and request patterns before a scraper ever reaches a product page. A plain HTTP request to Amazon or Walmart usually gets you a bot-detection page, not HTML.

Even when you get through, the data itself is messy. A single product page can contain 48 SKUs (12 sizes × 4 colors), each with its own price and stock status. Amazon's displayed price is the Buy Box winner's price while 15 other sellers list the same item at different prices, and the Buy Box rotates. Prices also shift by region, login state, and time of day — the same product can show $49 from one IP and $54 from another.

This is why most teams stop writing their own scrapers and pay for infrastructure that handles the blocking layer. That's the gap a scraping API fills.

## What ScraperAPI actually does for ecommerce product data

You send a URL (plus optional parameters like `render`, `premium`, or `country_code`), and ScraperAPI returns the page HTML or parsed data. Proxy rotation, headless browser rendering, CAPTCHA handling, and retries all happen behind the endpoint.

For ecommerce specifically, two features matter most:

1. **Structured Data Endpoints.** Instead of raw HTML, you can request parsed JSON for Amazon, Google, Walmart, eBay, and Redfin. Ask for an Amazon product and you get organized fields back: price, rating, BSR, images, seller info. No parser to maintain when Amazon tweaks its layout.
2. **Async Amazon Reviews API.** Reviews are pulled asynchronously by ASIN into JSON or CSV, covering Amazon storefronts well beyond the US — co.uk, de, fr, co.jp, com.au, com.ae, and more. The async flow posts a job, returns a `statusUrl`, and you collect results when the job finishes. It also supports filters like star rating and verified-purchase status.

One caveat worth knowing before you build around reviews: ScraperAPI's own documentation notes that Amazon review pages currently require a login to access, so review scraping has extra friction compared with product pages. Plan a validation step in your trial for exactly this endpoint.

If you want to see whether your specific targets work before spending anything, [👉 test the structured Amazon endpoints on the free trial](https://www.scraperapi.com/signup?fp_ref=coupons) — 5,000 credits over 7 days covers a meaningful sample of product pages and a few review jobs.

## Full plan and pricing table

All paid plans include JS rendering, premium residential and mobile IPs, JSON auto-parsing, CAPTCHA and anti-bot bypass, automatic retries, unlimited bandwidth, a 99.9% uptime guarantee, DataPipeline, and Full Crawler Access. Annual billing takes 10% off every tier.

| Plan | Monthly price (annual billing) | Credits / month | Concurrent threads | Geotargeting | Get started |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 ($44.10) | 100,000 | 20 | US & EU only | [ Buy Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 ($134.10) | 1,000,000 | 50 | US & EU only | [ Buy Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 ($269.10) | 3,000,000 | 100 | Country-level | [ Buy Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | $475 ($427.50) | 5,000,000 | 200 | Country-level | [ Buy Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 ($877.50) | 10,500,000 | 300 | Country-level | [ Buy Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 ($1,777.50) | 21,500,000 | 500 | Country-level | [ Buy Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom quote | 22,000,000+ | 500+ | Country-level | [ Contact sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Beyond the cards on the pricing page, two entry options sit in the FAQ: a 7-day trial with 5,000 credits (no card), and a free plan with 1,000 credits capped at 5 concurrent connections.

## The credit math most articles skip

Here's the part that determines whether a plan actually fits your workload: credits are a spend meter, and every request costs a variable amount.

The official pricing FAQ lays out the baseline. A standard page costs 1 credit. **Amazon costs 5 credits per request.** Google and Bing cost 25, LinkedIn 30. Sites behind Cloudflare, Datadome, or PerimeterX add 10 credits per request when the bypass fires. On top of that, parameters multiply costs: JS rendering or premium proxies take a request to 10 credits, premium plus rendering to 25, ultra-premium plus rendering to 75.

Run the numbers for a typical ecommerce job. Suppose you're monitoring 1,000 Amazon ASINs once per day for pricing:

- 1,000 requests/day × 30 days = 30,000 Amazon requests
- At 5 credits each = **150,000 credits per month**

That clears Hobby (100,000) out of the running and lands comfortably inside Startup (1,000,000). Add review scraping or JS rendering to the mix and the same workload climbs fast — rendering an Amazon page can push a single request from 5 credits toward 25 or more.

Two tools keep this from getting out of hand. The **Domain Cost Estimator** in the dashboard shows the exact credit cost for any URL before you burn quota, and the `max_cost` parameter lets you cap what any single scrape can consume. Neither gets mentioned in most comparison articles, but for ecommerce workloads they're the difference between a predictable bill and a surprise. [👉 Check per-domain credit costs and current plan pricing](https://www.scraperapi.com/pricing?fp_ref=coupons)

## Three limits that only show up in the FAQ

The pricing page looks clean; the fine print is where plan choice actually gets decided.

**Overage handling splits the plan lineup in two.** Pay-as-you-go — continuing to scrape past your credit limit at a fixed per-credit rate — is only available on Scaling, Professional, Advanced, and Enterprise. On Hobby, Startup, and Business, credits running out means scraping stops until renewal or upgrade. There's a middle path: auto-upgrade (opt-in, available from Hobby through Professional) automatically moves you to the next tier when you hit the wall, but that's a permanent plan bump, not a temporary bridge. If your request volume swings month to month — which ecommerce monitoring does, thanks to promotions and seasonal spikes — this single detail can matter more than the headline credit count.

**Geotargeting is US and EU only on the two cheapest tiers.** Hobby and Startup can't target, say, Japan or Brazil. If you're monitoring regional Amazon pricing or geo-varied prices on retail sites, Business is the first tier with country-level targeting.

**Concurrency is enforced by refusal, not queuing.** Exceed your thread limit and you get a 429 response telling you to retry — no extra charge, but no queue either. Your scraper needs retry logic built in. Related fine print: Hobby and Startup only retain 30 days of analytics history, while Business and above keep it indefinitely. If you audit usage or billing month over month, that's a real constraint.

One more thing on savings: community-maintained pricing breakdowns report a promo code **START10** that takes 10% off your first month on any paid plan, and note that most "28% off" or "50% off" codes floating around coupon aggregators simply don't work. Treat any code as unverified until it applies at checkout — the annual billing discount is the only saving confirmed on the official pricing page itself.

## Which plan fits which job

Matching workload to tier is arithmetic once you know the credit costs:

- **You scrape a few hundred pages a week from easy targets.** The free plan (1,000 credits, 5 threads) or Hobby covers it. Don't pay for more until the Domain Cost Estimator tells you otherwise.
- **Daily Amazon price monitoring on ~1,000 SKUs.** Startup at 1M credits handles 150k–300k credits of monthly Amazon spend with headroom, but remember: no PAYG. If a Black Friday surge doubles your volume, you're upgrading mid-month or waiting.
- **Multi-marketplace monitoring with reviews and rendering, or geo-specific pricing.** Business or Scaling. Scaling earns its "Most popular" tag for a specific reason — it's where overage stops being a hard stop.
- **Millions of requests monthly or 50M+ scale data pipelines.** Professional, Advanced, or a custom Enterprise quote with volume pricing.

## How ScraperAPI stacks up against the alternatives

You'll cross paths with a few other names while researching this. Apify runs a marketplace of pre-built Actors for Amazon, Shopify, and Walmart scraping, billed as a subscription plus separate compute, proxy, and storage costs — convenient if an existing Actor matches your target, messier to cost-predict at scale. Bright Data sells a Scraping Browser and ready-made datasets and is often recommended for heavily protected targets. Zyte and Oxylabs lean more enterprise. Managed ecommerce data services like DataWeBot or RealDataAPI position differently entirely — they sell delivered datasets (DataWeBot advertises a 99.9% accuracy SLA with automatic credits) rather than DIY infrastructure.

The honest framing: if you have a developer and want programmable, per-request control with structured JSON for the big marketplaces, ScraperAPI's credit model is straightforward. If you want zero code at all, a managed dataset vendor may fit better, at typically higher prices and less flexibility.

## FAQ

**How many requests do I actually get on a plan?**
It depends entirely on your targets and parameters. A standard page is 1 credit, Amazon is 5, and JS rendering or premium proxies multiply costs up to 75 credits per request. The same 100,000-credit Hobby plan can mean anywhere from roughly 1,300 fully-loaded renders to 100,000 plain requests.

**Can I scrape Amazon product reviews?**
Yes, via the async Structured Reviews API, which covers Amazon storefronts in 18+ countries and returns JSON or CSV by ASIN. The docs flag that Amazon review pages require a login, so test this endpoint specifically during your trial.

**What happens when my credits run out mid-month?**
On Hobby through Business, scraping pauses until renewal or upgrade. On Scaling and above you can enable pay-as-you-go at a fixed per-credit rate with a monthly spending cap you set. Auto-upgrade (opt-in) is available from Hobby through Professional.

**Is there a real free option?**
Two: a 7-day trial with 5,000 credits and no credit card, plus a standalone free plan with 1,000 credits and 5 concurrent connections. [👉 Compare every plan and start free](https://www.scraperapi.com/pricing?fp_ref=coupons)

**Can I cancel?**
Subscriptions can be canceled anytime. Third-party pricing guides also describe a 7-day no-questions-asked refund policy — worth confirming with support before your first renewal date, since it isn't stated on the pricing page itself.

## Before you subscribe

Two checks will save you money. First, run five or ten of your real target URLs through the trial and read the credit consumption in the dashboard — an Amazon-heavy workload consumes five times the headline request count, and that single number decides between Startup and Business. Second, decide now whether you need PAYG: if your volume has any seasonality, Scaling is the cheapest tier that won't stop mid-campaign.

If your workload is light and steady, Hobby billed annually at $44.10/month is the sensible floor, and the 10% annual discount applies across every tier. When you're ready, [👉 start with the free trial or pick your plan here](https://www.scraperapi.com/pricing?fp_ref=coupons) — the 5,000 trial credits will tell you more about your real costs than any pricing table can.
