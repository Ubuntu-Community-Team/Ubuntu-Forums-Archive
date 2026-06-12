---
title: "Slow Internet - was the same with Debian"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by guliver on 2006-10-22
Just switched back from Debian to Ubuntu. With Debian I had exactly the same problem.

***Symptom:***

When I open **any** wab page it need 5-7 seconds to open page, all that time it "looking for page" and than for less than a second it open the page. Same with Firefox, Opera..

Same when I send or receive emails with Evolution.

This computer with Windows on separate partition working perfect, it mean that hardware and internet are ok.

I have ASUS motherboard P4P800SE with 512mb DDR, P42.66Ghz and Maxtor 80gb disk.
Network adapter is integrated in motherboard and it is:

> -Marvell 88E8001 Gigabit Lan Controller supporting 10/100/1000 BASE-T Ethernet

This computer is than connected to D-Link DI604 router which is connected directly to the cable modem.

===================================================================

Can anybody tell me what should I check in order to fix this problem?

:-k

---

### Post by adwait on 2006-10-23
Turn IPv6 off. In firefox, type
```
about:config
```
in the address bar. Search for ipv6disable and set it to true.

---

### Post by guliver on 2006-10-23
Hi,

I did that yesterday but it did not help...

:neutral:

---

### Post by adwait on 2006-10-24
How about turning off ipv6 entirely through modprobe.....don't remember how exactly though, search the forums. You ought to find it

---

### Post by squibT on 2006-10-24
Turn IPv6 off. In firefox, type
Code:

about:config

in the address bar. Search for ipv6disable and set it to true.

Edit the file /etc/modprobe.d/aliases

locate the line:

alias net-pf-10 ipv6

with:

alias net-pf-10 off

then reboot.

---

### Post by timhaughton on 2006-10-24
I have almost the exact same problem with Dapper on my laptop. It seems to be a DNS issue when I'm behind certain types of router. When  I'm at home, DNS works very quickly and all is well. When I'm on site, name resolution can take over 5 seconds.

I dont know what causes it, as the Windows machines I use on site all resolve names really quickly.

Regards,

Tim

---

### Post by handy on 2006-10-24
Are you using DHCP?

I had this problem when I first started using Breezy & I erroneously set it up as static IP.

Every new server I went to was slow to load, then pages on the same server where fast as usual!

---

### Post by migster85 on 2006-12-21
I'm also having a problem with slow DNS resolution, and I've tried everything metioned here and in other posts:
1) turning on/off ipv6
2) dynamic and static ip
3) providing external DNS server IP manually
4) plugging in directly to modem, without the router
5) playing with the router's DNS settings

I also tried all combinations of 1-5 with no luck. Other computers on my network are working fine (other Ubuntu machines) but one is having a 5-second DNS lag whenever I try to resolve the name to an ip for the first time - after that everything is fine. I think that it's something wrong with Ubuntu's setup - some configuration file or some package had gone crazy, or some library. Don't know what to do at this stage.

Does anyone know what might case a DNS hangup internally? Maybe Ubuntu is looking for DNS somewhere on the system, and then considers asking the router/other source? Maybe it thinks that localhost is the primary DNS server somehow? The reason why I'm asking is because when I ping to some site, I see no traffic until after 5 seconds, so the machine is not even asking the router for anything, and then 5 seconds later it goes "oh, yeah, do you know what the ip is" and sure enough the router/DNS server provides the IP.

---

