---
title: "[SOLVED] Contantly resetting wrt54g, losing eth connection"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by psycosmyth on 2008-08-11
I have ran this by several people and have not found an answer.
I have a new Linksys WRT54GS with v8 firmware. I have had a time setting up my connection to this router with many distros. Wireless is fine and I don't use windows so I don't want to go there, nearly every thread or info I found does. When I type Ifconfig I get eth with a different number after each boot. It got to eth20 and quit. It changes each time. I did ifup and down and that helped for a few days. Here is my output.

eth20     Link encap:Ethernet  HWaddr 00:00:6c:4b:39:29  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe4b:3929/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5032639 (4.7 MB)  TX bytes:697734 (681.3 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90028 (87.9 KB)  TX bytes:90028 (87.9 KB)
Sometimes there is an Avahi Daemon output is listed, why?

I have to reset the router with the little button. This works but it is anoying. It works right now BTW.

I have WARdriven for two years and gave up out of guilt, I have my own connection now and setting up this router is new to me. Maybe ther is a DHCP limit that I need to set, I don't know so I am asking the best.

---

### Post by psycosmyth on 2008-08-12
Still happening.

---

### Post by linux6994 on 2008-08-12
On your WRT54G just a few questions:

1. Have you tried replacing the ethernet cable? 
2. Are you sure that the NIC card is seated securely?
3. Have you tried to reseat the card?
4. Have you tried moving the NIC card to a different slot within the PC if possible.

Even if the router were to "reset" itself often it would not change the eth designation within your pc. The problem must be either the ethernet cable or most likly the NIC card itself.

---

### Post by psycosmyth on 2008-08-12
I have found some simular posts for other distros but the fixes don't work well. It seems to be conflict with the router's firewall. My card and cable are OK. Most issues are for RPM based. This is a common router and Hardy, I don't get it. It's on eth21 now. My ISP is fiberoptic with a signal converter on the house. I don't think any conflict is there. I disabled DHCP and changed eth21 to static. Worked fine but my wireless died. 
I'm back where I started.

Hey!!Mr. 6994, you might be close, I could have the Wrong Module for my net card? built-in Nvidia? usualy sucks for everything else right? Other pc's I have used had no issue, I may try a pci card and see what happens.

---

### Post by psycosmyth on 2008-08-12
Well, I have not had much help from others but I believe in recording this type of issue on the forums in case someone else needs it.
There is a setting in the Phoenix AwardBios found in many MBs for custom MAC address setting. Just enable the default. Duh!! I am now back at ETH0!!
I think this is it, I reset the router and it is happy right now. 
Network Manager still likes to revert to roaming mode though.
:guitar:

---

