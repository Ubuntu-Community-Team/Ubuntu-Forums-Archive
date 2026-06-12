---
title: "wlan0 in feisty"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by teddybairs1 on 2007-04-09
I know this is a problem which has been hashed and rehashed, but I'm at a loss. I recently upgraded to feisty and lost my wireless. I had been using Edgy and Ndiswrapper and it worked fine. Earlier today I got it working again, and then X crashed on me, and I had to re-install and go through it all again. Now, far as I can tell, I'm doing everything the same as before, following all of the wikis and guides for ndiswrapper, but it won't bring up wlan0 and tells me the device isn't there. It did this before I had got it working earlier, but now it won't correct itself. Anyone have some ideas? yes, it's a bcm 4318.

---

### Post by dbott67 on 2007-04-09
Did you compile ndiswrapper from source or install from the repos?  If you compiled from source, you have to re-do the steps every time you upgrade the kernel.

Can you post the output of the following commands:

1. This will show which name has been assigned to your various network cards (eth0, eth1, wlan0):
```
dbott@feisty:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:ba:c0:a7:55 arp 1

```

2. This command will show all interfaces, active or not:
```
dbott@feisty:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:119030160 (113.5 MiB)  TX bytes:20186091 (19.2 MiB)
          Interrupt:17 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:94118 (91.9 KiB)  TX bytes:94118 (91.9 KiB)

```

3. This command will output the contents of your interfaces file and show whether or not they are configured to be activated on startup:
```

dbott@feisty:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

4. This command will try scanning for wireless using all network interfaces:
```
iwlist scanning
```

5. This command will show whether or not the bcmxx module is loaded (which has proven to be a problem for some and requires blacklisting in some cases).  If you've been using ndiswrapper, you should not see it:
```
lsmod | grep bcm
```

6. This command will show whether or not the ndiswrapper module is loaded:
```
lsmod | grep ndis
```

-Dave

---

### Post by teddybairs on 2007-04-09
Yeah, the default without Ndiswrapper is eth1 and it is recognized as eth1. When I blacklist bcm43xx and load ndiswrapper, eth1 completely disappears. It's supposed to be replaced by wlan0. I manually edited iftab and interfaces in order to reflect this instead of eth1 and it worked the last couple of times I used Ndiswrapper. But now, when I use ifconfig and iwconfig it won't show either eth1 or wlan0.

It's weird because I didn't do anything different the last time, and it worked after a few tries.

I might try returning it to bcm43xx and starting over again from scratch. I did get it working before, so it has to be some combination of steps I just didn't do right. I've noticed that the ndiswrapper install for 4318 seems to have to be done in a certain order or else it all falls apart.

---

### Post by spd106 on 2007-04-09
Check that you have the ndiswrapper-utils-1.8 package installed. You may also have to create a symlink.

Can you post the output of ```
ndiswrapper -v
```

---

### Post by teddybairs1 on 2007-04-09
the output says no version defined, but the ndiswrapper-utils installed is designated as 1.9

---

### Post by teddybairs1 on 2007-04-09
I took out ndiswrapper completely and restored it to bcm43xx. For some reason, the wireless works now. I'm not entirely sure what happened, or why the bcm43xx is working now, because it wasn't to begin with even with the firmware.

I'm beginning to think that feisty is living up to its name; else it should be called ornery.

---

