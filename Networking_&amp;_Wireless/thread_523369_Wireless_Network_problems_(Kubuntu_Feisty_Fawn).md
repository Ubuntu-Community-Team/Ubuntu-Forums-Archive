---
title: "Wireless Network problems (Kubuntu Feisty Fawn)"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Tomkin on 2007-08-11
I am new to Linux and I just recently installed Kubuntu Feisty Fawn. I got the wired network set up but I can't figure out how to set up a wireless network. I tried using KNetworkManager, but nothing happened when I clicked on it. I also tried going to System Settings > Network Settings but I couldn't find my way around. Any help would be welcomed. Thanks!

 - Tomkin

I have a bcm43-something wireless card using ndiswrapper and Windows drivers.

---

### Post by moore.bryan on 2007-08-11
*may i suggest trying [wicd]("http://wicd.sourceforge.net/") instead of knetworkmanager?*

---

### Post by kevdog on 2007-08-12
Lets just check your installation of the drivers on your card

Can you type at the command line and cut and paste the output of 
lspci -nn
lshw -C network

Thanks

---

