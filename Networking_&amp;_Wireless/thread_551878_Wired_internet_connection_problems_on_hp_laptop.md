---
title: "Wired internet connection problems on hp laptop"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Marcipicus on 2007-09-15
Hi I have an hp dv2412 laptop with kubuntu 7.04 which isn't connecting to the internet through the wired connection.

When i plug the ethernet cable into the laptop the knetwork icon shows that i have an active connection but i can't connect to anything (apt servers etc.)

I am not familiar with networking so a little guidance will be needed to diagnose the problem

---

### Post by rivalarrival on 2007-09-15
There's various levels of "broken" when it comes to ethernet  and tcp/ip connections.

Easiest way to diagnose is to open a terminal window.

type: 
```
 
ifconfig

```
For the record: prepend "probably" to all of my absolute statements...  Weird things happen...

You should be able to find an IP address - if it is in the 169.x.x.x, then you're not getting an IP address from your router. If it's 192.168.x.x or 172.x.x.x or 10.x.x.x then you're behind a router of some sort (possibly your isp's router) (This is a good thing)
If it's just about anything else, you've got an internet IP address (this is also good)
If it's 0.0.0.0 then your connection isn't configured. 

If you've got anything but 169.x.x.x or 0.0.0.0, try:
```

ping 64.233.167.99

```
which is Google's IP address. (You'll have to press "ctrl+C" to break out of ping)

If it replies something along the lines of "64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=244 time=24.5 ms" and you still can't connect to the internet, then DNS isn't working right. If you don't get that response, try pinging an IP address on your local network (Unless you changed it, your router (if you have one) is probably 192.168.1.1)

How are you connected to the internet? Directly to a cable or DSL modem? Through a router?

The more you can tell the community, the better solutions you'll get back!  :)

---

### Post by Marcipicus on 2007-09-16
Thanks for the help. I am connected directly to the cable modem. I am switching the ethernet cable between my desktop and laptop to make posts so some of this info might change.

ifconfig output is

```
eth0      Link encap:Ethernet  HWaddr 00:16:D3:AA:1A:0F
          inet6 addr: fe80::216:d3ff:feaa:1a0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10936 (10.6 KiB)  TX bytes:5039 (4.9 KiB)
          Interrupt:20 Base address:0xe000

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:AA:1A:0F
          inet addr:169.254.4.110  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3696 (3.6 KiB)  TX bytes:3696 (3.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:7C:55:46
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Memory:b3000000-b3004000

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:73:7C:55:46
          inet addr:169.254.5.39  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:b3000000-b3004000
```

---

### Post by noob12 on 2007-09-17
You don't have any address assigned.  

Are you supposed to get an address automatically by DHCP from your ISP / modem?

Is your modem require a PPPOE client or does it provide full IP on ethernet?

Did you have another machine connected to this modem before?

---

