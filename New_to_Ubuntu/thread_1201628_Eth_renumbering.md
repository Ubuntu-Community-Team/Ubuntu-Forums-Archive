---
title: "Eth renumbering"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by gurt on 2009-07-01
How can I change eth11 to eth6?

```
gurt@mingus:~$ ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8c:d6:e0  
eth1      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2c  
eth2      Link encap:Ethernet  HWaddr 00:02:b3:28:50:7f  
eth3      Link encap:Ethernet  HWaddr 00:02:b3:28:50:80  
eth4      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6a  
eth5      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6b  
eth11     Link encap:Ethernet  HWaddr 00:02:b3:28:52:2d
```

tanks!

---

### Post by colau on 2009-07-01
> **gurt said:**
> How can I change eth11 to eth6?

```
gurt@mingus:~$ ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8c:d6:e0  
eth1      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2c  
eth2      Link encap:Ethernet  HWaddr 00:02:b3:28:50:7f  
eth3      Link encap:Ethernet  HWaddr 00:02:b3:28:50:80  
eth4      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6a  
eth5      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6b  
eth11     Link encap:Ethernet  HWaddr 00:02:b3:28:52:2d
```

tanks!
```

cd /etc/udev/rules.d/
sudo cp 70-persistent-net.rules 70-persistent-net.rules.bak
sudo gedit /70-persistent-net.rules &

```
Edit and reboot.

---

### Post by gurt on 2009-07-01
Cool beans! Thanks colau!

Follow-on q:

If I remove all the entries in there, does that force ubuntu to reinstall/reinitialize my nics?

I have a bunch of entries for USB NICs in there I'm trying to get working.

Ta!

---

### Post by NTolerance on 2009-07-01
> **gurt said:**
> Cool beans! Thanks colau!

Follow-on q:

If I remove all the entries in there, does that force ubuntu to reinstall/reinitialize my nics?

I have a bunch of entries for USB NICs in there I'm trying to get working.

Ta!

In my experience all NICs will be re-numbered, probably depending on what order they're connected to the bus.  I don't necessarily think the drivers get changed or re-installed, but I'm not 100% sure.  I did a bit of work with editing this udev file when I moved a partition from one system with its own unique NICs to another system which had different NICs.

---

### Post by colau on 2009-07-01
> **gurt said:**
> Cool beans! Thanks colau!

Follow-on q:

If I remove all the entries in there, does that force ubuntu to reinstall/reinitialize my nics?

I have a bunch of entries for USB NICs in there I'm trying to get working.

Ta!
How many nics you have?

---

### Post by gurt on 2009-07-01
I have a total of 13 interfaces.
1 on board
3 dual port NICs (6 ports)
6 davicom dm9601 USB NICs

I trying to get the USB NICs working but it not going well. This is a lab for dynamips/dynagen. There are posts from people that can get it working but I seem to be missing something.

Thanks!

---

### Post by gurt on 2009-07-01
It's an odd thing. At first I tried to add 3 USB NICs to one of the USB ports (via a dongle). Only one showed up under ifconfig and of course is was in 70-persistent-net-generator.rules too.

Then I shutdown and add another dongle to a different USB port, again with 3 USB NICs. All three show up in ifconfig, but the one I had before is gone. Note eth7 is missing!

```

gurt@mingus:~$ ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8c:d6:e0  
eth1      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2c  
eth2      Link encap:Ethernet  HWaddr 00:02:b3:28:50:7f  
eth3      Link encap:Ethernet  HWaddr 00:02:b3:28:50:80  
eth4      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6a  
eth5      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6b  
eth6      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2d  
eth8      Link encap:Ethernet  HWaddr 00:60:6e:35:8e:a2  
eth9      Link encap:Ethernet  HWaddr 00:60:6e:35:ce:a3  
eth10     Link encap:Ethernet  HWaddr 00:60:6e:92:4a:f4  
```

All the eths (0-10) are shown in 70-persistent-net-generator.rules

I sure I wish I knew what I was doing.
](*,)
I'm going to keep trying different cominations of NICs on dongles and keep editting the 70-persistent-net-generator.rules.
Is there something else I need to be doing to make sure I don't hose something up in the process?

Ta!

---

### Post by colau on 2009-07-01
Is there any backup file named *70-persistent-net.rules.bak*?

---

### Post by gurt on 2009-07-01
I don't see one.

