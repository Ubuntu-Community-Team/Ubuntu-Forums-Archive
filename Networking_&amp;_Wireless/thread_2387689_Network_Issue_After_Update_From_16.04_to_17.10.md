---
title: "Network Issue After Update From 16.04 to 17.10"
date: 2018-03-22
forum: Networking &amp; Wireless
---

### Post by mpmckinnon on 2018-03-22
Hi there I upgrade my copy of Kubuntu 16.04 to 17.10 and when I rebooted my network card does not show up in the network tray. When I got to configure network connections they do show up but have no network connection. I did do some looking on the internet on another computer and tried sudo dpkg-reconfigure resolvconf but get this error message  /usr/sbin/dpkg-reconfigure: resolvconf is broken or not fully installed. Does anyone have any thoughts on how I can fix this issue short of reinstall (really don't want to). Thank you all for your help on this.

---

### Post by TheFu on 2018-03-22
Networking changed drastically with 17.10.   They use netplan these days.  Resolve has been added to systemd-resolv too, I believe.

So, the first thing to do is try to figure out what the problem is actually.  In order:
* ping the router, by IP address.  Does this work?
* ping 8.8.8.8   . Does this work?
* ping google.com   Does this work?
If you can't ping the router, don't continue.

Post the command and output from these commands:
* ifconfig
* route -n
* lshw -C network

Those will tell us about the card, drivers, and routing.

Please use "code tags"  - Adv Reply (#) so the output lines up. Too hard to read otherwise.

---

