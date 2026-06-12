---
title: "Bad ESSID to disable connection?"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by blueturtl on 2006-12-16
This might not actually be an Ubuntu problem, but recently while visiting my inlaws I ran into an odd bug: my wife's laptop would not connect to their unprotected WLAN. Since I know the system is working (we have wireless at home too, though with WEP) I am beginning to suspect that it is indeed a problem with the router. The router has an ESSID with umlauts or an 'ä' in it. When viewing output from iwconfig everything shows up properly, except the ESSID of the wlan which displays a '?' where 'ä' should be. Can this one character be the reason we are not getting a connection or is it something else?

Somebody please assist because my father-inlaw is a Windows-man and he is just having way too much fun over "Linux that doesn't work". ](*,) 

p.s. I have tried to manually enter the proper ESSID into network-manager but the connection is never formed.

---

### Post by spd106 on 2006-12-16
AFAIK network-manager won't let you connect to a non-encrypted wireless network. I think that is more likely to be the problem. Try the network-admin utility or manually set it in the /etc/network/interfaces file.

---

### Post by emdeem on 2006-12-16
> **spd106 said:**
> AFAIK network-manager won't let you connect to a non-encrypted wireless network.

I can use network-manager to connect to non-encrypted wireless networks with no problem.

---

### Post by spd106 on 2006-12-17
[QUOTE=emdeem]I can use network-manager to connect to non-encrypted wireless networks with no problem.[/QUOTE]
I guess that was an earlier version, I'll have to keep up with developments a bit better. 


I still recommend trying the other two methods. There's no requirement for the essid to be in ascii.

---

### Post by blueturtl on 2006-12-17
> AFAIK network-manager won't let you connect to a non-encrypted wireless network. I think that is more likely to be the problem. Try the network-admin utility or manually set it in the /etc/network/interfaces file.

There's no requirement for the essid to be in ascii.

Thank you for your input. Next time around I will have to try manually setting the network parameters. I can't understand though why network-manager would not connect to an unprotected WLAN, I mean is this a bug? If it's bug shouldn't it have been squashed before the final release? You'd think they would have noticed a bug such as this one since so many people (unfortunately) run unprotected WLANs... :-k

---

### Post by blueturtl on 2006-12-28
Ok so apparently it is a bug:
[https://bugs.launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504](https://bugs.launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504)

This bug however only happens to affect this particular wireless chipset (Broadcom 43xx) running on ndiswrapper (that's my wife's system)! How inconvenient. I hope they fix this soon.

---

### Post by blueturtl on 2007-01-03
Found a temporary solution:

I type these commands into the terminal after booting to make the connection work:

sudo ifconfig eth1 up
sudo dhclient eth1

---

