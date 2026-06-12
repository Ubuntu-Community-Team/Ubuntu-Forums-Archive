---
title: "Please someone make my wireless card work!"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by dragonlor20 on 2006-08-25
Ok, I feel like I have read every HOWTO and workaround for my card that this forum has to offer. I have tried start-up scripts, I have changed my /etc/network/interfaces countless times. I have locked myself out of gnome and let myself back in. I just want this thing to work. Would someone please sit down and just walk me through this? You would make me the happiest Ubuntu user in the world, I gurantee it. Please don't send me to another HOWTO... :-(

Here is the deal:

I have a Linksys WMP54G wireless card on a desktop PC. 

It detects networks around here (there are lots of them) so it does work, but no internet (webpages, email, none of that stuff).

---

### Post by AzraelUK on 2006-08-25
Type iwconfig and ifconfig into the console, show us what you get.

---

### Post by dragonlor20 on 2006-08-25
> **AzraelUK said:**
> Type iwconfig and ifconfig into the console, show us what you get.

iwconfig returns with:

> lo        no wireless extensions.


eth0      no wireless extensions.


ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sit0      no wireless extensions.

and ifconfig returns with:

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5520 (5.3 KiB)  TX bytes:5520 (5.3 KiB)



ra0       Link encap:Ethernet  HWaddr 00:16:B6:99:4E:DC  
          inet6 addr: fe80::216:b6ff:fe99:4edc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:726873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54046457 (51.5 MiB)  TX bytes:0 (0.0 b)
          Interrupt:217 


Thanks for the interest in my problem...

---

### Post by AzraelUK on 2006-08-25
That's very good so far, it means ubuntu knows your card is there. I have to confess I don't know much about the Ralink chipset, but here is what I would do: Open up NetworkManager (System>Administration>Networking) and configure your card to use DHCP, and set anything else you need to there. This should get you on a network, but I can't guarantee it'll be *your* network ;)

---

### Post by dragonlor20 on 2006-08-25
> **AzraelUK said:**
> That's very good so far, it means ubuntu knows your card is there. I have to confess I don't know much about the Ralink chipset, but here is what I would do: Open up NetworkManager (System>Administration>Networking) and configure your card to use DHCP, and set anything else you need to there. This should get you on a network, but I can't guarantee it'll be *your* network ;)

:-( No luck... Same problem after I configure everything, no internet... I meant to say in my original post though, I don't have access to the router, but it is open access so no key needed or anything...

---

