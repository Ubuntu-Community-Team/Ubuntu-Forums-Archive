---
title: "Wifi connection over 10 times slower on Ubuntu vs Mac OSX"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by chrisboven on 2014-02-12
Hello everyone,

I recently upgraded my internet service and am able to achieve around 60 Mbps download speed when using my Macbook Air.  However, on my Ubuntu 13.10 installation the download speed is a mere 5 Mbps.  My Ubuntu machine has a new TP-Link 300 Mbps Wireless N PCI Express card, model no. TL-WN881ND, which is apparently supported by Ubuntu.  

I tried a few basic solutions like disabling IPv6 and wireless n, but still haven't been successful.  

Any suggestions?

Thank you

---

### Post by varunendra on 2014-02-13
Welcome to the forums chrisboven !

Please try this as a quick shot -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
This will be a temporary change that will be lost at next boot, so try connecting without rebooting and see if it helps. If it does, we can make it permanent.

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by tgalati4 on 2014-02-13
Describe how you were downloading the files.  If you were using an on-the-fly mount in Nautilus then it is typically slower than a permanent mount in /etc/fstab.

---

