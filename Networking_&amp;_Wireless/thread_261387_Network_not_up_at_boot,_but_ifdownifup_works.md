---
title: "Network not up at boot, but ifdown/ifup works?"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by LiteWait on 2006-09-20
strange issue in dapper... network does not come up on boot, but I           can open a terminal and do ifdown eth0/ifup eth0 and it works.

ifconfig says it got a DHCP address from the router, but ping the router says 'no route to host'. 

Any ideas?

---

### Post by wieman01 on 2006-09-20
Dumbest questionn I could think of: Have you installed a firewall (e.g. Firestarter) lately?

---

### Post by lkagan on 2006-09-20
When you say you have a IP address, is that before or after running your ifup?  Also, make sure that your /etc/network/interfaces config file has the line 'auto eth0' assuming eth0 is the network interface you want up at boot.  If you get an IP address after ifup but still can't ping the router, that sounds like your router is set to not respond to smtp requests.

These all may be way off but we have to start somehwere.

Larry Kagan

---

### Post by wieman01 on 2006-09-20
While we're talking about it, could you please show us this file?
> /etc/network/interfaces

---

### Post by LiteWait on 2006-09-23
The issue is the system boots and I try to ping the router and I get "no route to host", but a simple ifdown/ifup the network is up fine.  The working ifconfig is below.

/etc/network/interfaces:

auto eth0
iface eth0 inet dhcp
wireless-channel 11
wireless-mode managed
wireless-keymode open
wireless-key b0f259fbf7ffedd1XXXXXXXXXX ( XXXXX is of course not right)
wireless-essid NETGEAR

ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:30:BD:D1:EA:AA
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fed1:eaaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:850 errors:18 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:986563 (963.4 KiB)  TX bytes:178142 (173.9 KiB)
          Interrupt:3 Base address:0x100

---

### Post by wieman01 on 2006-09-23
I've had the same problem. For some reason I have to restart the network once while the system boots. It's a common problem. So this is why I had to go on both my computers (see the last post):

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

Silly but try. If not, there is a 2nd solution.

---

### Post by wieman01 on 2006-09-23
Second solution... Adding the red lines to your interfaces file:
> auto eth0
iface eth0 inet dhcp
[COLOR="Red"]ifconfig eth0 up
ifconfig eth0 down
ifconfig eth0 up
ifconfig eth0 down[/COLOR]
wireless-channel 11
wireless-mode managed
wireless-keymode open
wireless-key b0f259fbf7ffedd1XXXXXXXXXX ( XXXXX is of course not right)
wireless-essid NETGEAR

---

