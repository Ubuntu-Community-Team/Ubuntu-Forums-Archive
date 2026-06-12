---
title: "Wireless Constantly Freeze and Must be Restarted on Desktop"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by jeffreykutcher on 2013-12-14
Linux  3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


EDIMAX EW07811Un Wireless USB
wireless driver: rtl8192cu


Stays connected for a couple of minutes and then refuses to download anymore dat
a. Everything looks normal. No signs of error. Have to right mouse click the net
work icon and disable and enable networking. Repeat. There use to be no issues p
rior to 12.04.3.

---

### Post by varunendra on 2013-12-15
Please try this temporary parameter -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```
This would be a temporary change and would be lost at next boot. If it helps, can be made permanent.

If it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

