---
title: "Bad WIFI performance, Realtek RTL8188EE"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by rolltide101x on 2014-12-03
My girlfriend's laptop which is an HP 2000-2d70DX WIFI is very annoying and has been that way for quite some time. I kept assuming that a Kernel update would sooner or later completely solve the issue but it has not. It will work fine for a few minutes and then it will "pause" for about 30 seconds and it really is quite annoying. What I was here to ask is if I can replace the WiFi antenna with one that would be more Linux friendly? I have tried multiple times to fix it and I have made it better but I can just not solve the issue completely. 

If it can be replaced can someone give me some good options that are 100% supported in the kernel? If it can not be replaced maybe someone has some ideas on things to try? I have read multiple threads on the issue and tried multiple things to fix it but to no avail. Thank you for your time :)

I have never had a reason to look into replacing a WiFI antenna so I am pretty ignorant on how it works so that is why I am asking.

Specs if they are useful. Laptop has Ubuntu 14.10
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c04100514&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c04100514&cc=us&dlc=en&lc=en)

I would buy say this if it would solve our issue.
[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-half-height-mini-pcie-card](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-half-height-mini-pcie-card)

---

### Post by chili555 on 2014-12-04
Before you get out the credit card and the screwdriver, I suggest you first check here: [http://joshuawise.com/wireless-whitelist](http://joshuawise.com/wireless-whitelist)> “104 - Unsupported wireless device. System halted.”

The system powered up, and found that a wireless card existed. However, it determined that it was not a wireless card that was “approved” by the system, and hence refused to allow access to any part of the system until the “unapproved” device was removed. Also, the card you propose to swap is an Atheros card using the driver ath9k. I suggest you search this forum for 'ath9k' and see if your fellow Ubuntites are having a smooth, trouble-free experience. 

Next, I suggest you try a driver parameter. Please open a terminal and do:```
sudo -i
echo "options rtl8188ee fwlps=0"  >  /etc/modprobe.d/rtl8188ee.conf
modprobe -r rtl8188ee
modprobe rtl8188ee
exit
```It may take a reboot. Any improvement?

---

### Post by rolltide101x on 2015-01-10
I finally gave up and just bought a USB wifi adapter. This one works really well and is cheap

[http://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

These drivers help it perform even better!

[https://github.com/vincent-t/rt8192cu_dkms](https://github.com/vincent-t/rt8192cu_dkms)

---

### Post by owenll on 2015-04-12
> **chili555 said:**
> 

Next, I suggest you try a driver parameter. Please open a terminal and do:```
sudo -i
echo "options rtl8188ee fwlps=0"  >  /etc/modprobe.d/rtl8188ee.conf
modprobe -r rtl8188ee
modprobe rtl8188ee
exit
```It may take a reboot. Any improvement?

Thanks for this advice. It seems to have worked for me. Is anybody able to explain what these commands do?

---

### Post by chili555 on 2015-04-12
Frankly, I just copied from another thread where is was reported as helping. The listing in modinfo says:```
$ modinfo rtl8188ee
<snip>
fwlps:Set to 1 to use FW control power save (default 1)
<snip>
```Essentially, we set the driver to *NOT* use firmware control power save. I suspect, but don't know for sure, that the instability stems from power save turning on and off repeatedly. A few Linux wireless drivers do not handle power save well.

---

### Post by owenll on 2015-04-12
Thanks. Whatever it does your advice has changed a pretty infuriating laptop into a working one

---

