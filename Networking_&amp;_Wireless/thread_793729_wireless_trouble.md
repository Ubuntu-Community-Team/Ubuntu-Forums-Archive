---
title: "wireless trouble"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by SCHWARTZMC on 2008-05-14
i am a noob

running feisty

i wish i knew what i was doing

i started having trouble with my wi-fi earlier this winter. i would open mozilla and simply get 'cannot find server'. i managed to find out that if i entered the command below, i could get back on the internet.

sudo /etc/init.d/networking restart

at first it seemed that i would only have to do this after restarting the whole computer. but then it just happen...whenever it felt like it. i did receive some help from someone more experienced, but we were unable to find a solution. he recommend i give the following command:

matt@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:F7:2C:2C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:DF:86:84  
          inet addr:192.168.100.90  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fedf:8684/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1364 errors:0 dropped:40089 overruns:0 frame:0
          TX packets:1079 errors:0 dropped:0 overruns:0 carrier:60
          collisions:0 txqueuelen:1000 
          RX bytes:308590515 (294.2 MiB)  TX bytes:33240090 (31.7 MiB)
          Interrupt:17 Base address:0x8000 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:F7:2C:2C  
          inet addr:169.254.4.212  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1995755 (1.9 MiB)  TX bytes:1995755 (1.9 MiB)
__

and the contents of '/etc/network/interfaces' 


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp





iface eth1 inet dhcp
wireless-essid StructuredMesh





auto eth1

auto eth0

__

i have now started using it on a new wireless network and am experiencing a new twist. to get it working i have to flip a switch (possibly connected to the wi-fi brains) on the laptop from what i am guessing a 'on' position to an 'off' position. then switch it past 'on' to 'start' where it will spring back to 'on' (kind of like starting a car). i then have to enter the network restart command listed above...and POW! i'm back online.

i hope it is helpful. if there is a way to avoid this process, i would love to know. any help from anybody else would be greatly appreciated.

---

### Post by SCHWARTZMC on 2008-05-14
sorry about the simlie above. i tried to remove it, but as i said...i don't really know what i'm doing.

---

