---
title: "MAC address changes every reboot"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2007-09-24
I just installed Feisty on a new PC (asus p5k mainboard with onboard NIC)
Every time I reboot the box, the MAC address is different.  I am assuming Ubuntu is doing something flaky because I have built two identical PC's running XP and the MAC is stable.  Same mainboard, same bios, same bios settings.  The NIC is listed as an Attansic Technology L1 GigE adapter.

How do I tell Ubuntu to only use the rom hardcoded MAC?

-J

---

### Post by noob12 on 2007-09-24
It should use the real ones unless you're running something to change them.  Maybe you have multiple nics and they aren't mapped in /etc/iftab?  Are you getting alternation between two?

Can you post the output of these?
```

lspci -nn

lsusb

sudo lshw -C network

ifconfig -a

cat /etc/iftab

```

---

### Post by miatawnt2b on 2007-09-24
I've edited out the IP's and such.  The interface does work, it's just the MAC that's screwed. The MAC listed here is not the manufacturer hardware MAC.
Thanks for the help,
-J

```
/var/log$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:2940] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation Unknown device [8086:2948] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation Unknown device [8086:294a] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2918] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation Unknown device [8086:2921] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation Unknown device [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0422] (rev a1)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
05:02.0 PCI bridge [0604]: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) [3388:0021] (rev 11)
05:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)
06:08.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
06:08.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
06:09.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
06:09.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
06:0a.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
06:0a.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
06:0b.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
06:0b.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)

```
```
/var/log$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```
```
/var/log$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: b0
       serial: ee:76:f8:df:5e:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.6 duplex=full firmware=N/A ip=[edited]x.x.160.249 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fe9c0000-fe9fffff irq:17

```
```
 ifconfig -a
eth1      Link encap:Ethernet  HWaddr EE:76:F8:DF:5E:7A  
          inet addr:[edited]x.x.160.249  Bcast:[edited]x.x.160.255  Mask:255.255.255.0
          inet6 addr: [edited]xxxx:xxxx:xxxx:xxdf:5e7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2010393 (1.9 MiB)  TX bytes:246606 (240.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```
```
:/var/log$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 0e:e6:e2:35:fd:5e arp 1

```

---

### Post by noob12 on 2007-09-24
What is the actual mac address ?

---

### Post by noob12 on 2007-09-24
You may be getting affected by this [http://lkml.org/lkml/2007/2/14/320](http://lkml.org/lkml/2007/2/14/320) .   I'm still trying to determine when this fix got into the kernel.  What kernel version are you running (can you post **uname -a**).

---

### Post by miatawnt2b on 2007-09-24
> **noob12 said:**
> What is the actual mac address ?

That's a very good question, I pulled the cover to look at the board and there is no sticker on it listing the hardware MAC. It maybe on the bottom (I have a spare that I am going to look at) So... short of installing XP on the drive I have no idea how to tell.

-J

---

### Post by wieman01 on 2007-09-24
So every time you reboot...
> ifconfig
...displays a MAC address different than the previous one?

In general this is how you change/clone MAC addresses (for reference):
> sudo ifconfig eth1 down hw ether 00:00:00:00:00:01
sudo ifconfig eth1 up
Replace "eth1" with your wireless interface and "00:00:00:00:00:01" with the target MAC address.

---

### Post by miatawnt2b on 2007-09-24
> **wieman01 said:**
> So every time you reboot...

...displays a MAC address different than the previous one?

Yep... strange huh?

> **wieman01 said:**
> 
In general this is how you change/clone MAC addresses (for reference):

Replace "eth1" with your wireless interface and "00:00:00:00:00:01" with the target MAC address.
I was going to try this as a down and dirty approach... assuming it works, what file do I edit to make this happen at boot?

Thanks
-J

---

### Post by noob12 on 2007-09-24
You should be able to do it in **/etc/network/interfaces** using an **hwaddress** line in the stanza for that interface.  e.g.

```

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:00:00:00:00:01

```

replacing with desired mac.  See **man interfaces** for details.

Also, if you clear out your iftab, it will probably start appearing at eth0.  Otherwise the mismatch will always cause it to bump to eth1.

---

### Post by noob12 on 2007-09-24
Also, further research determines the bug is fixed in version 2.0.7 of the atl1 driver.  [http://sourceforge.net/forum/forum.php?forum_id=666235](http://sourceforge.net/forum/forum.php?forum_id=666235)

It looks like the fix is in the 2.6.22 kernel in Gutsy.   You could probably build from sources yourself.  Cheers.

---

### Post by miatawnt2b on 2007-09-24
> **noob12 said:**
> Also, further research determines the bug is fixed in version 2.0.7 of the atl1 driver.  [http://sourceforge.net/forum/forum.php?forum_id=666235](http://sourceforge.net/forum/forum.php?forum_id=666235)

It looks like the fix is in the 2.6.22 kernel in Gutsy.   You could probably build from sources yourself.  Cheers.

Thanks a bunch... the 2.07 driver did the trick.
-J

---

