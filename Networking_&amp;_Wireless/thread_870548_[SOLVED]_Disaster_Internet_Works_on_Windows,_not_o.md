---
title: "[SOLVED] Disaster: Internet: Works on Windows, not on Linux"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2008-07-25
This is seriously weird and I hope someone can help because the alternative does not bear thinking about:

My mix of four ubuntu hardy variant PCs and one Windows XP PC on a local network has been fine for months. The gateway IP is 192.168.1.1 

Overnight something strange happened. As of this morning:

[LIST]
[*]From the Ubuntu/ Linux PC local network access seems fine. I can access the router/ gateway from any Linux PC
[*]I CANNOT access the internet (ADSL) from ANY of the linux PCs
[*]**Internet acccess from the WIndows PC works fine.**
[/LIST]

As far as I can tell all hardware is up and running fine. In any case, it is unlikely that all the linux pcs had  simultaneous cardiac arrest. 

I don't know what else I can possibly check or do short of trying a rebuild one of the linux boxes to see what happens.

There have been **NO** updates or system changes leading into this catastrophe. 

Finally, this post is coming to you from a WindowsXP :(

I really appreciate some help. Thanks

---

### Post by bhankins on 2008-07-25
I am sure you have tried this but I thought I would throw it in there. Are you having dns trouble.  Can you get to or ping something outside by its IP address?

---

### Post by GuiGuy on 2008-07-25
> **bhankins said:**
> I am sure you have tried this but I thought I would throw it in there. Are you having dns trouble.  Can you get to or ping something outside by its IP address?

I can ping the local network but not outside, ie internet addresses.

---

### Post by Aearenda on 2008-07-25
Has anyone mucked with the MAC address filtering (or any other settings) on your gateway?

---

### Post by Aearenda on 2008-07-25
Also, let's see the output from 'route' on Ubuntu, please!

---

### Post by GuiGuy on 2008-07-25
> **bhankins said:**
> I am sure you have tried this but I thought I would throw it in there. Are you having dns trouble.  Can you get to or ping something outside by its IP address?

OK, I've added my ISPs DNS addresses to one of linux PCs list of DNS. It can now access the internet. 

It begs the questions though; why was it previously obtaining the DNS automatically and not now? And why can WindowsXP get the DNS automatically and not Linux?

Very frustrating :confused:

Thanks for the heads up, though.

---

### Post by GuiGuy on 2008-07-25
> **Aearenda said:**
> Has anyone mucked with the MAC address filtering (or any other settings) on your gateway?

Definitely no. The router was reset about a week ago and hadn't been touched since.

---

### Post by bhankins on 2008-07-25
I think it has to be something with the DHCP server. Are you using a linksys router or something for that?  I have had this happen before as well, which is why I asked that initially.

---

### Post by GuiGuy on 2008-07-25
> **Aearenda said:**
> Also, let's see the output from 'route' on Ubuntu, please!

I'm vague on it's usage. Should I get the output to the gateway/ router or beyond?

Thanks

---

### Post by bhankins on 2008-07-25
My issue was I accidentally put a competing dhcp server on the lan.

---

### Post by GuiGuy on 2008-07-25
> **bhankins said:**
> I think it has to be something with the DHCP server. Are you using a linksys router or something for that?  I have had this happen before as well, which is why I asked that initially.

No, I have Netcomm NB9W that's been well behaved to date. I can change to another modem/ router if I need to. But it doesn't explain why WindowsPC are working fine. Only the Linux ones have gone down. 

NB: just got the wife's ASUS EEC out. It's also failing to connect. So maybe it is something on the modem/ router? :confused:

---

### Post by Aearenda on 2008-07-25
'route' just prints the routing table - it's not the same as 'traceroute'. The output looks something like this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         server1         0.0.0.0         UG    0      0        0 eth1

```
All I wanted to see was where the 'gateway' entry pointed. Also, the contents of /etc/resolv.conf would be interesting, in the light of recent comments.

Edit: have there been any electrical storms or power surges in your area recently? I saw one router go weird after a surge - some sockets worked, some didn't.

---

### Post by Aearenda on 2008-07-25
> OK, I've added my ISPs DNS addresses to one of linux PCs list of DNS. It can now access the internet. 
Actually, it sounds as if the ISP has changed their DNS addresses. XP normally gets this automatically through DHCP, and so does Ubuntu if you use Network Manager. Otherwise, it depends on your settings in /etc/network/interfaces (possibly as managed through the GUI).

---

### Post by bhankins on 2008-07-25
Ok shot in the dark here, try this:

grep DHCPACK /var/log/daemon.log

and see if the last offer was from your gateway.

---

### Post by GuiGuy on 2008-07-26
> **GuiGuy said:**
> This is seriously weird and I hope someone can help because the alternative does not bear thinking about:

My mix of four ubuntu hardy variant PCs and one Windows XP PC on a local network has been fine for months. The gateway IP is 192.168.1.1 

Overnight something strange happened. As of this morning:

[LIST]
[*]From the Ubuntu/ Linux PC local network access seems fine. I can access the router/ gateway from any Linux PC
[*]I CANNOT access the internet (ADSL) from ANY of the linux PCs
[*]**Internet acccess from the WIndows PC works fine.**
[/LIST]



So, I managed to kludge it by listing the ISP's DNS addresses. Never needed to do that before, but it seems to be working. Another lesson learnt; things go bump in the night.

Cheers

---

### Post by GuiGuy on 2008-07-26
> **Aearenda said:**
> 
All I wanted to see was where the 'gateway' entry pointed. Also, the contents of /etc/resolv.conf would be interesting, in the light of recent comments.

Edit: have there been any electrical storms or power surges in your area recently? I saw one router go weird after a surge - some sockets worked, some didn't.

```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1

```

The first thing I did when this started was to restore the router settings. In any case it seemed to be functioning correctly in most aspects. 

Anyway, it's more or less working. If I have any more trouble I'll try an alternative router.

Cheers

---

### Post by GuiGuy on 2008-07-26
> **bhankins said:**
> Ok shot in the dark here, try this:

grep DHCPACK /var/log/daemon.log

and see if the last offer was from your gateway.

Right. I'm learning ever new things here. This is what I got

```
Jul 20 20:14:08 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 20 20:28:44 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 20 20:43:12 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 20 23:16:49 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 21 17:17:42 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 11:38:15 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 12:07:40 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 12:14:03 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 12:17:41 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 12:19:05 FF01 dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jul 26 12:55:19 FF01 dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Jul 26 13:48:48 FF01 dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Jul 26 13:57:41 FF01 dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1

```

Is this useful information in any way?

Thanks

---

### Post by GuiGuy on 2008-07-26
> **Aearenda said:**
> Actually, it sounds as if the ISP has changed their DNS addresses. XP normally gets this automatically through DHCP, and so does Ubuntu if you use Network Manager. Otherwise, it depends on your settings in /etc/network/interfaces (possibly as managed through the GUI).

Just checked with the ISP and previous setup advice. The DNS addresses have not changed. 

CHeers

---

### Post by Aearenda on 2008-07-26
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
No default entry, and so no gateway set? That's a little odd. I understand that you have it working now, but if you have any further trouble, please post the contents of /etc/network/interfaces.

---

