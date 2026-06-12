---
title: "Realtek RTL8188EE  Wifi Network Adaptor - Slow wifi"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by onetruesingh on 2013-12-30
Hi guys,

I just bought a new laptop, HP Pavilion 15-n096ea, which came with Windows 8 installed. As expected, I installed Ubuntu 13.10 over it. 

However, I am having major trouble with the wifi, it's so slow! With my old laptop I could reach the full 30mb coming from my router, but with this one I get around 2mb only!
Even when connected via ethernet the connection does not reach the full 30mb, it only reaches around 10mb.

My old laptop used an Atheros AR928X wireless adapter whereas this one uses the Realtek RTL8188EE. 

Now I've traversed the ubuntu forums for solutions similiar to my problem but nothing is working. It seems there is no suitable driver available that works properly.

Please help.

Best wishes,

Arron

(p.s first ever post on the ubuntu forums, woo!)

---

### Post by varunendra on 2014-01-02
Welcome to the forums Arron !

Have you tried this? - [http://askubuntu.com/a/337855](http://askubuntu.com/a/337855)

I suggest using the same procedure, but with a relatively newer package - [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2) instead of the one proposed in the above link.

If that doesn't solve your problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by onetruesingh on 2014-01-05
Thank you kindly Varun! My speed is now around 10-15mb which is much better than 2mb. May not be the full 30mb but I can live with it now. 

Arron.

---

### Post by varunendra on 2014-01-05
You're welcome !

If you wish, we can still use the wireless_script report to see if something can be done to further improve the speed, without breaking its current functionality. :)

---

