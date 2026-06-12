---
title: "Ubuntu Server does not load motherboard NIC but does load addon card NIC"
date: 2016-10-11
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2016-10-11
For some odd reason, Ubuntu Server loads my addon card NIC (one port) but it does not load my motherboard's NIC (two ports).

This is a pretty old box so I dont think its a driver issue, its problably that since it is old, it might not load it by default.

How can I start to get help? lspci?

---

### Post by riahc3 on 2016-10-11
Tried some help around and I get this:

user@srv:~/compat-wireless-2012-05-10$ make
./scripts/gen-compat-autoconf.sh /home/user/compat-wireless-2012-05-10/.config /home/user/compat-wireless-2012-05-10/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/4.4.0-38-generic/build M=/home/user/compat-wireless-2012-05-10 modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-38-generic'
/home/user/compat-wireless-2012-05-10/config.mk:21: *** "ERROR: compat-wireless by default supports kernels >= 2.6.24, try enabling only one driver though".  Stop.
Makefile:1403: recipe for target '_module_/home/user/compat-wireless-2012-05-10' failed
make[1]: *** [_module_/home/user/compat-wireless-2012-05-10] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-38-generic'
Makefile:84: recipe for target 'modules' failed
make: *** [modules] Error 2
user@srv:~/compat-wireless-2012-05-10$

---

### Post by chili555 on 2016-10-11
> How can I start to get help? lspci?Please post:```
lspci -nnk | grep 0200 -A2
```> /home/user/compat-wireless-2012-05-10/config.mk:21: *** "ERROR: compat-wireless by default supports kernels >= 2.6.24, try enabling only one driver though". Stop.
Makefile:1403: recipe for target '_module_/home/user/compat-wireless-2012-05-10' failed
make[1]: *** [_module_/home/user/compat-wireless-2012-05-10] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-38-generic'
Makefile:84: recipe for target 'modules' failed
make: *** [modules] Error 2That's what happens when you try to graft a rusty old antique onto a shiny new 4.4.0-xx kernel. It blows up.

Without knowing the identity of the device in question, we don't know, but frankly doubt, that compat is a solution.

---

### Post by riahc3 on 2016-10-11
```
user@srv:~$ lspci -nnk | grep 0200 -A2
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
        Subsystem: Dell NetXtreme II BCM5708 Gigabit Ethernet [1028:01b1]
        Kernel driver in use: bnx2
--
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
        Subsystem: Dell NetXtreme II BCM5708 Gigabit Ethernet [1028:01b1]
        Kernel driver in use: bnx2
--
0c:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
        Kernel driver in use: xhci_hcd
0d:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express [14e4:1659] (rev 21)
        Subsystem: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express [14e4:1659]
        Kernel driver in use: tg3
user@srv:~$ ifconfig
enp13s0   Link encap:Ethernet  HWaddr 00:11:66:33:1a:bb
          inet addr:192.168.100.29  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe2f:3c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:86410 (86.4 KB)  TX bytes:25445 (25.4 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

user@srv:~$

```

---

### Post by chili555 on 2016-10-11
What does the message log tell us?```
dmesg | grep -e 05:00 -e bnx2
dmesg | grep -e 09:00 -e bnx2
```For what it's worth, the driver bnx2 is pretty rare.

Firmware???

---

