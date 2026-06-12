---
title: "eth devices mixed up -results in dhcp not assigning address"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by leo287 on 2007-05-07
Hi there Ubuntu users:

Few days ago had to add a ethernet pci board (realtek) because my on-board ethernet port stopped working.  Since this change the system (Feisty 7.04) is unable to assign an IP address via dhcp. In order to access the net I have to manually execute the "sudo ifconfig eth(x) IP netask etc ...).

here are the things I have discovered:

eddie@fiben:~$ dmesg | grep eth

[   35.804109] eth0: RealTek RTL8139 at 0xf0846000, 00:e0:4c:86:11:8e, IRQ 16
[   35.804113] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   36.801563] eth1: VIA Rhine II at 0x1ed00, 00:50:70:f7:0a:22, IRQ 19.
[   36.802274] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   46.881762] eth0: link down
[   61.748853] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[   89.831197] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.741291] eth2: duplicate address detected!

----> Looks like eth0 is my new realtek board and eth1 is my old one. However the eth0 is transformed to eth2 !!!! WHY ??? and then we get the "eth2: duplicate address detected!" !!!!!!!!!!!!!!!

Follows " ifconfig"  AFTER the network was launched manually:

eth0      Link encap:Ethernet  HWaddr 00:50:70:F7:0A:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0  >---- VIA eth board
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xed00 

eth2      Link encap:Ethernet  HWaddr 00:E0:4C:86:11:8E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0    >----------- manually configured
          inet6 addr: fe80::2e0:4cff:fe86:118e/64 Scope:Link             >---------------- realtek pci board
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3277546 (3.1 MiB)  TX bytes:425669 (415.6 KiB)
          Interrupt:16 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:F7:0A:22  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39838 (38.9 KiB)  TX bytes:39838 (38.9 KiB

This very strange - because eth0 has now the hardwre of the via-rhine on-board  ethernet port while during boot time eth0 is the new realtek board (see dmesg output) !!!!!!

Here is the /var/log/udev report

UEVENT[1178545369.241961] add      /class/net/eth0 (net)
ACTION=add
DEVPATH=/class/net/eth0
SUBSYSTEM=net
SEQNUM=1709
PHYSDEVPATH=/devices/pci0000:00/0000:00:0b.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=8139too
INTERFACE=eth0

UEVENT[1178545369.241981] add      /class/net/eth1 (net)
ACTION=add
DEVPATH=/class/net/eth1
SUBSYSTEM=net
SEQNUM=1710
PHYSDEVPATH=/devices/pci0000:00/0000:00:12.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=via-rhine
INTERFACE=eth1

UEVENT[1178545369.241993] add      /class/net/lo (net)
ACTION=add
DEVPATH=/class/net/lo
SUBSYSTEM=net
SEQNUM=1711
INTERFACE=lo

Any ideas what can be done here ? I am running occasionally windows XP and no problems. Hardware is well detected, network works fine once configured MANUALLY, the automated ifup + dhcp are having problems.

Thanks in advance for your help

---

### Post by dbott67 on 2007-05-07
The logical names are bound to the MAC address in the iftab.  You can edit the file and adjust the names accordingly:
```
sudo gedit /etc/iftab
```

Change the MAC address that is associated with eth0, eth1, eth2 to your preferred settings.  You'll need to edit the /etc/network/interfaces file to reflect any changes made to iftab if you've made any changes to a specific interface (such as assigning a static IP to eth2).

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1
```

-Dave

---

### Post by leo287 on 2007-05-08
> **dbott67 said:**
> The logical names are bound to the MAC address in the iftab.  You can edit the file and adjust the names accordingly:
```
sudo gedit /etc/iftab
```

Change the MAC address that is associated with eth0, eth1, eth2 to your preferred settings.  You'll need to edit the /etc/network/interfaces file to reflect any changes made to iftab if you've made any changes to a specific interface (such as assigning a static IP to eth2).

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1
```

-Dave


Hey Dave,

Thanks for your input. Things getting a bit better since ifconfig assigns the right mac addresses. However still DHCP not working, have to manually launch my network via ifconfig and route.

there is still this message in DMESG that prevents things to get better:

eddie@fiben:~$ dmesg | grep eth
[   22.472970] eth0: RealTek RTL8139 at 0xf0846000, 00:e0:4c:86:11:8e, IRQ 16
[   22.472973] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   25.667127] eth1: VIA Rhine II at 0x1ed00, 00:50:70:f7:0a:22, IRQ 19.
[   25.667836] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   33.022609] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   33.028859] eth1: link down
[   79.396796] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   79.959316] eth0: duplicate address detected!

I cannot figure out where this "duplicate address" is coming from, my etc/network interfaces is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


and ifconfig (after manually launching the network) is:

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:86:11:8E  
          inet6 addr: fe80::2e0:4cff:fe86:118e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7398 (7.2 KiB)  TX bytes:7878 (7.6 KiB)
          Interrupt:16 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:50:70:F7:0A:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xed00 

