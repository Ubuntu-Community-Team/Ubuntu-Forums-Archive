---
title: "Need help with IEEE802X Authentication"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Rever75 on 2007-11-21
Ok,
  I am putting together a proposal for my company to switch to Linux, in particular Ubuntu. I currently and for awhile have been running Ubuntu (ATM Gutsy) on my laptop. Here at my company we use a Ciscos Wireless Controller with 11 AP setup across the Network. The Authentication goes through IAS on a Windows Server and is setup via AD. We are using EAP-PEAP with MSCHAPv2. I have been able to successfully connect to this AP only by inputting the info into /etc/network/interfaces. I do see a security issue here as my Username and Password is in plain text in the file. Also by adding this to the file I am unable to roam to different Wireless networks (ie My Home or Other Plant Wireless Networks) without commenting out those lines. Any help in getting this connection setup to function with Network-Manager-Gnome so I can choose btw Wired and different wireless networks would be great. Without this i feel I will not stand a chance on convincing the company to switch.

---

### Post by wieman01 on 2007-11-21
Nonsense... Had to remove my post. Sorry, confused it with LEAP.

---

### Post by wieman01 on 2007-11-21
WICD could be an option for you:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by Rever75 on 2007-11-21
I installed WICD but no option for MSCHAPv2. I did sea PEAP with GTC but none PEAP with MSCHAPv2

---

### Post by wieman01 on 2007-11-21
> **Rever75 said:**
> I installed WICD but no option for MSCHAPv2. I did sea PEAP with GTC but none PEAP with MSCHAPv2
Perhaps the latest, latest CVS version of Network Manager? You will have to compile it from source in that case...

---

