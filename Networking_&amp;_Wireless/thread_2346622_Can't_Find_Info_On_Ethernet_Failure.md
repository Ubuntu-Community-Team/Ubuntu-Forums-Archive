---
title: "Can't Find Info On Ethernet Failure"
date: 2016-12-16
forum: Networking &amp; Wireless
---

### Post by terrigat on 2016-12-16
I have a known good NIC plugged into a known good PCI slot with a known good cat 5e patch cable plugged into a known good switch port.

The mobo NIC initially only ran at 10mbit [1mb/s] speeds until I powered down and inserted a different NIC. Since reboot(s), I have not gotten internet access again (mobo or otherwise). The light on the switch / NIC only lights up before Ubuntu tries to init the network.

Using 14.04 TLS Ubuntu.

This server has been in operation for 7 years. Ubuntu has been reinstalled maybe three times total. I haven't done more than update to 14.04 TLS on the current install. Outside of some ZFS not being the main branch messages I have not noticed any real errors until now.

Dmesg
```

...
[    1.693346] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.693480] r8169 0000:04:06.0 (unregistered net_device): not PCI Express
[    1.693779] r8169 0000:04:06.0 eth0: RTL8169sb/8110sb at 0xffffc90000c76000, 00:e0:4c:77:d8:0f, XID 10000000 IRQ 20
[    1.693782] r8169 0000:04:06.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
...
[   11.826698] systemd-udevd[1744]: renamed network interface eth0 to eth1
[   11.827993] hda_intel: position_fix set to 1 for device 1458:a022
[   11.833085] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   11.837963] type=1400 audit(1481048250.690:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1801 comm="apparmor_parser"
[   11.837973] type=1400 audit(1481048250.690:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1801 comm="apparmor_parser"
[   11.837978] type=1400 audit(1481048250.690:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1801 comm="apparmor_parser"
[   11.838596] type=1400 audit(1481048250.690:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1801 comm="apparmor_parser"
[   11.838603] type=1400 audit(1481048250.690:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1801 comm="apparmor_parser"
[   11.838935] type=1400 audit(1481048250.690:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1801 comm="apparmor_parser"
[   11.844210] type=1400 audit(1481048250.694:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=1806 comm="apparmor_parser"
...
[   18.519337] r8169 0000:04:06.0 eth1: link down
[   18.519397] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.530534] type=1400 audit(1481048257.378:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=2339 comm="apparmor_parser"
[   18.535098] type=1400 audit(1481048257.386:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=2337 comm="apparmor_parser"
[   18.535110] type=1400 audit(1481048257.386:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=2337 comm="apparmor_parser"
[   18.535498] type=1400 audit(1481048257.386:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=2337 comm="apparmor_parser"
[   18.540720] type=1400 audit(1481048257.390:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=2342 comm="apparmor_parser"
[   18.540949] type=1400 audit(1481048257.390:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2338 comm="apparmor_parser"
[   18.540963] type=1400 audit(1481048257.390:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2338 comm="apparmor_parser"
[   18.540970] type=1400 audit(1481048257.390:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2338 comm="apparmor_parser"
[   18.541604] type=1400 audit(1481048257.390:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2338 comm="apparmor_parser"
[   18.541610] type=1400 audit(1481048257.390:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2338 comm="apparmor_parser"
...
[  283.423477] r8169 0000:04:06.0 eth1: link down
[  283.423519] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1236.002848] r8169 0000:04:06.0 eth1: link down
[ 1236.002890] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
...

```

hosts
```

127.0.0.1    localhost
127.0.1.1    windham-GA-MA770-UD3

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:77:d8:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52812 (52.8 KB)  TX bytes:52812 (52.8 KB)

```

/etc/networks/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

lshw -c network
```

  *-network
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: eth1
       version: 10
       serial: 00:e0:4c:77:d8:0f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:be00(size=256) memory:fdcff000-fdcff0ff memory:fdb00000-fdb1ffff

```

lsmod
```

r8169                  71677  0 

```

lspci
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (PCI express gpp port B)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

nm-tool
```

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:77:D8:0F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

netstat
```

Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth1       1500 0         0      0      0 0             0      0      0      0 BMU
lo        65536 0       764      0      0 0           764      0      0      0 LRU

```

70-persistent-net.rules
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:d0:d9:5e:6a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:77:d8:0f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```
Tried deleting and running
/sbin/udevadm trigger --type=devices --action=add

resolv.conf
-EMPTY-

arp -a and route are empty

After I gathered this, I tried using modprobe and the latest RealTek drivers from the official website.
First modprobe -vfs r8169 | modprobe -v r8168 (back in the day there was a problem with r8169 that sounded alot like my problem, so tried this)
Then installed newest r8169 drivers

ifup / down
ifconfig interface up / down
NetworkManager.conf: managed = true / false
/etc/networks/interfaces: filled in and empty

---

### Post by terrigat on 2016-12-20
So. Is there a way to manually enable dhcp long enough to update?

In its current form adding routes does not help. Disabling Network Manager does not seem to allow configuration thru ifup/down and /etc/networks/interfaces.

I really don't know how I should try to activate the NIC even temporarily. At least without trashing the current install.

---