eth1:avah Link encap:Ethernet  HWaddr 00:50:70:F7:0A:22  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3780 (3.6 KiB)  TX bytes:3780 (3.6 KiB)


What is the eth1:avahi there for ??

Thanks again, we are getting closer but not there yet

Eddie

---

### Post by dbott67 on 2007-05-08
> **leo287 said:**
> ...What is the eth1:avahi there for ??

Thanks again, we are getting closer but not there yet

Eddie

Avahi is a system which facilitates service discovery on a local network.  In the event that the computer cannot find a DHCP server, avahi will automatically assign an IP address in the 169.x.y.z range.  This is useful if you're trying to connect 2 computers together via cross-over.

According to a [bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/78078") (#78078), some people have had success by re-installing avahi:

```
sudo apt-get --purge install avahi-autoipd --reinstall
```There are some other indications that it may be related to network-manager or possibly a hardware, cabling or DHCP server issue.  If re-installing avahi does not work, try the following:

1. Cable not fully connected or bad.  Try replacing it with a known-working cable.
2. Your DHCP server (in your router?) may have gotten hung-up.  Try re-booting the router or cycling the power.

Let me know.

-Dave

---

### Post by leo287 on 2007-05-08
> **dbott67 said:**
> Avahi is a system which facilitates service discovery on a local network.  In the event that the computer cannot find a DHCP server, avahi will automatically assign an IP address in the 169.x.y.z range.  This is useful if you're trying to connect 2 computers together via cross-over.

According to a [bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/78078") (#78078), some people have had success by re-installing avahi:

```
sudo apt-get --purge install avahi-autoipd --reinstall
```There are some other indications that it may be related to network-manager or possibly a hardware, cabling or DHCP server issue.  If re-installing avahi does not work, try the following:

1. Cable not fully connected or bad.  Try replacing it with a known-working cable.
2. Your DHCP server (in your router?) may have gotten hung-up.  Try re-booting the router or cycling the power.

Let me know.

-Dave

Hi

Reinstalled avahi as suggested and still "duplicate address" error is there. The router works fine under winXP so its not the router.

Thanks anyway if you have more ideas they are welcomed

---

### Post by dbott67 on 2007-05-08
> **leo287 said:**
> Hi

Reinstalled avahi as suggested and still "duplicate address" error is there. The router works fine under winXP so its not the router.

Thanks anyway if you have more ideas they are welcomed

I've got lots of ideas, but some of them are totally pointless! :)

I take it the computer is dual-boot with XP?  If so, we know the cable is good.  As for the router, it may be working, but the DHCP service component may be stalled.  FWIW, DHCP addresses are leased to computers and if XP already has assigned, it will continue to use that one (the computer just tries to "renew" the address upon bootup).

So, if the DHCP service on the router is stalled, it wouldn't necessarily prevent a computer with a previously assigned IP address from getting online --- the computer would just use the IP address it was assigned before.  If the IP address lease expires -or- the computer is requesting one for the first time, the computer would end up with one of the 169.254.x.y addresses, which is why I want to eliminate the DHCP service as an issue.  A quick re-boot or power cycle may eliminate the DHCP service as a problem.

After that, try:

1. Make sure no other LAN cables are plugged in to eth0 (the old NIC).  Also, try disabling eth0 from the command line and try option #2 below:
```
sudo ifdown eth0
```
2. Try the following commands (in order):
```
sudo ifdown eth1
```
```
sudo ifup eth1
```
```
sudo dhclient eth1
```
Post any output here.
3. Try setting a static IP for eth1 in Ubuntu.

-Dave

---

### Post by leo287 on 2007-05-08
OK I went a step further: since eth1 is the on-board ethernet port that is not functionning I disabled it on the computer BIOS so that no more eth1.

Rebooted and still "duplicate address" error persist.  On winXP all is OK.

Remains eth0 and it shows on ifconfg.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


eddie@fiben:~$ sudo ifdown eth0
Password:

There is already a pid file /var/run/dhclient.eth0.pid with pid 5433
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:e0:4c:86:11:8e
Sending on   LPF/eth0/00:e0:4c:86:11:8e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67

eddie@fiben:~$ sudo ifup eth0


There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4c:86:11:8e
Sending on   LPF/eth0/00:e0:4c:86:11:8e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: No such device
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
eddie@fiben:~

---

### Post by dbott67 on 2007-05-08
Now that you've disabled the onboard nic, can you post the output of:
```
sudo lshw -C network
``` and 
```
ifconfig -a
```

What about trying a static IP?

---

### Post by leo287 on 2007-05-08
Hi

Static works !!!!!!!!  It did not before! Still its a mistery because at startup dmesg has "duplicate address". Here are the infos



eddie@fiben:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:86:11:8e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:e100-e1ff iomemory:e8111000-e81110ff irq:16
eddie@fiben:~$ 

eddie@fiben:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:86:11:8E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe86:118e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604818 (590.6 KiB)  TX bytes:40222 (39.2 KiB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

eddie@fiben:~$ 

Thanks a lot Dave

---

