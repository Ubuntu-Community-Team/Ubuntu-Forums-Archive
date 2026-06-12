---
title: "Ubuntu &amp; Wireless?"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2007-02-12
OK so I have Ubuntu 6.10 installed on my laptop and I believe my wireless (internal) card is labeled as **eth1**. My question is when I am at home, I do NOT want to use my wireless card so I went to "System > Administration > Networking" & I make sure "enable this connection is NOT selected. However I still obtain and IP at home from my neighbors AP and I don't know how to disable this connection?

As you can see my eth1 is getting a wireless IP when Gnome is showing me the connection is NOT enabled...:confused: 

[IMG]http://img403.imageshack.us/img403/3582/eth1yf6.png[/IMG]

```
eth1      Link encap:Ethernet  HWaddr 00:16:6F:54:C2:9A  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe54:c29a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:5 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2221096 (2.1 MiB)  TX bytes:399329 (389.9 KiB)
          Interrupt:209 Base address:0xe000 Memory:dfcff000-dfcfffff 

```

---

### Post by Ren McCourtey on 2007-02-12
Hi,
it's just a workaround, but You can simply use **ifconfig eth1 down** before You solve this problem better way.

---

