# AZ DIGITAL PROJECT

### Group Members + Contribution: (we did it all together)

- Pooya Fallah 50%
- Ali Alhosein Akhzar 50%

---

## Report:

کدهای ارائه شده شامل فایل‌های ربات ۱ و ۲ و فایل utils برای کنترل ربات‌های دو تیم زرد و آبی می‌باشند. برای استفاده از این کدها باید در پوشه‌های مربوط هر تیم در تکلیف ارائه شده کپی شوند. علاوه بر فایل های کد یک فیلم کوتاه‌ هم از نحوه عملکرد کدها تهیه شده‌است.<br/>
استراتژی استفاده شده در این کدها به این صورت است که ربات مهاجم همیشه به دنبال کردن و ضربه زدن به توپ می‌پردازد که نحوه عملکرد آن تقریبا مشابه با تمرین قرار گیری در پشت توپ بخش‌تمرین‌ها می‌باشد و ربات مدافع در زمان‌هایی که توپ از آن فاصله دارد به سمت دروازه می‌رود و در نقطه‌ای ثابت نزدیک به دروازه خودی می‌ایستد و زمانی که توپ نزدیک می‌شود مانند مهاجم عملکرده و اقدام به ضربه زدن به توپ می‌کند. ربات مدافع این محدودیت را نیز دارد که نمی‌تواند فاصله زیادی از دروازه خودی بگیرد. این استراتژی به صورت مشابه برای هر دو تیم به کار رفته است. نکته‌ای که لازم به ذکر است عملکرد عجیب کلی تکلیف می‌باشد به طوری که دستورات ربات‌ها تا زمانی که در یک رنج مشخصی از توپ قرار بگیرند عمل نمی‌کنند خواهشا این نکته را در زمان بررسی کدها و فیلم در نظر داشته باشید.<br />

#### Controllers:

ربات مدافع برای قرارگیری در نقطه نزدیکه به دروزاه خودی از تکنیکی شبیه با تمرین حرکت در دو جهت و چرخش ۹۰ درجه استفاده می‌کند که برای کنترل چرخش خود از یک کنترلر PID با مقادیر ضریب‌های 1, 1, 30 (30 برای P) استفاده می‌کند. این کنترلر تنها کنترلر استفاده شده در مجموع ربات‌های یک تیم است. باقی اعمال تنها با دادن یک سرعت ثابت به موتورها و توقف عمل در زمان رسیدن به یک اندازه خطای مطلوب انجام می‌شود.

#### PID Controller class:

کلاس کنترلر در فایل utils هر کدام از تیم‌ها می‌باشد. این کنترلر با دریافت اختلاف مقدار مطلوب و خروجی، خروجی براساس فرمول زیر می‌دهد:<br/>
$$output = K_Pe_k + K_I\sum^k_{i=0}e_i(t_i - t_{i-1})+K_D{e_k - e_{k-1} \over {t_k - t_{k-1}}} $$
| Variable | Description | Initial Value (k=-1) |
| :---: | :----: | :---: |
| $K_P$ | proportional controlller coeficiont |user's choice |
| $K_I$ | integral controlller coeficiont |user's choice |
| $K_D$ | derivative controlller coeficiont |user's choice |
| $e_k$ |controller input | 0
| $t_k$| time in seconds get using time.time at the moment<br/>when $e_k$ is received | time.time when an instance of class is created
