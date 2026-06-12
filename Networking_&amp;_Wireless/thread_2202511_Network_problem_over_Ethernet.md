---
title: "Network problem over Ethernet"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by ashwah on 2014-01-29
Hi Ubuntu people,

I've only recently switched to Ubuntu so be gentle.

My problem is that I don't seem to be able to talk to anything via my ethernet port on my laptop. For example, if I plug the computer into the router its as if there's no cable there at all. No symbol in the notification area, no lights on the router - nothing.

I've had a little poke about trying to create a new network connection, but with no success.

Anyway this is what ifconfig gives me. And thats about all I know to do...

eth0      Link encap:Ethernet  HWaddr 50:b7:c3:88:72:50            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:241992 (241.9 KB)  TX bytes:241992 (241.9 KB)


wlan0     Link encap:Ethernet  HWaddr c8:f7:33:50:61:71  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::caf7:33ff:fe50:6171/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2400835 (2.4 MB)  TX bytes:623175 (623.1 KB)

---

### Post by newbie-user on 2014-01-29
Have you tried a new network cable? Different LAN port on the router? Figured I'd ask since it's easy to check those things first before messing with the Ubuntu config files.

---

### Post by steeldriver on 2014-01-29
It looks like you have an established wireless connection? I don't think network-manager will drop an established connection in favor of a new one even if the new one might be "better" (e.g. wired GigE versus wireless-g) - you will probably need to disconnect from the wireless connection manually (or uncheck 'Enable wireless') in order to get it to try the wired connection.

---

### Post by Iowan on 2014-01-29
> **steeldriver said:**
> I don't think network-manager will drop an established connection in favor of a new one even if the new one might be "better" (e.g. wired GigE versus wireless-g)
Spanning tree protocol might keep NM from setting up two interfaces in the same subnet.

---

### Post by ashwah on 2014-01-30
Have tried different cable, different router port, different router. Have disconnected from WiFi when trying to get wired connection. Do you need me to post any more output?

---

### Post by cchat on 2014-01-30
I had the same problem.  Had a windows computer, a TV, and a printer on wired network and they worked fine including internet access.  Ubuntu computer wouldn't connect. I finally swapped the cables between my Ubuntu computer and internet modem and everything worked. Internet modem now uses the cable that was on Ubuntu computer vice versa and suddenly everything is happy?  Why ? ? ? ? ? Ain't got a clue.  Something on the Ubuntu box apparently didn't like the cable.  It is now plugged into the router using the other cable, same ports on the router as they originally had and it is happy as a clam. Internet modem worked fine with either cable.  ? ? ? ?  No changes to any setup files at all. Both devices plugged into same ports on the router as they were originally.

---

