---
title: "how to enable another ethernet card (eth1)"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-05-23
hi all,

currently I were using Ubuntu 7.0.4 64 bit server which is install to SunFire x2100 Server. From our server that have two Ethernet card. but unfortunately while I type at command line with [COLOR="Red"]**$sudo ifconfig**[/COLOR], it only appear 1 ethernet card [COLOR="Red"]**eth0**[/COLOR].

so do anybody can tell me how do i enable another ethernet card ?

Please Advice .. thanks..

---

### Post by rogier.de.groot on 2007-05-23
Try entering:
sudo ifconfig eth1 192.168.0.1 netmask 255.255.255.0 up
(adjust ip address / netmask values for your situation)
after that the command "ifconfig" should show two interfaces. If you get an error about eth1 not existing check (and post) the output of the "dmesg" command. Edit the file /etc/network/interfaces to make a permanent assignment to eth1 (just copy & adjust the eth0 lines - that's what I did). Don't know if that works with NetworkManager though (but you've got the GUI network tool thing for that).

---

