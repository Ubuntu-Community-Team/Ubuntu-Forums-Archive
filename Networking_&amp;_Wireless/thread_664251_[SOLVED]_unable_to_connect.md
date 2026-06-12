---
title: "[SOLVED] unable to connect"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Himie on 2008-01-11
hi im having a problem with linux, i have both windows and linux ubuntu installed, on windows i have internet connection but when i go to ubuntu i cant connect, the first day when i installed it i could connect easily but now it doesnt, wireless connection is active and can be used but not wired connection on linux

---

### Post by Hightide on 2008-01-11
HI can you post the output of ifconfig

goto Applications/Accessories/Terminal

Type: ifconfig

:)

---

### Post by Himie on 2008-01-11
```
eth0      Link encap:Ethernet  HWaddr 00:07:95:DF:8D:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:A1:B0:00:E9:52  
          inet6 addr: fe80::2a1:b0ff:fe00:e952/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8f00 

eth1:avah Link encap:Ethernet  HWaddr 00:A1:B0:00:E9:52  
          inet addr:169.254.7.64  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x8f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:394 (394.0 b)  TX bytes:394 (394.0 b)


```

ok here it is

---

### Post by Himie on 2008-01-11
bump, please i really need help its my first time with linux and if i cant access internet i will have to erase it

---

### Post by MrLaister on 2008-01-11
so you say you have wired networking with windows but when you reboot into ubuntu there isn't an internet connection provided by the wired connection?

If this is the case, try shutting down the computer and physically unplugging it for a few tens of seconds, this rectified a similar problem of mine which has sent me crazy over the past 3 hours!

My network card was a RTL-8139/8139C/8139C+, but perhaps this is a translatable problem?

Good luck with your debugging :)

MrLaister

---

### Post by Himie on 2008-01-11
> **MrLaister said:**
> so you say you have wired networking with windows but when you reboot into ubuntu there isn't an internet connection provided by the wired connection?

If this is the case, try shutting down the computer and physically unplugging it for a few tens of seconds, this rectified a similar problem of mine which has sent me crazy over the past 3 hours!

My network card was a RTL-8139/8139C/8139C+, but perhaps this is a translatable problem?

Good luck with your debugging :)

MrLaister

ok thx ill try i think i have a smilar card, so i unlpug the computer and the modem?

---

### Post by Himie on 2008-01-11
OMG ty so much ^^ i would never think of unplugging the computer

but why did it work?

---

### Post by MrLaister on 2008-01-11
To be honest, I'm still wondering about that myself! I kind of stumbled upon the problem!

I have made a post for some real experts to see if they can figure something out, I can imagine people other than me have ripped their hair out over this situation thinking it was kernel problem/bad packages/hardware problems, when all it was is probably the network card being 'held' in a certain state which linux doesn't agree with

Congrats on the networking, and I hope this has restored some faith in the power of the community :)

MrLaister

---

### Post by Himie on 2008-01-11
> **MrLaister said:**
> To be honest, I'm still wondering about that myself! I kind of stumbled upon the problem!

I have made a post for some real experts to see if they can figure something out, I can imagine people other than me have ripped their hair out over this situation thinking it was kernel problem/bad packages/hardware problems, when all it was is probably the network card being 'held' in a certain state which linux doesn't agree with

Congrats on the networking, and I hope this has restored some faith in the power of the community :)

MrLaister

lol yea i was ripping my hair off thinking i wasted my time on linux, i always wanted to try it and now i can ^^

again thx so much :)

---

### Post by Himie on 2008-01-13
ok heres something that might help explain

my internet connection remains good on linux as long as i dont boot windows, if i boot windows and after that i want to return to ubuntu i cant connect so i have to disconnect my computer so the internet can work, but i only have to do it if i run windows

---

### Post by ugm6hr on 2008-01-26
This is the same problem: [http://ubuntuforums.org/showthread.php?p=4208875#post4208875](http://ubuntuforums.org/showthread.php?p=4208875#post4208875)

---

