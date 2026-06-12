---
title: "Can I do something to speed up Internet?"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by prshah on 2008-06-29
Hello,

Background:

I have a single machine connecting to the Internet through a router. I use PPPoE.

My ISP has _supposedly_ upgraded all customers to 2mbps, but since I've taken an unlimited account, I _think_ I'm throttled to 256kbps (That's what the ISP's website says, but they don't exactly hold any record when it comes to accuracy, updating, or even website design)

My router shows connection of (Upstream data rate) 2048 kbps and (Downstream data rate) of 511 kbps, but I get download rates of _only_ 30~35kBps (Bytes, not bits) which seems to be consistent with 256kbps. I got the same rates even when I had windows, but at that time the connection was 256kbps and not 2mbps. Now I don't have Windows and cannot check.

EndBackground.

Now, my question is, is there anything I can do on my end to speed up data transfer or is this normal for 256kbps? 

Even when not downloading, browsing is _slightly_ sluggish. I considered changing to OpenDNS server, but gave up quickly when I conducted this little check: (The first is my ISP-assigned DNS servers, the second OpenDNS servers) ```

Sun Jun 29 12:53:40 ~:$ ping -c 5 218.248.255.145 
PING 218.248.255.145 (218.248.255.145) 56(84) bytes of data.
64 bytes from 218.248.255.145: icmp_seq=1 ttl=253 [color=red]time=8.55 ms[/color]
64 bytes from 218.248.255.145: icmp_seq=2 ttl=253 [color=red]time=8.30 ms[/color]
64 bytes from 218.248.255.145: icmp_seq=3 ttl=253 [color=red]time=8.37 ms[/color]
64 bytes from 218.248.255.145: icmp_seq=4 ttl=253 [color=red]time=8.77 ms[/color]
64 bytes from 218.248.255.145: icmp_seq=5 ttl=253 [color=red]time=8.58 ms[/color]

--- 218.248.255.145 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 8.308/8.519/8.777/0.202 ms

Sun Jun 29 12:54:54 ~:$ ping -c 5 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=2 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=5 ttl=53 [color=red]time=294 ms[/color]
--- 208.67.222.222 ping statistics ---
5 packets transmitted, 3 received, 40% packet loss, time 3998ms
rtt min/avg/max/mdev = 292.752/293.268/294.135/0.878 ms

```

Other tweaks: Disabled ipv6 (in os+browser), set MTU 1492.

I also find that sites like youTube and most (high bitrate) internet radio services are buffering quite a bit. (Even when not running anything else).

I don't mind living with a slower connection, but if I'm missing some important settings that can cause a boost, I'd appreciate it.

---

