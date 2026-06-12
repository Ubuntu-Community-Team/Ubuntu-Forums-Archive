---
title: "[SOLVED] NetGear VPN111 Wireless USB connects but no internet + how to auto-accept we"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by benoka on 2008-11-28
I have an older (2003) Acer Travelmate 800, one of the first with integrated wireless card. It works well on both, XP and Ubuntu (8.10).

I have a NetGear router and a NetGear wireless USB card (WPN111) that I could successfully install with ndiswrapper.

Now, both are connected, see ifconfig (excluding loopback and eth0, my normal LAN connection, disconnected):

eth1      Link encap:Ethernet  HWaddr 00:04:23:4b:d7:61  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4790177 (4.7 MB)  TX bytes:659327 (659.3 KB)
          Interrupt:11 Base address:0x6000 Memory:d0206000-d0206fff

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b2:bc:fb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17615 (17.6 KB)  TX bytes:5964 (5.9 KB)

netstat -rn gives this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
  
With this setting it seems to only use my built-in wireless card as when I test the connection speed (speedtest.net) then I get a response of around 5 Mbit/s although the WPN111 runs at around 15 Mbit/s (official speed said by ISP is 20 Mbit/s)

As I have no option in my bios to disable the built-in wireless card, I tried with bringing it down via terminal (by the way, no option in network management GUI to enable/disable cards or choose the one to be used):

sudo ifconfig eth1 down

This is making eth1 disappearing from ifconfig, wlan0 is still alive and having a valid IP.

Now it connects to the router ok (can also be pinged; router IP: 192.168.1.1) but will not connect to the internet.

I also tried to de-activate the built-in wireless card with the laptop's wireless button but that brings the whole wireless connection down, even my WPN111 USB one.

Another question: I have to click ok on the already set wep password settings at every boot, is that normal?

I appreciate any help!

Thank you!

ben

---

### Post by benoka on 2008-11-30
ok, it seems I'll have to go back to windows, sad story...

---

### Post by benoka on 2008-12-02
wlan0 activated by bringing eth1 down:

sudo ifconfig eth1 down

then adding the route of the router's IP to wlan0:

sudo route add default gw 192.168.1.1 dev wlan0

(solution provided by simplexio on #ubuntu channel on IRC - Thank you!!!)

still waiting for auto-acceptance of the WEP...

---

### Post by benoka on 2008-12-02
all my problems (even setting fixed IP that seemed to cause a problem for the standard network configuration GUI) have been resolved by installing WICD

[http://kubuntuforums.net/forums/index.php?topic=3099106.0](http://kubuntuforums.net/forums/index.php?topic=3099106.0)
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

it's a pitty how bad networking is in ubuntu 8.10 for an average user like me

---

### Post by bschultzjames on 2008-12-05
I am having a similar problem...I can connect to my wireless network at home, but cannot connect to the internet.  I know the wireless router works because my windows laptop connects just fine to wireless internet.


any thoughts?


thanks!

---

### Post by benoka on 2008-12-06
Try WICD, it really did solve the problem (internet connection is ok now, fixed IP set, wep password not required at startup anymore). If you have questions about how to setup WICD, let me know. Setting up without WICD is still a big question for me too... ;)

good luck!

---

