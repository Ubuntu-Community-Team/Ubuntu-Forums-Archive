---
title: "Works With Live, but Not HD Install"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by stevesh on 2005-10-23
I've done a hard drive installation of BB, and eveything works except Internet access. I've tried 2 different cards (Netgear FA310 w/Tulip, and a Network Everwhere NC-100U). Both show as installed in Device Manager (I think - I'm new to Linux), but when I run Network Tools, I get *Network Devices Not Found*.

The confusing thing is, if I run the BB Live CD in the same machine, everything works fine. Anyone have an idea? Thanks

Steve

---

### Post by cwaldbieser on 2005-10-23
[QUOTE=stevesh]I've done a hard drive installation of BB, and eveything works except Internet access. I've tried 2 different cards (Netgear FA310 w/Tulip, and a Network Everwhere NC-100U). Both show as installed in Device Manager (I think - I'm new to Linux), but when I run Network Tools, I get *Network Devices Not Found*.

The confusing thing is, if I run the BB Live CD in the same machine, everything works fine. Anyone have an idea? Thanks

Steve[/QUOTE]
If you open a terminal and type "ifconfig", do you see your network card there-- usually it is "eth0" and the IP address should be in the blurb next to it.  If it's not showing up, you might need to install a driver that was auto loaded on the Live CD but not during installation.

The commands to typically try are:
"lspci" - tells you what cards in PCI slots are recognized.
"lsmod" - tells you what modules are loaded.

You could try these commands on your normal install and the Live CD, and compare the results to see what is missing.

---

