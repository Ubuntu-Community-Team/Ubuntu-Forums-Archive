---
title: "TP-LINK T9E no 2.4GHZ network detected"
date: 2017-01-10
forum: Networking &amp; Wireless
---

### Post by tholden on 2017-01-10
[SIZE=2][FONT=arial]I have this showing up in lspci

```
06:00.0 Network controller [0280]: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
        Subsystem: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:0619]

```
I have installed the broadcom wl driver using the driver utility.

Problem is, I can only see 5GHZ network, and it has a bad signal strength. The good working 2.4GHZ is not showing up. What can be the problem?
Card is a TP-LINK.

In Windows, both network shows up, so its not a signal issue.

Anyone know what could be causing this? Am I using the wrong driver?

I have tried scanning for it using iwlist, no results. I have also changed the regulatory domain to 00 to be sure that channels are not an issue.[/FONT][/SIZE]

---

### Post by slickymaster on 2017-01-10
*Thread moved to **Networking & Wireless**.*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by tholden on 2017-01-10
I have ran the script. Results are attached.

---

### Post by jeremy31 on 2017-01-10
Please move the wifi access point to channel 6 if you can.  Broadcom kernel modules dont allow 2.4 Ghz channels higher than 11

---

### Post by tholden on 2017-01-10
Thank you, now it works fine.

---

