---
title: "my NIC keeps spamming new MAC adress to the DHCP and getting my connection shut down"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Pekkalainen on 2007-05-26
Hi!

I have a rather complicated problem with my network cards and of course I come here looking for ways to troubleshoot.

I have a desktop and a laptop, both with Intel network cards. I keep getting my internet connection shut down because one of them is constantly spamming a new mac adress to my ISPs DHCP server. 

How do I figure out wich one of them is doing this and how do I solve it? The guy at the tech support said it could be a malfunctioning driver or a busted network card. 

Does ubuntu provide crappy drivers? The thought scares me :(

Thanks in advance!

---

### Post by Pekkalainen on 2007-05-26
*bump*

I bump this as my ISP is getting kind of pissed off at me :???:

---

### Post by dmizer on 2007-05-27
do you not have a router?

you can take a look at your broadcasted mac address by looking at the output of ifconfig:
```
$ ifconfig
eth0      Link encap:Ethernet  [COLOR="Red"]HWaddr 00:C0:9F:76:86:1E[/COLOR]  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99898908 (95.2 MiB)  TX bytes:17795661 (16.9 MiB)
          Interrupt:10 Base address:0x2800
```
i've highlited my own mac address information in red.

but this is not your problem.

you have two computers.  and your isp authenticates you via mac address.  each computer you use has a unique mac address.  so, every time you connect to the internet with your desktop, it sends your desktop mac to your isp who then authenticates it.  then, later, when you use your laptop ... your laptop sends your isp its mac address, and your isp records a different mac.

this problem can be further compounded if you have your deskop and laptop both pluged directly into your modem (one with ethernet and another with usb).

your fix here is most likely going to be to simply purchase a router.

edit:
and once you fix this "issue" by purchasing a router, you should send a nasty letter to your isp for being so pig headed.

---

### Post by Pekkalainen on 2007-05-28
Well my ISP allows 5 connections per account and somehow I seem to be breaking that limit with my 2 computers. They are hooked up to a gigabit switch with 5 ports, and then I have the switch connected to the broadband outlet in my apartment. we are talking LAN not DSL, maybe I should have mentioned that. He said it could be the switch that is acting up as well :-k  :-k

Neither of my comps seem to be switching mac adresses. I have checked both and they seem to retain the same adress all the time.

---

### Post by dmizer on 2007-05-28
what are the respective ip addresses of your machines?  are they the same or different?

i'd be reluctant to blame the problem on your switch.

---

### Post by cyberbat on 2007-05-28
I once experienced a new virus that can duplicate MAC addresses, but it only affected Windows.

This virus can duplicate MAC addresses such that 2 or more PCs can have the same MAC address and makes the network break down.

---

### Post by Pekkalainen on 2007-05-29
eth0     Link encap:Ethernet  HWaddr 00:03:47:AD:73:6B
          inet addr:213.113.160.213  Bcast:213.113.160.255  Mask:255.255.255.128
          inet6 addr: fe80::203:47ff:fead:736b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8882949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14830953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1246250739 (1.1 GiB)  TX bytes:2758662929 (2.5 GiB)

is what my desktop says, the laptop has a different mac adress and IP. I will post it shortly.


eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:54:13  
          inet addr:213.113.160.137  Bcast:213.113.160.255  Mask:255.255.255.128
          inet6 addr: fe80::2a0:d1ff:fec1:5413/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33002 (32.2 KiB)  TX bytes:11877 (11.5 KiB)
          Interrupt:16 Base address:0x6000 

is what my laptop says. I see no MAC adress changing or anything.


My desktop runs dual boot Win 2k and Kubuntu Feisty and my laptop is strictly Ubuntu Feisty if its of any help,

I just found out from the company that makes my laptop that it actually uses the Realtek RTL8111B chipset. My bad..

---

