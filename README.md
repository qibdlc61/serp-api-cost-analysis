# best serp api: How to Pick Without Overpaying — Real Cost Per 1,000 Searches, Hidden Credit Rules and When ScraperAPI Is Worth It

Most "best serp api" comparisons rank tools by headline price. That number is now misleading, for three reasons that changed within the last year: Google removed the `num=100` parameter in September 2025, so every provider paginates 10 results at a time; roughly half of tracked queries now trigger an AI Overviews block that cheaper APIs skip entirely; and Google's own Custom Search JSON API is being shut down by January 2027, pushing teams that relied on it toward third-party APIs.

So the honest answer: the best SERP API depends on what you're feeding. For pure Google results at scale for AI agents, Serper.dev sits at the bottom of the price range at $0.30–$1.00 per 1,000 requests. For the widest engine coverage, SerpApi supports 80+ engines at $75/month. For bulk rank tracking on a budget, DataForSEO starts at $0.60–$2 per 1,000. And if you need Google SERP plus e-commerce scraping plus general crawling in one credit pool — one API key, one dashboard, one bill — that's the niche **ScraperAPI** occupies, starting at $49/month with a 7-day trial of 5,000 credits and no credit card required.

> **Quick picks**
> - Testing things out first: the free trial gives you 5,000 credits for 7 days, no card needed, and every plan comes with a 7-day no-questions-asked refund after that.
> - Running Google SERP plus other scraping under one roof: Hobby at $49/month is the entry point; Startup at $149 drops the per-credit cost by 70%.
> - Production tools that must not stop mid-month: Scaling ($475) and up are the only tiers with pay-as-you-go overflow.
>
> 👉 [Start the 7-day free trial with 5,000 credits — no credit card required](https://www.scraperapi.com/?fp_ref=coupons)

## What "best" actually means for a SERP API

The right answer depends on four questions, and price is only one of them.

1. **Which engines?** If you only need Google, most providers work. If you need Yandex, Baidu, or dozens of regional engines, SerpApi's 80+ engine catalog is the reason people pay $9–$15 per 1,000 requests for it.
2. **What latency do you need?** Real-time user-facing features need sub-2-second responses. Overnight rank tracking doesn't, and queue-based pricing (like DataForSEO's) gets much cheaper when you can wait.
3. **Do you need more than SERP?** If your product also pulls Amazon listings, product pages, or anything behind Cloudflare, running separate vendors for each means separate dashboards, separate billing, and separate failure modes.
4. **How deep do you track?** Since Google killed `num=100`, grabbing the top 100 results costs 10 API calls per keyword. Multiply any headline rate by 10 before comparing rank-tracking costs — this single adjustment flips most "cheapest" rankings published before late 2025.

A third-party comparison summed up ScraperAPI's recurring presence on shortlists well: it bundles SERP endpoints, a proxy pool, JavaScript rendering, and a data pipeline into one credit economy, so teams don't buy three tools to do one job. The same review notes it isn't the cheapest for pure SERP volume — that's accurate, and the credit math below shows exactly why.

## ScraperAPI plans: the full current lineup

Here's everything on the official pricing page, including the free tier and the quoted Enterprise plan:

