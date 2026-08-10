# TikTok API Integration by tikapis.com

Unlock instant access to all Bytedance applications at unbeatable prices, including TikTok and CapCut, with our comprehensive suite of signature and encryption features. Ensure seamless integration and optimal performance across web and iOS platforms. Our services are **completely free**.

> **X-Argus and X-Ladon are the two most critical security headers in ByteDance's mobile protocol stack.**
> This repository demonstrates how to generate both using [tikapis.com](https://tikapis.com) — the only API that keeps these fully up to date across all 59 mobile apps and both Global and China regions.

---

## X-Argus — Deep Dive

`X-Argus` is ByteDance's primary **data integrity header** sent with every authenticated mobile API request. It encodes a signed payload containing device info, timestamp, and request fingerprint. Without a valid `X-Argus`, all requests to TikTok's passport, user, and content endpoints return `10000` or signature errors.

**What it protects:**
- Device fingerprint authenticity
- Request payload integrity
- Anti-tamper detection

**How tikapis.com handles it:**
Every request routed through `mobile-api.tikapis.com` is automatically signed with a fresh `X-Argus` before forwarding. You never touch the algorithm — it runs server-side, updated the moment ByteDance changes it.

---

## X-Ladon — Deep Dive

`X-Ladon` is ByteDance's **access control header**, sitting alongside `X-Argus` on all mobile requests. It encodes a challenge-response token proving the client is a legitimate app binary.

**What it protects:**
- Unauthorized API access
- Non-app client detection
- Rate-limit bypass attempts

**How tikapis.com handles it:**
`X-Ladon` is generated in tandem with `X-Argus` — both are computed from the same device session and delivered together. No extra step required.

---

## Full Header Stack

| Header | Role | API |
|---|---|---|
| `X-Argus` | Core integrity & device signing | Mobile |
| `X-Ladon` | Access control token | Mobile |
| `X-Gorgon` | Hash-based auth layer | Mobile |
| `X-Khronos` | Replay-attack prevention via timestamp | Mobile |
| `X-Medusa` | Payload encryption | Mobile |
| `X-Helios` | Secondary payload security | Mobile |
| `X-Bogus` | Web endpoint signing | Web |
| `X-Gnarly` | Newer web signing scheme | Web |
| `_signature` | Web request signature | Web |
| `MSToken` | Web session token | Web |
| `TTEncrypt` | Transit encryption | Both |
| `MSSDK` | SDK seed, token & RI reports | Both |

---

## Captcha Solving

| Type | Method |
|---|---|
| Slide Captcha | Automated (server-side) |
| Rotate Captcha | Automated (server-side) |
| Same Object Captcha | Automated (server-side) |

---

## Supported Applications — 68 Apps Across Both APIs

### Mobile API — Global Android (24 apps)

| AID | App | Package |
|---|---|---|
| `1233` | TikTok | com.zhiliaoapp.musically |
| `1180` | TikTok (trill) | com.ss.android.ugc.trill |
| `1340` | TikTok Lite | com.zhiliaoapp.musically.go |
| `473824` | TikTok Lite | com.ss.android.ugc.tiktok.lite |
| `385522` | TikTok Now | com.ss.android.ugc.now |
| `563145` | TikTok Notes | com.ss.android.ugc.spark |
| `567753` | TikTok Studio | com.ss.android.tt.creator |
| `7743` | Seller Center | com.tiktokshop.seller |
| `4082` | TikTok TV | com.tiktok.tv |
| `364225` | Whee | com.bytedance.snail |
| `318091` | PICO | com.picovr.assistantphone.global |
| `845221` | PineDrama | com.ss.android.ttmd.video |
| `310024` | TikTok Music | com.tiktok.android.music |
| `1811` | Resso | com.moonvideo.android.resso |
| `7356` | Hypic | com.xt.retouchoversea |
| `1372` | ULike | com.gorgeous.liteinternational |
| `580589` | Lemon8 | com.bd.nproject |
| `7633` | Fanno | com.fans.magellan.android |
| `945965` | Trae | com.bytedance.trae.overseas |
| `3006` | CapCut | com.lemon.lvoverseas |
| `359289` | CapCut Pad | com.lemon.ccpadpro |
| `489823` | Dola | com.larus.wolf |
| `862354` | Pippit | com.bytedance.pippitoverseas |
| `791253` | Dreamina AI | com.lemon.dreamina |

### Mobile API — Global iOS (13 apps)

| AID | App | Package |
|---|---|---|
| `1233` | TikTok | com.zhiliaoapp.musically |
| `1180` | TikTok | com.ss.iphone.ugc.Ame |
| `473824` | TikTok Lite | com.ss.iphone.ugc.tiktok.lite |
| `385522` | TikTok Now | com.ss.iphone.ugc.now |
| `364225` | Whee | com.bytedance.snail |
| `567753` | TikTok Studio | com.ss.iphone.tt.creator |
| `845221` | PineDrama | com.ss.iphone.ttmd.video |
| `791253` | Dreamina AI | com.lemon.dreamina |
| `1372` | ULike | com.light.beautyabroad |
| `7356` | Hypic | com.xt.retouchoversea |
| `3006` | CapCut | com.lemon.lvoverseas |
| `489823` | Dola | com.bot.cici |
| `862354` | Pippit | com.bytedance.pippitoverseas |

### Mobile API — Windows (1 app)

| AID | App | Package |
|---|---|---|
| `8311` | TikTok LIVE Studio | com.ss.windows.studio |

### Mobile API — China Android (8 apps)

| AID | App | Package |
|---|---|---|
| `1128` | 抖音 Douyin | com.ss.android.ugc.aweme |
| `8663` | 抖音火山版 | com.ss.android.ugc.live |
| `2329` | 抖音极速版 | com.ss.android.ugc.aweme.lite |
| `547599` | 抖音直播伴侣 | com.ss.android.ugc.livepro |
| `8478` | 汽水音乐 Luna | com.luna.music |
| `615883` | AI抖音 | com.ss.android.ugc.aweme.hubble |
| `32` | 西瓜视频 Xigua | com.ss.android.article.video |
| `568863` | 抖音精选 | com.ss.android.ugc.aweme.select |

### Mobile API — China iOS (12 apps)

| AID | App | Package |
|---|---|---|
| `1128` | 抖音 Douyin | com.ss.iphone.ugc.Aweme |
| `2329` | 抖音极速版 | com.ss.iphone.ugc.aweme.lite |
| `1347` | 像塑 EffectCam | com.ss.ios.ugc.EffectCamera |
| `8712` | 随变 Douyin Spark | com.ss.iphone.spark |
| `615883` | AI抖音 | com.ss.iphone.ugc.aweme.hubble |
| `561124` | 抖音商城 | com.ss.iphone.ugc.Live.lite |
| `1349` | 多闪 Maya | my.maya.iphone |
| `547599` | 抖音直播伴侣 | com.ss.iphone.ugc.aweme.livepro |
| `8663` | 抖音火山版 | com.ss.iphone.ugc.Live |
| `568863` | 抖音精选 | com.ss.iphone.yumme.video |
| `8478` | 汽水音乐 | com.soda.music |
| `905678` | 抖省省 | com.ss.iphone.ugc.lifeservices |

### Web API (10 apps)

| AID | App |
|---|---|
| `1459` | TikTok Web |
| `1583` | TikTok Ads |
| `4684` | TikTok Music Web |
| `427062` | TikTok Game |
| `628463` | TikTok for Artists |
| `348188` | CapCut Web |
| `386088` | Luna PC |
| `6383` | Douyin Web |
| `4068` | TikTok Ads SSO (Tokopedia) |
| `359713` | TikTok Ads SSO (Partner) |

> Fetch the live list: `curl -H 'accept: application/json' https://mobile-api.tikapis.com/apps`

---

## RapidAPI Access

[rapidapi.com/tikapiscom/api/tiktok-tikapis-com](https://rapidapi.com/tikapiscom/api/tiktok-tikapis-com)

---

## Community & Support

- **Telegram Group:** [t.me/tikapiscom_group](https://t.me/tikapiscom_group)
- **Contact / Support:** [t.me/tikapiscom](https://t.me/tikapiscom)
- **Website:** [tikapis.com](https://tikapis.com)
- **Documentation:** [tikapis.com/documentation](https://tikapis.com/documentation)

---

## Update Log

- X-Argus & X-Ladon algorithms fully updated — 2026 builds, both Global and China regions.
- 68 apps now supported across Mobile and Web APIs.
- MSSDK seed, token and RI pipeline current across all AIDs.
