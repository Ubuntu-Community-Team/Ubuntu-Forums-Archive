---
title: "WUSB54GSv2 present but..."
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Dimension7 on 2007-04-21
After carefully following the instructions at the [ [COLOR="Blue"]HOWTO: WUSB54GS v1 (only?) on (X)(K?)Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs"),

My driver & device were installed and present respectively, but I still don't have the wlan0.  Any advice on what to do next? 

Here's what I have so far...
```

# lsusb
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 002:  13b1:0014 Linksys
Bus 001 Device 001:  ID 0000:0000

# ndiswrapper -l
wusb54gsv2 : driver installed
     Device (13B1:0014) present

# iwconfig
lo	no wireless extensions.
eth0	no wireless extensions.

# ifconfig
eth0	Link encap:Ethernet  HWaddr 00:50:70:26:06:82
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
	Interrupt:10 Base address:0x6000

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:26:06:85
	inet addr:169.254.4.84  Bcast:169.254.255.255  Mask:255.255.0.0
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	Interrupt:10 Base address:0x6000

lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
	TX packets:1498 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:120004 (117.1 KiB)  TX bytes:120004 (117.1 KiB)	

```

---

### Post by medley on 2007-04-22
> **Dimension7 said:**
> After carefully following the instructions at the [ [COLOR="Blue"]HOWTO: WUSB54GS v1 (only?) on (X)(K?)Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs"),

My driver & device were installed and present respectively, but I still don't have the wlan0.  Any advice on what to do next? 

Here's what I have so far...
```

# lsusb
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 002:  13b1:0014 Linksys
Bus 001 Device 001:  ID 0000:0000

# ndiswrapper -l
wusb54gsv2 : driver installed
     Device (13B1:0014) present

# iwconfig
lo	no wireless extensions.
eth0	no wireless extensions.

# ifconfig
eth0	Link encap:Ethernet  HWaddr 00:50:70:26:06:82
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
	Interrupt:10 Base address:0x6000

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:26:06:85
	inet addr:169.254.4.84  Bcast:169.254.255.255  Mask:255.255.0.0
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	Interrupt:10 Base address:0x6000

lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
	TX packets:1498 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:120004 (117.1 KiB)  TX bytes:120004 (117.1 KiB)	

```

I wrestled with the WUSB54GSv2 for a couple weeks, but finally got it working consistently last night. I also used the howto you did. To be perfectly honest, I'm not sure which of the multiple things I tried finally got it working, but I'll tell you what I did:

1. I downloaded the latest ndiswrapper from sourceforge and compiled it. (I suspect this was probably the thing that made the difference)
2. I physically removed the other n/w adapters that were in the machine (one pci/wired, the other pci/wireless)
3. I upgraded the network utilities that showed 'upgradeable' in adept

You'll know you're on the right track when you see your adapter's power light come on during the boot up sequence. If you see the link light flashing during this also, you're golden.

I would suggest downloading ndiswrapper from sourceforge and compiling it. It's not difficult; just watch for any errors during compile. You should see none. Also, be aware that the howto is a year old, and the link that takes you to Linksys' download site for the driver gives you a newer file than he worked with, and the drivers have slightly different names. Just pay attention to detail and you'll be OK. Apart from these caveats, his howto is better than all the others I've tried.

Good luck.

---

### Post by Dimension7 on 2007-04-26
Got tired researching and conguring how to make this USB adapter work, so I bought a Netgear WPN311 PCI wireless adapter.  It worked out-of-the-box like magic!  

I have more time now exploring what Ubuntu can offer.  So far I'm happy with this distro and might say goodbye to WinXP soon.

---

