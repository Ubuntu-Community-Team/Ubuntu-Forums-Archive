---
title: "Trouble Connecting With Wireless"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by p4rk3r on 2007-08-20
I am having problems connecting to my wireless router. My router is a D-Link which is Linux compatible (I base this off of the penguin logo and its instruction to find the user manual with Linux). My wireless card is a HWPG1 hawking technologies. I think the wireless card is the problem. I went to their website for tech support [http://www.hawkingtech.com/support/d...=33&ProdID=290](http://www.hawkingtech.com/support/d...=33&ProdID=290) and it shows that there are no available drivers for Linux, but I am able to connect and get signal from my router, it just will not connect to the internet. Is there nothing I can do?

---

### Post by jakev383 on 2007-08-20
If it connects and gets a signal from your router, open a terminal and paste this info in.  Show us the output, please:
```

ifconfig
route

```

---

### Post by p4rk3r on 2007-08-20
eth0      Link encap:Ethernet  HWaddr 00:11:2F:81:93:64  
          inet6 addr: fe80::211:2fff:fe81:9364/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118699159 (113.2 MiB)  TX bytes:6000800 (5.7 MiB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra1       Link encap:Ethernet  HWaddr 00:0E:3B:07:CD:E4  
          inet6 addr: fe80::20e:3bff:fe07:cde4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:125116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2720 errors:25 dropped:25 overruns:0 carrier:0
          collisions:375 txqueuelen:1000 
          RX bytes:12255927 (11.6 MiB)  TX bytes:32112 (31.3 KiB)
          Interrupt:20 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by jakev383 on 2007-08-20
Okay, you're not actually getting an IP address, and I don't think your wireless card is showing up either.  Try installing ndiswrapper and see if you can get some Windows drivers to work.

---

### Post by p4rk3r on 2007-08-21
i downloaded the 3 ndiswrappers that appeared under my synaptic package manager but I'm not sure how to use any of them or how the program works.  Could you explain how i can attempt to turn on my windows drivers please?

---

### Post by jakev383 on 2007-08-22
Actually it does seem your card was recognized (didn't realize the ra1 was valid). It just wasn't getting an IP address.
Anyway, if you still have the ra1 device showing, try:
```
 sudo dhclient ra1 
``` and see if you can establish an IP address. 
You may also try ```
 sudo iwlist scan 
``` and see if it shows anything.
If you need to go the ndiswrapper route, this how-to may help - just remember to adjust it for your drivers: [http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper)

---

### Post by tyggna1 on 2007-08-22
I had  a similar problem with my wireless.  Here's three links that might be helpful:


This first one is just for the terminal commands, if you're already somewhat proficient.  All you need to do is figure out the name of the linux driver, and then you can use the commands to install it.

[http://ubuntuforums.org/showthread.php?t=527641]("http://ubuntuforums.org/showthread.php?t=527641")

This one is similar, but more helpful than the first as it's more verbose--it'll take longer to read, but you'll learn more about wireless troubleshooting in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=446010]("http://ubuntuforums.org/showthread.php?t=446010")

This last one is actually associated with a utility that is used for cracking wireless networks.  While that utility itself doesn't have many meritable uses, it gives a list of cards that work with it, and what driver they're based off of.  If you need to do in-depth research, it'd be a good place to go.

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=7c6009f5fab3bc9f37f7e4518c0095e2]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=7c6009f5fab3bc9f37f7e4518c0095e2")

I hope that these are helpful.

---

### Post by p4rk3r on 2007-08-22
thank you all for your help, still no luck. here is what i got when i checked ra1:

Listening on LPF/ra1/00:0e:3b:07:cd:e4
Sending on   LPF/ra1/00:0e:3b:07:cd:e4
Sending on   Socket/fallback
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ra1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.104 -- renewal in 4892 seconds.

---

### Post by p4rk3r on 2007-08-22
Also, I'd really like to try ndiswrapper to see if windows drivers might allow it to work.  But I have no idea, and can't find anything on how to use ndiswrapper in order to do that.

---

### Post by kevdog on 2007-08-22
Can you post 
lspci -nn
lshw -C network

Are you sure your card has a ra chipset???  It it does, I would recommend something else other than the ndiswrapper approach -- ie serial monkey drivers.  The output above will help us determine your chipset and then allow us to proceed on a proper course of action.

---

### Post by jakev383 on 2007-08-23
> **p4rk3r said:**
> thank you all for your help, still no luck. here is what i got when i checked ra1:

Listening on LPF/ra1/00:0e:3b:07:cd:e4
Sending on   LPF/ra1/00:0e:3b:07:cd:e4
Sending on   Socket/fallback
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ra1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.104 -- renewal in 4892 seconds.

According to that it leased IP address 192.168.0.104.  That should have allowed you to ping stuff and see that ra1 had an IP when you ran "ifconfig".

---

