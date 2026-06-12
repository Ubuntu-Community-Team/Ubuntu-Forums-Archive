---
title: "Hostname not displayed in DHCP clients table"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by Kamy on 2006-11-18
Hi,

I'm still fairly new to Linux.  I set up a settop box using Knoppmyth last year, which I have running fairly well, but Ubuntu 6.10 is my first full on distro on a "working" machine:D .

On my home network I have 3 WinXP pc's, 2 are wireless, one is wired to the router, and now 2 Linux pc's, my settop box running KnoppMyth, and my laptop running Ubuntu 6.10, both are wireless connections.

My question is, in the dhcp clients table of my router, all the wireless connections show the hostname of the computer they are on, except for my laptop running Ubuntu 6.10.  The table looks like this,

mythtv       192.168.1.102
*            192.168.1.104
kayla-athlon 192.168.1.109
karl-athlon  192.168.1.123

The * represents the laptop Ubuntu  6.10 is installed on.  How can I get it to display the hostname in my routers dhcp clients table?  Host name is karl-laptop.  The hostname is correct in /etc/hostname.

Thanks in advance,

Kamy

---

### Post by ash211 on 2006-11-20
In /etc/dhcp3/dhclient.conf uncomment the line beginning with "send host-name" and add your desired name after.

---

### Post by Kamy on 2006-11-21
Thanks ash211, that did the trick :)

---