```
gurt@mingus:/etc/udev/rules.d$ ls -l
total 16
-rw-r--r-- 1 root root  773 2009-07-01 15:10 70-persistent-cd.rules
-rw-r--r-- 1 root root 2328 2009-07-02 06:58 70-persistent-net.rules
-rw-r--r-- 1 root root 2487 2009-07-01 20:05 70-persistent-net.rules~
-rw-r--r-- 1 root root 1398 2009-04-09 08:33 README
```

Is 70-persistent-net.rules~ ba backup? What's that ~ for anyway?

---

### Post by colau on 2009-07-01
> **gurt said:**
> I don't see one.

```
gurt@mingus:/etc/udev/rules.d$ ls -l
total 16
-rw-r--r-- 1 root root  773 2009-07-01 15:10 70-persistent-cd.rules
-rw-r--r-- 1 root root 2328 2009-07-02 06:58 70-persistent-net.rules
-rw-r--r-- 1 root root 2487 2009-07-01 20:05 70-persistent-net.rules~
-rw-r--r-- 1 root root 1398 2009-04-09 08:33 README
```

Is 70-persistent-net.rules~ ba backup? What's that ~ for anyway?
Open that file with gedit.

---

### Post by mellowd on 2011-01-29
Sorry to bring a thread back from the dead, but I'm having the same issue here. 

I have Ubuntu 10.10 installed for my dynamips box. Inside I have 2 Quad NIC's and 4 Pluscom dm9601 USB NIC's.

This is during bootup:
```
darreno@CCIE:~$ dmesg | grep Ethernet
[    1.311502] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.366397] eth1-4: Quattro HME (PCI/CheerIO) 10/100baseT Ethernet DEC 21153 PCI Bridge
[    1.366400] eth1: Quattro HME slot 0 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:8d:49:18
[    1.371669] eth2: Quattro HME slot 1 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:8d:49:19
[    1.375867] eth3: Quattro HME slot 2 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:8d:49:1a
[    1.379775] eth4: Quattro HME slot 3 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:8d:49:1b
[    1.383794] eth5-8: Quattro HME (PCI/CheerIO) 10/100baseT Ethernet DEC 21153 PCI Bridge
[    1.383797] eth5: Quattro HME slot 0 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:b4:37:94
[    1.387607] eth6: Quattro HME slot 1 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:b4:37:95
[    1.391477] eth7: Quattro HME slot 2 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:b4:37:96
[    1.395375] eth8: Quattro HME slot 3 (PCI/CheerIO) 10/100baseT Ethernet 08:00:20:b4:37:97
[    5.976925] dm9601 4-1:1.0: eth9: register 'dm9601' at usb-0000:00:12.1-1, Davicom DM9601 USB Ethernet, 00:10:13:50:a3:43
[    6.033132] dm9601 4-3:1.0: eth10: register 'dm9601' at usb-0000:00:12.1-3, Davicom DM9601 USB Ethernet, 00:10:13:50:a3:43
[    6.088717] dm9601 6-1:1.0: eth11: register 'dm9601' at usb-0000:00:13.1-1, Davicom DM9601 USB Ethernet, 00:10:13:50:a3:43
[    6.144768] dm9601 6-2:1.0: eth12: register 'dm9601' at usb-0000:00:13.1-2, Davicom DM9601 USB Ethernet, 00:10:13:50:a3:43
```


This is what's actually there now:
```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:21:de:ed:1e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:8d:49:18", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:8d:49:19", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:b4:37:94", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth5"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:8d:49:1b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:b4:37:95", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth6"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:b4:37:97", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth8"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:b4:37:96", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth7"

# USB device 0x0fe6:0x8101 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:10:13:50:a3:43", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth9"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:8d:49:1a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:af:1a:ce:0b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

Basically, Ubuntu sees the NIC's on startup, but you then can't use them. I've got them all configer in /et/network/interfaces like so:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Sun Quad NICs
iface eth1 inet manual
#
iface eth2 inet manual
#
iface eth3 inet manual
#
iface eth4 inet manual
#
iface eth5 inet manual
#
iface eth6 inet manual
#
iface eth7 inet manual
#
iface eth8 inet manual

# USB NICs
#
iface eth9 inet manual
#
iface eth10 inet manual
#
iface eth11 inet manual
#
iface eth12 inet manual
```

But:
```
darreno@CCIE:~$ sudo ifconfig eth9 up
darreno@CCIE:~$ sudo ifconfig eth10 up
eth10: ERROR while getting interface flags: No such device
```



gurt, did you get this working?

---