### Post by riahc3 on 2016-10-11
```

user@srv:~$ dmesg | grep -e 05:00 -e bnx2
[    0.161583] pci 0000:05:00.0: [14e4:164c] type 00 class 0x020000
[    0.161630] pci 0000:05:00.0: reg 0x10: [mem 0xda000000-0xdbffffff 64bit]
[    0.161716] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    3.338378] bnx2: QLogic bnx2 Gigabit Ethernet Driver v2.2.6 (January 29, 2014)
[    4.052437] bnx2 0000:05:00.0 eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem da000000, IRQ 16, node addr 00:22:33:44:55:66
[    4.541290] bnx2 0000:09:00.0 eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem d6000000, IRQ 16, node addr 00:22:33:44:55:77
[    4.553848] bnx2 0000:05:00.0 enp5s0: renamed from eth0
[    4.568679] bnx2 0000:09:00.0 enp9s0: renamed from eth1
user@srv:~$ dmesg | grep -e 09:00 -e bnx2
[    0.134618] pci 0000:09:00.0: [14e4:164c] type 00 class 0x020000
[    0.136004] pci 0000:09:00.0: reg 0x10: [mem 0xd6000000-0xd7ffffff 64bit]
[    0.138617] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    3.338378] bnx2: QLogic bnx2 Gigabit Ethernet Driver v2.2.6 (January 29, 2014)
[    4.052437] bnx2 0000:05:00.0 eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem da000000, IRQ 16, node addr 00:22:33:44:55:66
[    4.541290] bnx2 0000:09:00.0 eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem d6000000, IRQ 16, node addr 00:22:33:44:55:77
[    4.553848] bnx2 0000:05:00.0 enp5s0: renamed from eth0
[    4.568679] bnx2 0000:09:00.0 enp9s0: renamed from eth1
user@srv:~$
```

Thats strange. I plugged in a network cable just in case before making this thread and nothing....

---

### Post by chili555 on 2016-10-11
Both devices get interface names, enp5s0 and enp9s0 respectively. So far, so good.

Since this is a server, may I assume there is no desktop environment and no Network Manager? If I am correct, then this is entirely correct and as expected:>  I plugged in a network cable just in case before making this thread and nothing....Did you declare these interfaces in /etc/network/interfaces or ... where?

---

### Post by riahc3 on 2016-10-11
> **chili555 said:**
> Both devices get interface names, enp5s0 and enp9s0 respectively. So far, so good.

Since this is a server, may I assume there is no desktop environment and no Network Manager? If I am correct, then this is entirely correct and as expected:Did you declare these interfaces in /etc/network/interfaces or ... where?

Im trying that as I speak...

A start job is running for Raise network interface


5 minutes seem to be its timeout.

Lets wait it out.

```

user@srv:~$ ifconfig -a
enp13s0   Link encap:Ethernet  HWaddr 00:11:22:33:44:55:66
          inet addr:192.168.100.29  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe2f:3c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:198922 (198.9 KB)  TX bytes:47208 (47.2 KB)
          Interrupt:16

enp5s0    Link encap:Ethernet  HWaddr 00:11:22:33:44:55:77
          inet6 addr: fe80::219:b9ff:fed8:e470/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:11500 (11.5 KB)

enp9s0    Link encap:Ethernet  HWaddr 00:11:22:33:44:55:88
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

user@srv:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

auto enp5s0
iface enp5s0 inet dhcp

auto enp9s0
iface enp9s0 inet dhcp

user@srv:~$
```

Edited the interfaces file, rebooted, got that 5 minute job stuck, and this is the end result that doesnt work.

---

### Post by chili555 on 2016-10-11
By declaring 'auto' on all three interfaces, the system is trying to get an IP address for all three, even though no cable is attached. It takes time to try, fail, try again, etc.

I suggest that you attach the cable to one only and declare it 'auto' only, something like:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

#auto enp5s0
iface enp5s0 inet dhcp

#auto enp9s0
iface enp9s0 inet dhcp
```Of course, in a server, I also suggest a static IP so you can find it to ssh, ftp, scp, etc., but that is a different question.> this is the end result that doesnt work.It doesn't? All three show up and the one with the cable gets an IP address. It works.

---

### Post by riahc3 on 2016-10-11
> **chili555 said:**
> By declaring 'auto' on all three interfaces, the system is trying to get an IP address for all three, even though no cable is attached. It takes time to try, fail, try again, etc.

I suggest that you attach the cable to one only and declare it 'auto' only, something like:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

#auto enp5s0
iface enp5s0 inet dhcp

#auto enp9s0
iface enp9s0 inet dhcp
```Of course, in a server, I also suggest a static IP so you can find it to ssh, ftp, scp, etc., but that is a different question.It doesn't? All three show up and the one with the cable gets an IP address. It works.

