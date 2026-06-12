---
title: "Packet injection problems; Ubuntu freezing?"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by logan_101 on 2008-10-25
Hey everyone, I'm trying to crack the WEP code to my AP, but i've run into a slight problem. First I'll just list my hardware in case that helps: Intel T5200 Core 2 Duo CPU, Ubuntu 8.04 x86-64, Intel 3945ABG wireless.

I'm using aircrack-ng and the ipwraw driver to do this. (I am following this: [http://www.maxi-pedia.com/crack+WEP]("http://www.maxi-pedia.com/crack+WEP") tutorial) I can find the AP, collect packets, authenticate, and even crack the WEP once I've collected enough packets (takes HOURS), but whenever I try to inject packets Ubuntu freezes and I'm forced to hold down the power button to restart. Aireplay-ng will connect to the access point and start waiting for ARP packets, but as soon as it finds one the computer freezes and the caps lock light starts flashing.

Any ideas?

---

### Post by sloggerkhan on 2009-01-30
My main thought would be drivers... I know intel has open drivers, but I think not all drivers support every feature, especially advanced ones, or maybe they've got a bug or something. For example I've got a wireless network adapter that can't do promiscuous mode, but otherwise works perfectly with linux. So that's my shot in the dark. Might be able to find something in one of your system logs.

---

### Post by scrypt on 2009-03-26
you are probably trying to remove the driver that is in use.

Try to remove the driver when you have turned off yor wireless adaper

---

