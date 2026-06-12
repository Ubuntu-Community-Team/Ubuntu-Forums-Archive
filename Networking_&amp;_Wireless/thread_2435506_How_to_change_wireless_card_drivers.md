---
title: "How to change wireless card drivers?"
date: 2020-01-21
forum: Networking &amp; Wireless
---

### Post by CorporateMonkey on 2020-01-21
So I wanted to test some other drivers to see if they are going to work with my wireless card. So, let say I wanna test this driver ["]https://wireless.wiki.kernel.org/en/users/drivers/ath9k_htc]("https://wireless.wiki.kernel.org/en/users/drivers/ath9k_htc) How do I make backup of driver I currently have and how do I install the new one?

---

### Post by oldrocker99 on 2020-01-23
If there is a Windows driver, you can extract the .exe to get the .info file. Then,
```
sudo apt install ndiswrapper
```
It will most likely be in Syetem Tools. Open it up, and tell it where the .info file is located, and that's all that's there is to it. You **may** need to reboot.

---

### Post by wildmanne39 on 2020-01-23
I am on my cell phone so just a short reply ndiswrapper has not worked in a long time and even when it did it was always the last resort. You may be able to use a different version of your devices driver or set a parameter to help it work better but using one not for your device will not work. Please post the device you are using so some one may be able to help you .

---

### Post by wildmanne39 on 2020-01-23
Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created, if you need help with the driver you have installed, please tell us what issues you are having, as I said in my previous post a driver parameter may be able to be set to help it perform better or a different version of the driver, ndiswrapper was never a good option even when it did use to work in some cases, it only worked with a 32bit windows driver and has not worked with any new releases for a few years.

---

### Post by slickymaster on 2020-01-24
*Thread moved to **Networking & Wireless**.*

---