So only ONE auto (Im going to have only one cable connected)?

---

### Post by chili555 on 2016-10-11
> So only ONE auto (Im going to have only one cable connected)?Yes, exactly. Ideally, 'auto' the interface to which the cable is connected. It may take a couple of tries to figure it out.

You know, I suspect, that the add-on is enp13s0. However, which of the two ports on the mobo is enp5s0 may take some trial and error. Basically, if you boot and it still takes minutes to come up, you know you have the wrong one autoed. When you have the right one, it should take seconds; maybe 25 or so unless you have an SSD, in which it may take 8 seconds!

---

### Post by riahc3 on 2016-10-11
> **chili555 said:**
> Yes, exactly. Ideally, 'auto' the interface to which the cable is connected. It may take a couple of tries to figure it out.

You know, I suspect, that the add-on is enp13s0. However, which of the two ports on the mobo is enp5s0 may take some trial and error. Basically, if you boot and it still takes minutes to come up, you know you have the wrong one autoed. When you have the right one, it should take seconds; maybe 25 or so unless you have an SSD, in which it may take 8 seconds!


Yeah, just disabled all of them except the one it is, and it still gets stuck waiting.

On a side note, is there a way to lower that time from 5 minutes to less? 10 seconds?

---

### Post by chili555 on 2016-10-11
Lets' see:```
dmesg | less
```Show the big gap in the boot process. We'd like to see the 8-10 lines just before the gap(s).

Perhaps it isn't networking.

---

### Post by riahc3 on 2016-10-12
> **chili555 said:**
> Lets' see:```
dmesg | less
```Show the big gap in the boot process. We'd like to see the 8-10 lines just before the gap(s).

Perhaps it isn't networking.

Its networking. When I remove the autolines, it boots up as it should.

Ok, then my question would be the following. How do I get all the interfaces active and when I plug in a cable THEN it does a DHCP request....Not before booting the system up.

---

### Post by chili555 on 2016-10-12
> When I remove the autolines, Remove them entirely? Or comment them out as I suggested?```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

[COLOR="#FF0000"]#[/COLOR]auto enp5s0
iface enp5s0 inet dhcp

[COLOR="#FF0000"]#[/COLOR]auto enp9s0
iface enp9s0 inet dhcp
```Please notice that enp13s0 is *not* commented out. I believe that if the cable is attached to the ethernet port corresponding to the add-on ethernet device, enp13s0, we believe, the computer will boot and be connected correctly. Are you saying this is *not* the case??

Likewise, if you change the /etc/network/interfaces file to comment out enp13s0 and un-comment enp5s0 and then attach the ethernet cable to the correct port integral to the mobo, the behavior should also be correct.

I know of no way to get the system to boot normally with no active ethernet interfaces and then activate one upon plugging the cable and do so headless. We ought to and can get this working correctly. Servers all over the world, most running Linux and many running Ubuntu, do this. So can you.

---

### Post by QLee on 2016-10-12
> **chili555 said:**
> 
I know of no way to get the system to boot normally with no active ethernet interfaces and then activate one upon plugging the cable and do so headless. 

Dr Chili555,

I have a great deal of respect for your ability and energy and experience with Networking so I ask this as a question. 
Is this a case where ifplugd could be useful?

---

### Post by chili555 on 2016-10-12
> **QLee said:**
> Dr Chili555,

I have a great deal of respect for your ability and energy and experience with Networking so I ask this as a question. 
Is this a case where ifplugd could be useful?Probably. But why? To show that, with a bit of tweaking, we can overcome a solvable mis-configuration and that, to do so, we must stand by to plug in the cable on boot?

I believe that every server ought to boot and be connected without human intervention; especially when human intervention may involve a drive across town at 3:30 am to get in the server room to figure out what's gone wrong and fix it. Why not just do it right from the start?

I always welcome illustrative questions. The more I learn, over the years, the more I find I still don't know!

---

### Post by riahc3 on 2016-10-13
> **chili555 said:**
> Remove them entirely? Or comment them out as I suggested?```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