| Plan | Monthly | Annual (10% off) | API credits | Threads | Get started |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 | 5 | [Sign up free](https://www.scraperapi.com/?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 | [Start Hobby trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [Start Startup trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [Start Business trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [Start Scaling trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [Start Professional trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [Start Advanced trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Enterprise | Custom quote | — | 22,000,000+ | 500+ | [Contact sales](https://www.scraperapi.com/?fp_ref=coupons) |

Every paid tier includes the same core feature set: JavaScript rendering, premium residential and mobile IPs, JSON auto-parsing, rotating proxies, CAPTCHA and anti-bot handling, automatic retries, unlimited bandwidth, and the 99.9% uptime guarantee. You're not paying to unlock features as you climb tiers — you're paying for credits, concurrency, and geo-targeting range.

## The credit math every comparison skips

This is where most ScraperAPI reviews lose readers, and one Capterra reviewer put it bluntly: "the breakdown of credit costs can be confusing." Here's the part that actually matters for a SERP use case.

A Google or Bing request costs **25 credits**, not 1. LinkedIn costs 30. Amazon, Walmart, and eBay cost 5. A standard page on anything else costs 1. On top of the base cost, `render=true` adds 10, `premium=true` adds 10, and bypassing sites protected by Cloudflare, Datadome, or PerimeterX adds another 10. Parameters like `country_code`, `device_type`, `session_number`, and `output_format` are free.

Translated into real money per 1,000 Google searches (25 credits each):

| Plan | Cost per 1,000 Google SERP requests |
| --- | --- |
| Hobby ($49) | $12.25 |
| Startup ($149) | $3.73 |
| Business ($299) | $2.49 |
| Scaling ($475) | $2.38 |
| Professional ($975) | $2.32 |
| Advanced ($1,975) | $2.30 |

Two conclusions fall out of this table. First, Hobby's effective rate for Google SERP work is punishing — 100,000 credits is only about 4,000 Google searches. If SERP is your main workload, Hobby exists for light testing, not production. Second, the price curve flattens hard after Business: going from Business to Advanced costs 6.6 times more money and delivers roughly the same per-credit rate ($0.100 vs $0.092). What you're actually buying above Business is concurrency and overflow permissions.

One practical tool worth knowing before you commit: the dashboard has a **Domain Cost Estimator** that shows the exact credit cost for any URL, and a `max_cost` parameter that caps what a single request can burn. Between the two, the "surprise credit drain" problem is manageable — set `max_cost` on your riskiest calls and the worst case is a rejected request, not an empty balance.

Before choosing a tier, run your own weighted calculation. Take a representative sample of your actual target URLs, run them on free credits without flags, and see what fraction works as plain 1-credit pages. Re-run failures with rendering enabled. Only then pick the tier that covers your **peak** month — because of the rule coming up next.

## The fine print that changes which plan you should buy

Three rules sit in the docs rather than the pricing page, and each one has changed someone's plan choice.

**Credits don't roll over.** Unused credits are wiped when your subscription renews. Combined with the next rule, this means your plan has to cover your busiest month, not your average one.

**Pay-as-you-go overflow only exists on Scaling and above.** On Hobby, Startup, and Business, hitting 100% of credits means scraping stops. Your options are upgrading mid-cycle or negotiating a custom plan — there's no "keep running and settle the bill later." On Scaling, Professional, Advanced, and Enterprise, you can enable pay-as-you-go at a fixed per-credit rate up to a monthly spending cap you set. If a mid-month hard stop would break a production tool, that's the real difference between Business and Scaling, and it's worth more than the $176 price gap suggests.

Alternatively, Hobby through Professional offer opt-in **auto-upgrade**: when credits run out, your account moves to the next tier automatically. It's opt-in, so check your billing page if you want that safety net.

**Geo-targeting is tier-gated.** Hobby and Startup can target the US and EU only. Country-level targeting anywhere else requires Business ($299) or higher. If your SERP data needs Japan, Brazil, or India results, the $149 Startup plan won't do the job regardless of credit volume.

Two rules work in your favor: requests over your concurrency limit get a 429 and are turned away without charge (not queued, not billed), and you're only billed for 200 and 404 responses — a 403 or a timeout you waited out costs nothing. Failed anti-bot battles don't show up on your invoice.

On the trial and refund side, the terms are unusually forgiving. Seven days, 5,000 credits, no card, and after upgrading you still have 7 days to get a no-questions-asked refund. 👉 [Test ScraperAPI's Google endpoints on the free trial before committing to a plan](https://www.scraperapi.com/pricing?fp_ref=coupons)

## How ScraperAPI stacks up against the main alternatives

All figures below come from published 2026 comparisons; no links here, just the numbers for context.

| Provider | Entry price | Cost per 1K SERP | Free allowance | Known for |
| --- | --- | --- | --- | --- |
| ScraperAPI | $49/mo | 25 credits/request (see table above) | 5,000-credit 7-day trial | SERP + full scraping toolkit in one credit pool |
| Serper.dev | $50 top-up (50K credits) | $0.30–$1.00 | 2,500 searches | Fast, cheap Google for AI agents |
| SerpApi | $75/mo | $9–$15 | 250/mo | Widest engine coverage (80+) |
| DataForSEO | $50 deposit | $0.60–$2.00 | $1 trial credit | Bulk SERP at the lowest base rate |
| SearchApi | $40/mo | $2.86–$4.00 | 100 searches | Multi-engine plus ChatGPT/Perplexity tracking |
| Bright Data | PAYG | $1.00–$1.50 | $5 credit | Enterprise multi-engine reliability |
| Oxylabs | $49/mo | ~$1.00 | 7-day trial | Premium proxies, sub-second fast API |
| Scrapingdog | $40/mo | $0.29–$1.00 | 1,000 credits | Budget all-rounder |

Read this table honestly: on pure per-request Google cost, ScraperAPI loses to Serper.dev, DataForSEO, Scrapingdog, and Decodo. Its structured SERP endpoints also cover Google (Search, News, Shopping, Jobs) — if you need structured data from Bing, Yandex, or Baidu, you'll be looking at the raw-HTML path or a different vendor.

Where it earns its keep: if your monthly workload is, say, 500,000 Google searches plus 200,000 Amazon pages plus assorted product scrapes, doing all of it on one Startup or Business plan is simpler and often cheaper overall than stitching a dedicated SERP API to a separate scraping vendor. The credit pool is shared, the parsing is included at no extra charge, and the DataPipeline handles scheduled collection without extra infrastructure.

## Why the cheapest headline rate can cost you more

Three market changes make per-request price a worse comparator than it used to be.

The `num=100` removal on September 11, 2025 is the big one. Every provider now paginates 10 results per call, so rank tracking the top 100 costs 10 calls per keyword. A provider charging $0.50 per 1,000 shallow requests can end up costing more than a $2 provider if your actual queries need depth. Calculate at the depth you truly query.

AI Overviews is the second gap. Around half of tracked queries now show a generative block above organic results. Major platforms — SerpApi, SearchApi, DataForSEO, Bright Data — parse that block; several budget options don't, which means you're paying for an incomplete picture of the page. Before committing anywhere, check whether the AI Overviews field comes back in the response.

Third, Google's Custom Search JSON API sunsets by January 2027. Teams built on it are migrating now, and migration season is exactly when people grab the first API they find instead of the right one. If that's you, the trial-then-decide path matters more than usual.

## FAQ

**How much does ScraperAPI cost for Google SERP scraping?**
Google requests consume 25 credits each. On the Startup plan ($149/month, 1,000,000 credits), that works out to about $3.73 per 1,000 Google searches, dropping to about $2.49 on Business. Hobby's rate is roughly $12.25 per 1,000 because its per-credit price is much higher.

**Is there a free plan?**
Yes. Signing up gets you 1,000 free credits with up to 5 concurrent connections, no card required. The 7-day trial adds 5,000 credits on top, and you can ask support for extra test credits if 6,000 total isn't enough to evaluate.

**What happens when I run out of credits?**
By default scraping pauses until renewal. On Hobby through Professional you can enable auto-upgrade to move up a tier automatically; on Scaling and above you can enable pay-as-you-go overflow up to a self-set monthly cap. Unused credits never roll over either way.

**Can I get a refund?**
Yes — a 7-day no-questions-asked refund on paid plans, and you can cancel anytime from the dashboard without a cancellation fee.

**Does ScraperAPI's SERP endpoint work outside the US?**
Hobby and Startup plans cover US and EU geo-targeting only. Country-level targeting worldwide requires Business or higher.

## Which one should you actually pick

- Only need Google results to feed an AI agent, highest volume, lowest cost: the usage-based providers like Serper.dev or DataForSEO will beat ScraperAPI on raw price.
- Need Yandex, Baidu, or dozens of engines: SerpApi's coverage is the reason for its price.
- ScraperAPI makes sense when SERP is part of a broader scraping workload — e-commerce, protected sites, scheduled pipelines — and you want one key and one bill covering all of it. For that case, Startup at $149 is the sensible entry point, and Business at $299 if you need non-US geo-targeting or 100 concurrent threads.
- Whatever you choose, verify with real traffic first: run your own URL mix through the free credits, check the AI Overviews parsing, and size your plan against your peak month since credits reset at renewal.

If that third scenario describes you, 👉 [check ScraperAPI's current plans and start the 7-day, 5,000-credit free trial](https://www.scraperapi.com/pricing?fp_ref=coupons) — the refund window means you're not locking anything in on day one.
