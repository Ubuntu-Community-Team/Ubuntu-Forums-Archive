---
title: "I need Wi-fi help"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by armymedic42 on 2007-06-17
I am running Ubuntu 7.04, GNOME.

I'm trying to find a program that operates similar to Windows' Wireless network tool (whatever the hell its called)  to locate, and connect to networks, including PPTP VPN networks.  

I've tried every wifi management program in Add/Remove, and although some of them actually detect the network for me, they don't seem to want to connect.  And as for VPNs, I have Kvpnc and just CAN'T get it to pick up the network I need at school.

I'm new to the whole Linux scene, so I don't know how to figure any of this stuff out.  PLEASE HELP!

---

### Post by Alex&amp;Linux on 2007-06-17
Heyo armymedic42, whats up?

Im also fairly new to this, I did setup a wireless network with 6.10 for my mother, I believe that using the standard network manager, I had to specify SSID to connect to the network. As far as a utility that can automatically detect SSIDs in range not exactly sure. However, as root, you can run:

 "iwlist [name of wireless interface] scanning"

The output should show SSIDs in range, as well as a host of other informations.
There are a lot of applications that are available through terminal that dont have a GUI (writing dvds ect.) and they are extremely useful if you dont mind using terminal.

For more information regarding that command, you can run "man iwlist" or use the following link:

[http://www.linuxcommand.org/man_pages/iwlist8.html](http://www.linuxcommand.org/man_pages/iwlist8.html)

There will ultimately be a better answer, or an application that provides a GUI for this output.
For me though, I figure that if I can do it faster with terminal, why complicate things with another layer?

---

