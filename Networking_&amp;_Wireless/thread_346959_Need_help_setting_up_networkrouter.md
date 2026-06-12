---
title: "Need help setting up network/router"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by tjk on 2007-01-26
I have tried everything to setup a LAN with 2 computers (1 running Ubuntu /other main comp running KDE) to the Internet.  I have probably spent arount 100 hours with NO luck!!  I have tried different cables, NIC cards -- I tried using a switcher rather then the router and still am not able to get anything working (except 1 Internet connection).  [COLOR="Black"]Please help[/COLOR]

Context:
I run a DSL modem on a server that only allows one mac address (therefore, I don't know if I can use my router).  I currently have three nic ports on my main computer (1 port is onboard and is currently disabled (eth1) -- since I thought that it may be conflicting.  I have been able to get one card working at a time -- that is why I have Internet access (eth0).  I have tried so many different firewalls and edited so many ip tables/config files that I am concerned that I have messed up the network system beyond repair.

I would like to know if it would be best to run the router between the DSL modem and the main comp. w/ a crossover cable from the main comp to the second comp. <OR> can I run 2 lines from the router (given that I am only allowed 1 mac address)?  As well, should it be alright to remove one of my nic cards from my main computer and enable the internal port?

This may be helpful:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:5A:A8:1E:76
          inet addr:64.180.117.235  Bcast:64.180.119.255  Mask:255.255.248.0
          inet6 addr: fe80::210:5aff:fea8:1e76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2726052 (2.5 MiB)  TX bytes:340943 (332.9 KiB)
          Interrupt:185 Base address:0xe000

eth2      Link encap:Ethernet  HWaddr 00:50:BA:26:AC:49
          inet6 addr: fe80::250:baff:fe26:ac49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27074 (26.4 KiB)  TX bytes:13266 (12.9 KiB)
          Interrupt:193 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:648 (648.0 b)  TX bytes:648 (648.0 b)

---

### Post by chili555 on 2007-01-26
Unless I am missing something, I believe your router has only one MAC address.

So, I suggest you connect your router to the DSL modem and hook as many computers as you want to the router. To the DSL modem, the router looks like one computer with one MAC address that wants a web page, google.com, for example. The DSL modem goes out on the internet and gets it and hands it to the router.

The router does Network Address Translation (NAT) and says which computer wanted google.com...hmmm...computer number 1 (let's call him 192.168.1.2, for example). OK, number 1, here's your page. Now computer number 2 wants a page, ubuntuforums.org, for example. Number 2 (let's call her 192.168.1.3) requests the page from the router and the process is the same.

Or, to put it the "brute strength and awkwardness" way, try it and see what happens. Let us know.

Your eth0 looks like it is connected, but directly to the DSL modem. I'd simply insert the router in between the DSL modem and the computers and restart.

---

### Post by tjk on 2007-01-30
Hey, I just wanted to say thanks for the tips -- they were all I needed to get things working through my router/network.

---

