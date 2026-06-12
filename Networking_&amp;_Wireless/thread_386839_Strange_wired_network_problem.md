---
title: "Strange wired network problem"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by thecolorifix on 2007-03-17
Ok, this is my first time posting, thanks in advance for any help.

So, I'm running Kubuntu 6.10 Edgy Eft,  I'm on a wired network (cable internet) using a netgear router. When I set up the computer I just plugged in the ethernet cable, everything worked fine. 

Now, I'm getting dropouts where my download goes to zero when I'm trying to web surf (monitoring the network with superkarambas desktop widget). The upload usually  reads on the widget as fine, but sometimes they both go down to zero. It'll drop for about 10-15 seconds then shoot all the way back up.

And this isn't happening on any of the 5 windows computers in the house, doesn't happen with the wireless (on the odd occasion my roommate uses his laptop),

I'm very new to Linux, and I have no idea how to even go about looking into what this might be. But it's very frustrating as I'm paying extra to 6mbps internet and it's working at about 56k speed, lol.

Again, thank you for any help, it's much appreciated.

---

### Post by Kobalt on 2007-03-17
The problem is actually bizarre... 
Did it happen after you installed something particular : additional firewall, antivirus, updates... ?
Can you please post us the result of ```
ifconfig
```

---

### Post by thecolorifix on 2007-03-17
eth0      Link encap:Ethernet  HWaddr 00:40:05:80:2A:17
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe80:2a17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1757103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2187861 errors:0 dropped:0 overruns:15 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:882329519 (841.4 MiB)  TX bytes:1661538305 (1.5 GiB)
          Interrupt:185 Base address:0x6f00

eth1      Link encap:Ethernet  HWaddr 00:0C:6E:56:2A:13
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5409557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5409557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3271273676 (3.0 GiB)  TX bytes:3271273676 (3.0 GiB)

---

### Post by Mr. C. on 2007-03-17
Disable IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Be sure your router's firmware is up to date.

Test again after these changes.

MrC

---

### Post by thecolorifix on 2007-03-17
> **Mr. C. said:**
> Disable IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Be sure your router's firmware is up to date.

Test again after these changes.

MrC

Well, in the ten minutes or so sice I restarted, I've had NO problems (usually it would strt within the first few minutes).

Man, I'd heard people here were good, but damn.

Thank you so much for the help, I'll definitely post up if it happens again, but it's looking like that completely took care of it.

And hey, if you feel like helping with another problem (lol): Whenever I have the superkaramba widget "GlassMonitor" on (the one I was using to monitor network activity) my cursor has little stutters where it freezes for half a second. Any Ideas?

---

### Post by Mr. C. on 2007-03-17
Glad it worked out.

I don't know much about your second question.  Post it to one of the other forms, and I"m sure you'll find better responses than I could give.

Cheers,
MrC

---

### Post by thecolorifix on 2007-03-17
I knew I shouldn't have been so optimistic, lol

it seems like when I went and turned another computer on the network on it started happening again. Then I turned that computer off and it's still happening.

I'm gonna try to restart again and see what happens. brb.

---

### Post by thecolorifix on 2007-03-17
so it only happens when the network is beaing/has been used by another computer (oh good, that's only 98% of the time, lol), it seems.

---

### Post by Mr. C. on 2007-03-18
Another Ubuntu system ?  Perhaps also with IPv6 ?

Did you check for and update the firmware in your router ?

MrC

---