[COLOR="#FF0000"]#[/COLOR]auto enp5s0
iface enp5s0 inet dhcp

[COLOR="#FF0000"]#[/COLOR]auto enp9s0
iface enp9s0 inet dhcp
```Please notice that enp13s0 is *not* commented out. I believe that if the cable is attached to the ethernet port corresponding to the add-on ethernet device, enp13s0, we believe, the computer will boot and be connected correctly. Are you saying this is *not* the case??

Likewise, if you change the /etc/network/interfaces file to comment out enp13s0 and un-comment enp5s0 and then attach the ethernet cable to the correct port integral to the mobo, the behavior should also be correct.

I know of no way to get the system to boot normally with no active ethernet interfaces and then activate one upon plugging the cable and do so headless. We ought to and can get this working correctly. Servers all over the world, most running Linux and many running Ubuntu, do this. So can you.

OK, Im gonna try that right now...give me a sec...

---

### Post by riahc3 on 2016-10-13
```

user@srv:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp13s0
iface enp13s0 inet dhcp

# auto enp5s0
iface enp5s0 inet dhcp

# auto enp9s0
iface enp9s0 inet dhcp

user@srv:~$ ifconfig -a
enp13s0   Link encap:Ethernet  HWaddr 00:11:22:33:44:55
          inet addr:192.168.100.29  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe2f:3c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:152070 (152.0 KB)  TX bytes:23859 (23.8 KB)
          Interrupt:16

enp5s0    Link encap:Ethernet  HWaddr 55:44:33:22:11:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp9s0    Link encap:Ethernet  HWaddr 55:44:33:22:11:11
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

user@srv:~$

```

Setup the way you said. It boots instantly. I plug a cable into the other two interfaces and I do not get a IP address.

BTW, I did not confirm it before (sorry) but the addon card is indeed enp13s0

---

### Post by riahc3 on 2016-10-14
Any other ideas/solutions?

---

### Post by chili555 on 2016-10-14
> Setup the way you said. It boots instantly. As we suspected.

I suggest that you change the file to comment out enp13s0 and un-comment enp5s0:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto enp13s0
iface enp13s0 inet dhcp

auto enp5s0
iface enp5s0 inet dhcp

#auto enp9s0
iface enp9s0 inet dhcp
```Plug the cable into one of the mobo ports and reboot. If it boots instantly, you are all set. If not, switch the cable to the other mobo port and reboot. One port or the other will boot correctly and you are all set.

If you'd like to set a static IP address so that you always know where to find it to ssh, ftp, etc., post back and we'll proceed.

---

### Post by Tadaen_Sylvermane on 2016-10-15
Change auto to allow-hotplug on all but interface lo.

Auto is nothing but trouble imo, not sure why it is the default.

---

### Post by chili555 on 2016-10-15
> **Tadaen_Sylvermane said:**
> Change auto to allow-hotplug on all but interface lo.

Auto is nothing but trouble imo, not sure why it is the default.When set to 'auto', the OP reports:> Setup the way you said. It boots instantly.And it get's an IP address:> enp13s0   Link encap:Ethernet  HWaddr 00:11:22:33:44:55
          inet addr:192.168.100.29  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:fe2f:3c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:152070 (152.0 KB)  TX bytes:23859 (23.8 KB)
          Interrupt:16
How much trouble was that?

---

### Post by riahc3 on 2016-10-17
> **Tadaen_Sylvermane said:**
> Change auto to allow-hotplug on all but interface lo.

Auto is nothing but trouble imo, not sure why it is the default.


This did the trick for me :)

It gets stuck when shutting down for a while on Stopped Create Volatile Files and Directories or something like that but eventually it shuts down.

---

