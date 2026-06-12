---
title: "Internet Faster than LAN"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by minger_88 on 2014-03-17
OK, so I've felt like I've had a slow local network for some time, so tonight I ran some tests and ... am confused. It started by not being able to stream anything through ps3mediaserver. Then, I realized that I wasn't even able to stream music off a shared network drive (seriously, I couldn't stream mp3s).

So, my setup is as follows:
Router - WRT54GL
Desktop - Wired to Router Running Precise
Laptop - Wireless Running Saucy
PS3 - Wireless (we don't need to worry about)

Generally, I use(d) my desktop as network storage -- and connect from my laptop. If I run iperf on the desktop
```

~ $ iperf -c 192.168.1.102 -p 6777
------------------------------------------------------------
Client connecting to 192.168.1.102, TCP port 6777
TCP window size: 22.9 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.101 port 37782 connected with 192.168.1.102 port 6777
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.2 sec  6.00 MBytes  4.92 Mbits/sec

```
I'm getting only 5 Mbit/sec. Now, if I run an interest speedtest from my laptop (via wireless), I get 5.2 Mbit/sec (I used dsl reports speed test). 

So, if I run my laptop in server mode and use my desktop as the client
```

~ $ iperf -c 192.168.1.101 -p 6777
------------------------------------------------------------
Client connecting to 192.168.1.101, TCP port 6777
TCP window size: 23.5 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.102 port 33580 connected with 192.168.1.101 port 6777
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  13.4 MBytes  11.1 Mbits/sec

```
When I run a speed test on my desktop I am able to get 9 Mbit/sec. 

So, I'm expecting 10-15 Mbit/sec internet ... I suppose with a 10/100 router, I'm expecting 10 Mbit/sec LAN, but don't understand why I'm only getting it one way. 

Does anyone have any ideas how I can get better network speed from my desktop? I really appreciate any help - thanks a bunch.

---

### Post by TheFu on 2014-03-18
Troubleshooting wireless is hard - especially from here. There are hundreds of issues that could cause slow performance - many of them are out of your control.
So ... connect everything with wired ethernet and test again. If everything works around 90Mbps when wired, THEN we can move on to the wireless issues.  Here's a [wifi router checklist]("http://blog.jdpfu.com/pages/wifi-security") that might help. The *Channel Selection* part is likely all we can do from here.

---

### Post by minger_88 on 2014-03-19
OK, so laptop plugged into router, I am 94 Mbit/sec when laptop is server, and 88 Mbit/sec when desktop is server. That's better. 

Next I unplugged the wired connection and sit the laptop basically on top of the wireless router -- 100% 
Laptop serving to Desktop: 18 Mbit/sec
Desktop serving to Laptop: 20 Mbit/sec. 

Looking your through your link, I started tinkering. I realized at first there was an abundance of networks on the channel I was using. I switched to a channel with no other networks
Laptop serving to Desktop: 20 Mbit/sec
Desktop serving to Laptop: 21 Mbit/sec.

I suppose a little better. So I have a 5x speedup when I have a better connection. Is there hardware to help improve the range or am I limited some place else? Should I be concerned with this wireless speed or should I focus on connection? 

Thanks a bunch

---

### Post by TheFu on 2014-03-19
The wifi router you have .. is 54Mbps - IN THEORY. Every wifi device added approximately halves that bandwidth.
```
Dev	Max
0	54
1	27
2	13.5
3	6.75
4	3.375
5	1.6875

```
So, connect fewer devices to the wifi. Fewer wifi signals means better connections and more throughput. Use an uncluttered channel - hopefully from channels 1, 6, 11.
The radios in every device matter - some are better than others, I hear.
WiFi-G matters. You could get a 300Mbps "N" router and upgrade all the wifi components inside every machine.  Don't expect to see 300Mbps.

The WRT54 is pretty old. There are lots of newer routers - GigE wired that will perform better.

BTW, I avoid wifi and use wired everywhere. This is after designing wifi deployments for over 1200 locations.  wifi cannot be trusted. Even inside your house, there are atmospheric conditions that impact bandwidth. Hard to believe, but true.

---

### Post by minger_88 on 2014-03-25
So, I got a new wireless router -- $20, not a terrible investment. I found that I don't really get any better speeds. 

[B]WRT54
[/B]Internet Speed: 10 Mbit/sec
LAN Speed: 21 Mbit/sec[B]

TP-WR841N[/B]
Internet Speed: 11 Mbit/sec
LAN Speed: 30 Mbit/sec

So, my LAN speed is a bit faster, but I was (ahem, honestly) expecting a bigger increase. However, I think I was having intermittent connection issues with the previous router. In the living room, my "connection" is now 70% from some odd 40%-ish. I also find that I can now stream media from my desktop in the back of the house. 

So ... things appear (fingers crossed) to be better. While I don't see significantly higher speeds, I think the connection is more stable is working much better.

---

### Post by TheFu on 2014-03-26
Be certain to replace the factory firmware on the router. Pretty much every vendor has been caught with bugs/backdoors, so loading tomato, ddwrt, openwrt, is a good idea.

If you just changed the router, then the PCs still have old radios and performance doesn't really change. 70% (whatever that means), isn't very good either. You are lucky to stream and may need to increase the buffer sizes in the client programs. There is always powerline networking for situations like yours to extend networking to other parts of the house.

---

