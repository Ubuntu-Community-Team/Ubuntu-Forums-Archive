---
title: "Can't connect with D-Link DWA-110 Wireless USB adapter"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by peterballard on 2008-05-08
Hi all,

As the title says, I've got a D-Link DWA-110 Wireless USB adapter plugged into a USB port, but can't connect. This is a new PC with Ubuntu 8.04 installed. It is a dual boot system, and in Windows XP it works fine. 

I have installed both ndiswrapper, and the driver for this device. I followed the instructions at this sticky thread [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) ... and now "ndiswrapper -l" gives this reply:

```

dr71wu : driver installed
	device (07D1:3C07) present

```

and I added these lines to my /etc/network/interfaces file:

```

auto wlan0
iface wlan0 inet dhcp

```


But my system just doesn't seem to know there's a wireless device there.

And removing the above lines from /etc/network/interfaces (as suggested) is no help.

To try and anticipate some questions, I'll list what I've done and the results of a few commands...

"route -n" doesn't see it, just giving:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```

"ifconfig" only sees the devices "eth0" and "lo".

"lshw -C network" only sees device "eth0".

The "lsusb" command sees my adapter,but I don't know how much help this is...

```

Bus 008 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 004: ID 07d1:3c07 D-Link System 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 413c:2006 Dell Computer Corp. 
Bus 002 Device 005: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 004: ID 413c:1004 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Any advice appreciated...

---

### Post by danpos on 2008-05-08
@peterballard

Hi! This wireless device is a Ralink RT73 one and so it has native linux driver. You can set it up using the informations of this thread: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236). I've one of this and I've got success to set it up using the instructions from link that I've point you out. :)

Regards,

Danpos.

---

### Post by peterballard on 2008-05-09
> **danpos said:**
> @peterballard

Hi! This wireless device is a Ralink RT73 one and so it has native linux driver. You can set it up using the informations of this thread: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236). I've one of this and I've got success to set it up using the instructions from link that I've point you out. :)

Regards,

Danpos.

Thanks, using that download, instead of ndiswrapper, works. though I had to reboot after step 14.

---

### Post by danpos on 2008-05-09
> **peterballard said:**
> Thanks, using that download, instead of ndiswrapper, works. though I had to reboot after step 14.

I'm glad that you solved your problem. As a matter of fact, the reboot is necessary because of this wireless adapter needs that the firmware be loaded into internal bios. In my case I stopped at step 13 and then I installed [**Wicd**]("http://wicd.sourceforge.net/") in replacement to **gnome-network-manager**, I think that it manages better my network adapters.

Regards,

Danpos.

PS: Since that you've solved your issue, please mark this thread as "RESOLVED".

---

