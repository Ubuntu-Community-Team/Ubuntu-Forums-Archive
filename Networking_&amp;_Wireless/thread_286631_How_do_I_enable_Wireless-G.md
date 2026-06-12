---
title: "How do I enable Wireless-G?"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by inabsolutes on 2006-10-28
Hi,

I've gotten my wireless card working by following the guide [here]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=wireless").  I have a Broadcom 4306 802.11 b/g, and I'm using Dapper.  
The problem is, I have to set my wireless to mixed mode to be able to connect, because my wireless is only transmitting in wireless-b.  I'd like to get it going in wireless-g, but I don't know how to set that up.  

This is my iwconfig:
> eth1      IEEE 802.11b/g  ESSID:"JesusChrist"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:76:54:9F
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr: off   Fragment thr: off
          Link Quality=100/100  Signal level=3/3  Noise level=192/100
          Rx invalid nwid:0  Rx invalid crypt:44  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



These forums have been fantastic getting me up and running.  You guys are doing a great job.  Thanks.

---

### Post by squibT on 2006-10-28
sudo iwconfig eth0 rate 54M (from 11M)

I use NDISWrapper now because it installs my wpc54gs drivers (latests drivers)at 54M....

---

### Post by inabsolutes on 2006-10-28
Thanks squibT.

I tried to change it with this code:
```
sudo iwconfig eth1 rate 54M
```

When I run iwconfig again, the changes show up, but I still can't connect to a wireless-G router and after I've tried to connect, my rate reverts to 11 Mb/s again.  Is there some way to make the change permanent that I'm missing?

---

### Post by squibT on 2006-10-28
If you can, set you router to Auto not G Only, DD-WRT can do this if your router supports it.

sudo iwpriv wlan0 (or your ethX) network_type g
your card may not support this cmd

Dunno how to make 54M stick...works for me till I log out. Script maybe? 

Try NDIS and drivers specifically make for your NIC

Thats all I can think of....sorry....

---

