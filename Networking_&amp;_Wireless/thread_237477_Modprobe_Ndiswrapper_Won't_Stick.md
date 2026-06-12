---
title: "Modprobe Ndiswrapper Won't Stick"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by skattman83 on 2006-08-16
I can do a "sudo modprobe ndiswrapper" and then use my Linksys WUSB54GV2 (PrismGT chipset) to get on my network just fine.  However, when I reboot, I need to do the modprobe again, otherwise, running the wpa_supplicant command returns a bunch of errors and then fails.  Also a iwconfig after a reboot does not show wlan0, but after modprobing, it does show wlan0.  Any ideas on what's going on here?

---

### Post by skattman83 on 2006-08-16
I think I found my answer here:
[http://www.ubuntuforums.org/showthread.php?t=177836](http://www.ubuntuforums.org/showthread.php?t=177836)

---

