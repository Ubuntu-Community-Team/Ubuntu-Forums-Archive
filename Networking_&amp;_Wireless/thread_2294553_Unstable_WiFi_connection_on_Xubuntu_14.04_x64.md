---
title: "Unstable WiFi connection on Xubuntu 14.04 x64"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by mateusz12 on 2015-09-11
Hi guys,
I have problem with my wifi connection on my Xubuntu 14.04 x64. When I run my computer wifi is stable about 30sec, after this time, connection disables and enables again everytime. My laptop model is Samsung r522 (network card rtl8192se inside). 

I've tried this:
[B]echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
[/B]
and this:
[B]sudo -i
echo "options rtl8192se fwlps=0"  >  /etc/modprobe.d/rtl8192se.conf
modprobe -r rtl8192se
modprobe rtl8192se[/B]
**exit**

Nothing fix my problem :(

Please help me

PS: Everything is good on x32 version of Ubuntu

---

### Post by praseodym on 2015-09-11
Why not staying on 32bit?! How much RAM do you have? If it is below 4 GB then 32bit is suitable

---

### Post by mateusz12 on 2015-09-11
I have 4GB. I think that 64bit is faster and more future.

---

### Post by praseodym on 2015-09-11
So, then run the wireless-script from the sticky thread and show the outputs:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

