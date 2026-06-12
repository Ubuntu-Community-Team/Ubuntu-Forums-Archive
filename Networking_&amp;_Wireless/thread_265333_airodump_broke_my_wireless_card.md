---
title: "airodump broke my wireless card"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by mysmallsecret on 2006-09-25
i am running Ubuntu and
i have a d-link WNA-2330 wireless card with ndiswrapper
which used to work great until i used airodump with it

my wireless card still gets a signal but
now if i run dhclient
sudo dhclient ath0
i get this message

Listening on LPF/ath0/00:15:e9:72:c8:8c
Sending on   LPF/ath0/00:15:e9:72:c8:8c
Can't bind to dhcp address: Address already in use
Please make sure there is no other dhcp server
running and that there's no entry for dhcp or
bootp in /etc/inetd.conf.   Also make sure you
are not running HP JetAdmin software, which
includes a bootp server.

which didn't happen before i used airodump

if i try to scan with
iwlist ath0 scan
before i run dhclient
i get a segmentation fault message
and my computer kindly freezes
but after dhclient is run and fails to work, "iwlist ath0 scan" works fine

anyway i haven't been able to connect to networks that i know the nameserver address for the resolv.conf file either since i tried using airodump. i was thinking airodump changed something causing my other wireless tools to act funny. seeings how it must be run as root. 
uninstalling aircrack
reinstalling wireless-tools dhclient ...
didn't work
from "iwconfig ath0" tells me that i am in Managed mode at boot

any ideas?
<3

---

### Post by mysmallsecret on 2006-09-26
in case anyone else has this or similar problem
i think i have figured it out 
and i think this is how i did it

disable all network devices
using sudo ifconfig <device> down

add the line
auto ath0
to the file /etc/network/interfaces

and reboot the computer

---

