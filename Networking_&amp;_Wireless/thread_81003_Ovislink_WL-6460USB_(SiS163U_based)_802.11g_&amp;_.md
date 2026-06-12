---
title: "Ovislink WL-6460USB (SiS163U based) 802.11g &amp; ndiswrapper"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by fatgit on 2005-10-23
I've installed ndiswrapper without any problems, and ndiswrapper -l reports :
sis163u driver present, hardware present.

However, modprobe ndiswrapper does not get the light to turn on.
iwlist wlan0 scan reports : Interface doesn't support scanning
iwconfig iwlan essid <essid name> reports : Error for wireless request "Set ESSID (8B1A) :
SET failed on device wlan0 ; No such device


As a newbie to ubuntu, and a beginner in linux, Im not sure what to do next, other than buy a more linux-compatible card ;)

*edit* should say /var/log/dmesg has nothing at all showing after I do modprobe ndiswrapper - no errors or anything

---

### Post by fatgit on 2005-10-23
when plugging the adapter in, syslog reports :
usb 4-3: new high speed USB device using ehci_hcd and address 14

---

### Post by fatgit on 2005-10-23
I reinstalled ubuntu from scratch (it was a new install anyway), installed gcc, kernel headers etc, and compiled the ndiswrapper utils and ndiswrapper 1.5rc1

I then installed the driver using ndiswrapper -i sis163u.inf, and got a wierd set of errors to do with perl, so I hit ctrl+D to get out of it.
Out of curiosity I tried ndiswrapper -l - this gave me errors again, and holding ctrl&d seemed to scroll through the entire function line by line (somehow I must have got into a debug mode ??)  & got the message that the driver was loaded, and the hardware present.
I followed the rest of the ndiswrapper instructions, and lo and behold, the damned thing worked :o

No idea why it worked this time, or what I did, but I finally have wireless lan on the laptop - something I've failed to do in a loooong time :o

---

