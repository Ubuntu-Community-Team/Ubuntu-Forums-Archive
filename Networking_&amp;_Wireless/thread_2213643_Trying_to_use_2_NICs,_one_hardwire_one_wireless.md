---
title: "Trying to use 2 NICs, one hardwire one wireless"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2014-03-27
I have hardwired/wireless network 10.0.0.0/24 that connects to the Internet
I have a Wireless network on 192.168.1.0/24 that consist of 2 systems, an old XP system that has been taken offline and the other is running xubuntu 12.10 for about another week or two when 14.04 is ready or at least a release candidate
the xubuntu box is sharing the printer/scanner so the goal is to have it on both networks
when both networks are connected i can ping the XP box but the XP box cant ping back, sometimes it can but it is very lossy/slow, but it i disconnect from the hardwire it acts right

I tried creating a virtual NIC eth0:1 but it keeps disappearing and will not appear even if i put it in /etc/network/interfaces  so i figure i will just use the wireless for it, at least that does not vanish

---

### Post by SeijiSensei on 2014-03-28
Are you trying to connect to the same subnet using both the wired and wireless adapters?  That usually causes routing problems since the choice of the default gateway is randomized.  Just use one connection or the other.  Unless you use "bonding" to connect to the two interfaces together, you're really not gaining anything in terms of performance by using both adapters.

---

### Post by pqwoerituytrueiwoq on 2014-03-28
just trying to isolate the 2 networks and have 1 system on both

DIR-615 ver I1 running DD-WRT w/ second 2 wireless networks [screenshot](http://www.zimagez.com/zimage/screenshot-03282014-025448pm.php)
&#9500;&#9472;&#9472; Wireless Laptop in 10.0.0.0/24 network (Xubuntu 12.10)
&#9500;&#9472;&#9472; Wireless Desktop on 192.168.1.0/24 network (Windows XP)
&#9492;&#9472;&#9472; Wired Desktop on 10.0.0.0/24 network with wireless card on 192.168.0/24 network (Xubuntu 12.10 or 13.10 i forget)
Only the 10.0.0.0/24 network has Internet access

---

### Post by SeijiSensei on 2014-03-29
> Wired Desktop on 10.0.0.0/24 network with wireless card on 192.168.0/24 network (Xubuntu 12.10 or 13.10 i forget)

What's the default gateway on this machine?  Can you show us the output from "route -n"?

If you want the machine to have Internet access, its default gateway should be in the 10 network.  Then it would use the wireless connection to communicate with hosts in the 192.168 network and send any other traffic to the default gateway in 10.

---

