---
title: "ndiswrapper/WUSB54Gv1 help and advice needed"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by ubergam3r on 2007-04-16
hi ok ive got a linksys wusb54gv1 and downloaded ndiswrapper latest version.

so far ive downloaded the drivers for it from the ndiswrapper wiki page,loaded them and  when i list the the drivers it says "Installed ndis drivers:wlanuig driver present", ive plugged in my linksys adapter then run the "modprobe ndiswrapper" code.

according to the install doc it should create a wlan0, but it isnt present.

Any advice on what my next step or fix is?

---

### Post by Floppyjoe on 2007-04-16
What is the output of:
```
ndiswrapper -l
```
when the device is plugged in?
What version of Ubuntu are you using?

---

