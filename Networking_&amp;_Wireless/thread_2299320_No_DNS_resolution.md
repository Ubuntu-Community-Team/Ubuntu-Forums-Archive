---
title: "No DNS resolution"
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by marc60 on 2015-10-17
[COLOR=#111111][FONT=Ubuntu]nstalled Ubuntu 14 desktop a few months ago, in a mixed (different machines) windows/linux environment. Everything was working fine till yesterday: accessing shared folders/files on windows/linux from one computer to another over the network, browsing, printers, etc.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then I installed frostwire and deluge. After that, no DNS resolution. I can access the windows pcs shares from ubuntu, i can access ubuntu shares from linux, I can print on network printer. I can ping any IP address (8.8.8.8). But if I try to browse or ping using [www.yahoo.com](www.yahoo.com) or [www.google.com](www.google.com), DNS resolution failed.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have tried:[/FONT][/COLOR]

[LIST=1]
[*]rebuild the link for resolv.conf sudo dpkg-reconfigure resolvconf.
[*]Commented out the dns=dnsmasq line in /etc/NetworkManager/NetworkManager.conf.
[*]Added 8.8.8.8 and 8.8.4.4 in the resolver.
[*]Verified nmcli dev list iface eth0 | grep IP4.DNS:
IP4.DNS[1]: 192.168.1.1
IP4.DNS[2]: 8.8.8.8
IP4.DNS[3]: 8.8.4.4
[*]In /etc/network/interfaces:
auto lo
iface lo inet loopback
[*]added in interfaces
auto eth0
iface eth0 inet dhcp
[*]nslookup google.com and nslookup google.com 8.8.8.8 all fail with a "connection timed out; no servers could be reached" message. Reminder: I can successfully ping 8.8.8.8, and browse my network, and can browse from other computers in the same network.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]
I removed frostwire and deluge and rechecked everything, redone every step. And rebooted every time to no avail. Other suggestions?

Thank you for any help

Marc[/FONT][/COLOR]

---

### Post by marc60 on 2015-10-17
Still not solved. but...
running sudo nmap 192....(local ip) -p53 and sudo nmap 192....(local ip) -p53 -sU shows the port closed for tcp and udp. Yet I have no firewall running (sudo ufw status verbose gives inactive)

Any ideas?

---

### Post by oldos2er on 2015-10-17
Moved to Networking & Wireless.

---

