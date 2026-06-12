---
title: "nm-applet (network manager) problem"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by zajjar on 2007-10-19
I use Ubuntu 7.10.
I want to connect to wirless network (WPA2, pass, hiden SSID) and I use for it "nm-applet (network manager) -> Connect to other wirless network" option.
I set SSID, pass, and encryption. Next I click on connect button.
Everything is OK, WiFi works fine, but when I restart my computer I see then network manager don't remember this network and don't connect to this network.
What I must do to save this settings? Is this possible to do in "nm-applet (network manager)"?

-- 
regards,
zajjar

---

### Post by rawlinc on 2007-10-22
The exact same thing happens with my wireless network (WPA Personal, TKIP, hidden SSID).  Is this a bug?  Does the network manager usually forget wireless settings between reboots?

---

### Post by LDRoamer on 2007-10-23
Try turning on your SSID and see if that fixes the problem.  A few years ago I had a Win98 machine on my network and it wouldn't work unless the SSID was turned on. I have read that a hidden SSID isn't much of a security feature anyway.

---

### Post by NilsE on 2007-10-23
Make sure gnome-keyring-manager is installed and working.  This is where passwords etc are saved for network-manager.

One way to check is to see if you have System/Administration/Keyring Manager and if your passwords are in there.

---

### Post by zajjar on 2007-10-23
Thanks for your answers but I have not fixed it till now.
I think that this is a bug in Ubuntu 7.10 and I reported it in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155304](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155304)

-- 
regards,
zajjar

---

