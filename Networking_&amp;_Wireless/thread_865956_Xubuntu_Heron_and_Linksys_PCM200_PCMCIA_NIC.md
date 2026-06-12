---
title: "Xubuntu Heron and Linksys PCM200 PCMCIA NIC"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by usmcstitch on 2008-07-21
Hey everyone,

I am running an averatec laptop, where, upon changing out the harddrive, I've caused my onboard NIC to cease functioning.  If you've ever owned an Averatec, then you'll sympathize with me not taking it appart to try to fix it.  And for those who haven't, believe me, its not worth it.  I've built, supported, maintained etc. computers and laptops for over 20 years, and this is the WORST hardware wise.  Anyway, to the point of the post:

On this laptop, I am using Xubuntu Hardy 2.6.24-19-generic.  I have in my posession a Linksys PCM200 PCMCIA NIC that will not get an IP address nor even attempt to connect. The network manager and device manager both see the card, and recognize it as a "Linksys 21x4x DEC-Tulip compatible 10/100 Ethernet" and assigned it as eth1.  Also, in ifconfig there was this:

eth0
Link encap:Ethernet  HWaddr 00:40:45:28:03:e9
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:18 Base address:0x2c00 

eth1     
Link encap:Ethernet  HWaddr 02:13:08:80:20:06
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:1291134 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:16 Base address:0x1000

eth1:avahi Link encap:Ethernet  HWaddr 02:13:08:80:20:06
inet addr:169.254.2.66  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
Interrupt:16 Base address:0x1000

What is eth1:avahi????  I've never seen this.  Anyway.  When i plug in a network cable (indeed several), my lights go on (on the NIC) but I still don't get an IP.  I tried manually inputing one, but that didn't help either.  

For grins and giggles, i plugged this into my Windows Gaming Laptop and it worked up a champ.  I was surfing fine and dandy, so I know the card works.  

I've researched many many posts, both on Ubuntu and other linux fourms as well as the Big G.  None of the posts I've run across apply to my situation or did not offer any help.  I think I need some hand holding here.  I'm not a Linux newborn, but I am still in my infant stage, so be gentle and break it down Barney style for me.  Just let me know what info you need from me.

TIA
Stitch
Semper

---

### Post by usmcstitch on 2008-09-19
Nobody?  Anybody?
:confused:

Nobody has anything after 30+ views?

---

