---
title: "Wired Ethernet Connection Problems"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by id1337x on 2008-04-28
I have a HP pavillion a633f PC with Ubuntu 7.10 my Wired Ethernet connection doesn't work except for on windows.
I have been trying to fix this problem for a while. Here is a previous topic: (it may have additional information)

[http://ubuntuforums.org/showthread.php?t=761055]("http://ubuntuforums.org/showthread.php?t=761055")

When I click connection information I get the following:

```

[SIZE="5"]**Active Connection Information:**[/SIZE]

Interface:          Wired Ethernet (eth0)
Speed:              1000 mb/s
Driver:             r8169

IP Address:         0.0.0.0
Broadcast Address:  0.0.0.0
Subnet Mask:        0.0.0.0
Default Route:      0.0.0.0
Primary DNS:        0.0.0.0
Hardware Address:   00:1E:8C:35:9C:7B
```

sudo dhclient eth0

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:8c:35:9c:7b
Sending on   LPF/eth0/00:1c:8c:35:9c:7b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DPCPOFFERS received.
No working leases in persistent databases - sleeping.
```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-generic
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: 00:1e:0c:35:9c:7b
       width: 32 bits
       clock: 66MHZ
       capabilities: bus_master vga_palette cap_list ethernet physical
       configuration: broadcast=yes driver=8169 driverversion=2.2LK latency=255 maxlatency=255 minint=255 module=r8169 multicast=yes

```
sudo lshw -C network
```
PCI (sysfs)
```

route

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

sudo lspci | grep -i eth
```
02:00.0 Ethernet controller: Realtek Semiconducter CO., Ltd. RTL8111/81688 
PCI express Ethernet controller (rev ff)
```

ifconfig -a
```
eth0      Link encap:Ethernet   HWaddr 00:1E:8C:35:9C:7B
          inet6 addr: fe80::21e:8cff:fe35:9c7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967255 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000

eth0:avah Link encap:Ethernet   HWaddr 00:1E:8C:35:9C:7B
          inet addr: 169.254.6.173  Bcast: 169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr: 127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


```

---

### Post by chili555 on 2008-04-28
> except for on windows.This may be the key! I just read this: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/) and this: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Please let us and the future searchers  know.

---

### Post by 85fb on 2008-04-29
thats weird. I just got my wireless fixed with a tutorial on here (Vostro 1500 w/ hardy) now my eth0 isnt being recognized at all.

---

### Post by id1337x on 2008-04-30
Anyways I put in my Ubuntu 8.04 disc to see if the new Linux kernel and the newer OS wouldn't have the same problems. It still does have the same problems. I tried checking to see if the WOL is the problem and it isn't first of all it is enabled already in the device manager and when I unplug power it doesn't help.

It does seem though that things are much different if I just booted  up straight from Ubuntu rather then a restart from Windows or something. When I boot up straight from Ubuntu it doesn't recognize the same stuff. (it doesn't even show the connection information. It doesn't recognize the same stuff.)

Now:

```

ping 128.1.65.255
network is unreachable
```

Before:

```
ping 128.1.65.255
pinging 128.1.65.255...
host is unreachable
```

I think I'm pretty sure now that the problem is in the following link: (I will test it as soon as possible).

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

---

### Post by id1337x on 2008-05-02
Well interestingly when I boot up without my NIC connected I pretty much get all the same results as above!

[SIZE="4"]It still doesn't work[/SIZE] :confused:

**Wake on LAN:**

On windows I tried "Wake-on-LAN Disabled" and I still got all the same results, the same ifconfig and the same otherwise. I normally have "Wake-on-LAN Enabled" anyways and I still get the same results. The setting seems to me to be irrelevant.

[IMG]http://img177.imageshack.us/img177/4122/nwproblemxj6.jpg[/IMG]

Ya that is how it is normally anyways. Sometimes I get even further **limited network access**. The only reason I've observed is that I powered down for a while before booting Ubuntu rather then just doing a restart from Windows. I noticed that the ifconfig when I am in this limited state has only a few differences. Eth0 in ifconfig is "UP BROADCAST MULTICAST" rather then "UP BROADCAST RUNNING MULTICAST" also it doesn't display etho:avah.

**The bugs:**

Well it's quite simple. When I do rmmod it doesn't allow me to successfully unload the module so this solution doesn't seem to work.

---

### Post by chili555 on 2008-05-02
Grasping at straws a bit here...some computer BIOS have a setting to enable or disable Wake on LAN and, a few, other Wake ons. Does yours? Are all of them enabled?

Did you try:```
sudo rmmod -f 8139too
```

---

### Post by id1337x on 2008-05-04
*Grasping at straws a bit here...some computer BIOS have a setting to enable or disable Wake on LAN and, a few, other Wake ons. Does yours? Are all of them enabled?*

I checked the BIOS I'm pretty sure this is not the case. Anyways I will check out the BIOS more if nothing else works.

When you said **sudo rmmod -f 8139too** I think you ment **r8169 **:razz:

dmesg | grep 'Ethernet'

```
[  27.639221] r8169 Gigabit Ethernet driver 2.2lk loaded
```

sudo rmmod -f r8169
This works it says 'no network devices have been found' and ifconfig doesn't even show eth0 or eth0:avah. Reloading the module doesn't seem to work for some mysterious reasons :confused:

modprobe -v r8169

```
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/net/r8169.ko
FATAL: Error inserting r8169 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/r8169.ko): Operation not permitted.
```

sudo modprobe -v r8169

```
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/net/r8169.ko

```

Ok so if I do sudo on them it seems to let me do it its just that the modprobe doesn't even change anything for some reason.

---

### Post by chili555 on 2008-05-04
> I think you ment r8169I did indeed. Sorry about the error.> modprobe doesn't even change anything for some reason.It certainly removes and inserts the module, it's just that it doesn't get your interface going. 

I saw this: [http://ubuntuforums.org/showthread.php?t=538448&page=4](http://ubuntuforums.org/showthread.php?t=538448&page=4) and was interested in this, specifically:> unticked the box for "Let windows power down this device" in the device manager network card section of windows and now my connection is back upWould you please check on this?

I am running out of ideas. You could always scrub Windows.

---

### Post by id1337x on 2008-05-04
```
unticked the box for "Let windows power down this device" in the device manager network card section of windows and now my connection is back up
```

[SIZE="7"]WOOT[/SIZE] It works :lolflag: 

:)

---

### Post by chili555 on 2008-05-04
Fabulous! Glad it's going well.

---

