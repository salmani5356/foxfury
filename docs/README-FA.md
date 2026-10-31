# راهنمای انتشار فاکس‌فیوری (مایکت و بازار)

## محتویات
- `web/` نسخه وب (PWA). روی هر هاست استاتیک آپلود کن (مثلاً GitHub Pages، لیارا، آروان). بدون CDN و آفلاین کار می‌کند.
- `android-capacitor/` پروژه ساخت APK.
- `store/` آیکون 512، بنر 1024x500، اسکرین‌شات‌ها (1080x1920).
- `docs/store-listing-fa.md` متن‌های آماده فروشگاه.

## ساخت APK (روی کامپیوتر خودت)
پیش‌نیاز: Node.js 18+، Android Studio (JDK 17).
```
cd android-capacitor
npm install
npx cap add android
npx @capacitor/assets generate --android      # آیکون و اسپلش از پوشه assets
npx cap sync android
npx cap open android
```
در Android Studio: Build > Generate Signed Bundle/APK > APK. اگر کلید نداری گزینه Create new keystore را بزن.
**فایل keystore و رمزش را حتماً چند جا نگه دار؛ بدون آن نمی‌توانی آپدیت بدهی.**
- در `android/app/build.gradle` مقدار `versionCode 1` و `versionName "1.0.0"`؛ با هر آپدیت versionCode را زیاد کن.
- جهت صفحه: در `android/app/src/main/AndroidManifest.xml` داخل تگ activity بنویس `android:screenOrientation="portrait"`.
- `appId` در `capacitor.config.json` (الان `ir.foxfury.game`) را به شناسه یکتای خودت تغییر بده، قبل از `cap add android`. بعد از انتشار دیگر عوض نمی‌شود.

## نکته صادقانه
من در محیط خودم نتوانستم APK بسازم و پروژه اندروید را تست نکرده‌ام. کد بازی را در مرورگر با WebGL تست کردم. اگر موقع بیلد خطایی دیدی متنش را بفرست.

## ثبت در مایکت و بازار
1. مایکت: developer.myket.ir، بازار: developers.cafebazaar.ir؛ حساب توسعه‌دهنده بساز.
2. APK، آیکون، بنر، اسکرین‌شات‌ها و متن‌های `store-listing-fa.md` را وارد کن.
3. آدرس سیاست حریم خصوصی: `web/privacy.html` را روی هاست بگذار و لینکش را بده.
4. دسته: بازی > اکشن/ران‌نر. رده سنی: ۳+ (بدون خشونت واقعی).

## تبلیغات (فاز ۲)
فعلاً بازی بدون تبلیغ است و زنده شدن دوباره با ۳۰ سکه انجام می‌شود. برای درآمد واقعی باید SDK تپسل یا یکتانت (بومی اندروید) را با یک پلاگین Capacitor وصل کنیم و تابع `window.FoxAds.showRewarded(cb)` را پیاده کنیم؛ بازی از قبل آماده این قلاب است. بعد از تأیید حساب تبلیغاتی‌ات می‌توانیم این را انجام بدهیم.
