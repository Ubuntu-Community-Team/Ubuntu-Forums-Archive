---
title: "HP Proliant Micro Server G8 - Wired network Dropouts"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by jimmyboy101 on 2013-12-20
Having some issues with my New toy, a HP Proliant Micro Server G8 1608t

It appears to be dropping the ethernet connection. I have noticed that it does drop more regularly if I start using VNC (not so much if i just SSH into the box) however as Ill be using this as a Media box its going to cause issues. 

I thought it might be caused by the CPU or RAM maxing out when i vnc in however both are sitting at around 5-20 percent.

I am running Ubuntu 13.10 Desktop edition. 

I am getting the following errors in Syslog 

```
Dec 20 21:41:40 cubinator kernel: [  755.486683] tg3 0000:03:00.0 eth0: EEE is enabledDec 20 21:41:40 cubinator NetworkManager[921]: <info> (eth0): carrier now ON (device state 100)
Dec 20 21:41:49 cubinator NetworkManager[921]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 20 21:41:49 cubinator kernel: [  763.906105] tg3 0000:03:00.0 eth0: Link is down
Dec 20 21:41:52 cubinator NetworkManager[921]: <info> (eth0): carrier now ON (device state 100)
Dec 20 21:41:52 cubinator kernel: [  766.805442] tg3 0000:03:00.0 eth0: Link is up at 1000 Mbps, full duplex
Dec 20 21:41:52 cubinator kernel: [  766.805446] tg3 0000:03:00.0 eth0: Flow control is on for TX and on for RX
Dec 20 21:41:52 cubinator kernel: [  766.805448] tg3 0000:03:00.0 eth0: EEE is enabled
Dec 20 21:41:56 cubinator kernel: [  771.027578] tg3 0000:03:00.0 eth0: Link is down
Dec 20 21:41:56 cubinator NetworkManager[921]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 20 21:41:59 cubinator kernel: [  773.932163] tg3 0000:03:00.0 eth0: Link is up at 1000 Mbps, full duplex
Dec 20 21:41:59 cubinator kernel: [  773.932171] tg3 0000:03:00.0 eth0: Flow control is on for TX and on for RX
Dec 20 21:41:59 cubinator kernel: [  773.932173] tg3 0000:03:00.0 eth0: EEE is enabled
Dec 20 21:41:59 cubinator NetworkManager[921]: <info> (eth0): carrier now ON (device state 100)
Dec 20 21:42:10 cubinator kernel: [  785.183322] tg3 0000:03:00.0 eth0: Link is down
Dec 20 21:42:10 cubinator NetworkManager[921]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 20 21:42:13 cubinator kernel: [  788.101618] tg3 0000:03:00.0 eth0: Link is up at 1000 Mbps, full duplex
Dec 20 21:42:13 cubinator kernel: [  788.101625] tg3 0000:03:00.0 eth0: Flow control is on for TX and on for RX
Dec 20 21:42:13 cubinator kernel: [  788.101627] tg3 0000:03:00.0 eth0: EEE is enabled
Dec 20 21:42:13 cubinator NetworkManager[921]: <info> (eth0): carrier now ON (device state 100)
Dec 20 21:42:16 cubinator kernel: [  791.442557] tg3 0000:03:00.0 eth0: Link is down
Dec 20 21:42:16 cubinator NetworkManager[921]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 20 21:42:19 cubinator kernel: [  794.429109] tg3 0000:03:00.0 eth0: Link is up at 1000 Mbps, full duplex
Dec 20 21:42:19 cubinator kernel: [  794.429116] tg3 0000:03:00.0 eth0: Flow control is on for TX and on for RX
Dec 20 21:42:19 cubinator kernel: [  794.429118] tg3 0000:03:00.0 eth0: EEE is enabled
Dec 20 21:42:19 cubinator NetworkManager[921]: <info> (eth0): carrier now ON (device state 100)
Dec 20 21:42:23 cubinator kernel: [  797.864150] tg3 0000:03:00.0 eth0: Link is down
Dec 20 21:42:23 cubinator NetworkManager[921]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 20 21:42:26 cubinator kernel: [  800.860152] tg3 0000:03:00.0 eth0: Link is up at 1000 Mbps, full duplex
Dec 20 21:42:26 cubinator kernel: [  800.860160] tg3 0000:03:00.0 eth0: Flow control is on for TX and on for RX
Dec 20 21:42:26 cubinator kernel: [  800.860161] tg3 0000:03:00.0 eth0: EEE is enabled



```

Any Ideas?

---

### Post by tgalati4 on 2013-12-20
Have you swapped cables to see if you have a bad cable?  Swap ports on the router if the cable swap doesn't change the intermittent behavior.

---

### Post by jimmyboy101 on 2013-12-20
Just tried it then (would be unlucky but still worth a shot) no good
Tried a different cable. Also tried the second Ethernet slot and a different port on the switch/router
Also plugged laptop directly into the device and still had the dropouts
Network connection isnt dropping on the iLo port however thats just for managing the hardware

Im really confused about the cause of it. I have tried sending large packets to the device and it seems to handle it fine with no packetloss (only increased latency which is to be expected 
```
Reply from 192.168.1.136: bytes=65500 time=17ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=18ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=62ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=31ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=13ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=15ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=18ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=17ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=19ms TTL=64
Reply from 192.168.1.136: bytes=65500 time=13ms TTL=64

``` 
However as soon as i ask vnc to draw anything it starts dropping out 
```
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Request timed out.
Reply from 192.168.1.136: bytes=32 time=1ms TTL=64
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Request timed out.
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Request timed out.
Reply from 192.168.1.136: bytes=32 time=4ms TTL=64
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Request timed out.
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Reply from 192.168.1.136: bytes=32 time=3ms TTL=64
Request timed out.

``` 
Same story if i SSH in and update the packages. 

So system initiated traffic kills the link. however my large pings dont seem to bother it at all

---

