---
title: "NIC Bonding"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by resin2 on 2017-07-26
I'm still new to the Linux world but the reason why I have built my PC is to learn it - so please bear this in mind as I may be doing something obvious wrong. 

A brief outline of my setup so you can understand what I am trying to achieve: I have a custom built PC where I have installed Ubuntu Server to host various virtual machines. The virtual machines HDDs are located on my NAS which I connect via ISCSI and I wish to bond two ports together to improve the speed. At the moment I have a 4 port PCI-E card, two ports I wish to bond for ISCSI directly into my NAS, one shall remain unplugged and one will be for my general connectivity. [SIZE=2]*As a side note, my motherboard's NIC ([COLOR=#000000][I]enp30s0) *[/COLOR]is useless it crashes after a few seconds when VNC is active so I'd set random IP details so it doesn't interfere as I don't know how to permanently disable it (it shows as unmanaged in the control panel).[/I][/SIZE]

I tried following this tutorial: [https://www.unixmen.com/linux-basics-create-network-bonding-on-ubuntu-14-10/](https://www.unixmen.com/linux-basics-create-network-bonding-on-ubuntu-14-10/) as well as [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) but have come across the following errors:

```
admin@VMPC:~$ journalctl -xe
-- Unit ssh.service has begun reloading its configuration
Jul 26 18:11:02 VMPC sshd[1629]: Received SIGHUP; restarting.
Jul 26 18:11:02 VMPC systemd[1]: Reloaded OpenBSD Secure Shell server.
-- Subject: Unit ssh.service has finished reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit ssh.service has finished reloading its configuration
-- 
-- The result is done.
Jul 26 18:11:02 VMPC sshd[1629]: Server listening on 0.0.0.0 port 22.
Jul 26 18:11:02 VMPC sshd[1629]: Server listening on :: port 22.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Main process exited, code=e
Jul 26 18:11:02 VMPC systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has failed.
-- 
-- The result is failed.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Unit entered failed state.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Failed with result 'exit-co
lines 2433-2455/2455 (END)
-- Unit ssh.service has begun reloading its configuration
Jul 26 18:11:02 VMPC sshd[1629]: Received SIGHUP; restarting.
Jul 26 18:11:02 VMPC systemd[1]: Reloaded OpenBSD Secure Shell server.
-- Subject: Unit ssh.service has finished reloading its configuration
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit ssh.service has finished reloading its configuration
-- 
-- The result is done.
Jul 26 18:11:02 VMPC sshd[1629]: Server listening on 0.0.0.0 port 22.
Jul 26 18:11:02 VMPC sshd[1629]: Server listening on :: port 22.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jul 26 18:11:02 VMPC systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit networking.service has failed.
-- 
-- The result is failed.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Unit entered failed state.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Failed with result 'exit-code'.

```

```
admin@VMPC:~$ systemctl status networking.service
&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Wed 2017-07-26 18:11:02 BST; 2min 55s ago
     Docs: man:interfaces(5)
  Process: 4132 ExecStop=/sbin/ifdown -a --read-environment --exclude=lo (code=exited, status=0/SUCCESS)
  Process: 6870 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 6864 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCCESS)
 Main PID: 6870 (code=exited, status=1/FAILURE)


Jul 26 18:10:00 VMPC sh[6864]: Unknown interface enp34s0
Jul 26 18:10:00 VMPC sh[6864]: Unknown interface enp36s0
Jul 26 18:10:00 VMPC ifup[6870]: Unknown interface enp34s0
Jul 26 18:10:00 VMPC ifup[6870]: Unknown interface enp36s0
Jul 26 18:10:00 VMPC ifup[6870]: Waiting for a slave to join bond0 (will timeout after 60s)
Jul 26 18:11:01 VMPC ifup[6870]: No slave joined bond0, continuing anyway
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jul 26 18:11:02 VMPC systemd[1]: Failed to start Raise network interfaces.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Unit entered failed state.
Jul 26 18:11:02 VMPC systemd[1]: networking.service: Failed with result 'exit-code'.

```

Here is all the information relevant system info (if you need more please let me know).

```
/etc/network/interfaces
This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto enp30s0
iface enp30s0 inet static
address 172.16.0.2
netmask 255.255.255.0
network 172.16.0.0


#enp34s0 configuration
auto enp34s0
iface eth1 inet manual
bond-master bond0
bond-primary enp34s0


#enp36s0 configuration
auto enp36s0
iface eth2 inet manual
bond-master bond0


# Bonding enp34s0 & enp36s0 to create bond0 NIC
auto bond0
iface bond0 inet static
address 192.168.14.10
netmask 255.255.255.0
bond-mode balance-alb
bond-miimon 100
bond-slaves none

```

```
ifconfig -a
bond0     Link encap:Ethernet  HWaddr ca:f4:3e:98:f3:6c            inet addr:192.168.14.10  Bcast:192.168.14.255  Mask:255.255.255.0
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp30s0   Link encap:Ethernet  HWaddr 4c:cc:6a:fb:09:55  
          inet addr:172.16.0.2  Bcast:172.16.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp34s0   Link encap:Ethernet  HWaddr 00:e0:4c:68:12:30  
          inet addr:192.168.14.2  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::5e95:83bb:bd91:9be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14017 (14.0 KB)  TX bytes:14358 (14.3 KB)


enp35s0   Link encap:Ethernet  HWaddr 00:e0:4c:68:12:31  
          inet addr:192.168.0.204  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6f6:99fc:cb14:9cdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18139 errors:0 dropped:1224 overruns:0 frame:0
          TX packets:9281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9936585 (9.9 MB)  TX bytes:1053632 (1.0 MB)


enp36s0   Link encap:Ethernet  HWaddr 00:e0:4c:68:12:32  
          inet addr:192.168.14.3  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::c771:25b:9923:26a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24406 (24.4 KB)  TX bytes:23893 (23.8 KB)


enp37s0   Link encap:Ethernet  HWaddr 00:e0:4c:68:12:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:55290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:26230968 (26.2 MB)  TX bytes:26230968 (26.2 MB)


virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


virbr0-nic Link encap:Ethernet  HWaddr 52:54:00:a1:14:54  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1450
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1451
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1454
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1454
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1460
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1461
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1462
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1463
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1464
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1465
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1466
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1467
03:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43bb (rev 02)
03:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b7 (rev 02)
03:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02)
04:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
1e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
20:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
21:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
21:03.0 PCI bridge: ASMedia Technology Inc. Device 1184
21:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
21:07.0 PCI bridge: ASMedia Technology Inc. Device 1184
22:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
23:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
24:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
27:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 699f (rev c7)
27:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
28:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
28:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1456
28:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 145c
29:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
29:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
29:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Device 1457
```

From what I can tell it isn't correctly detecting the NICs I've tried to bond despite (best to my knowledge) me configuring them correctly as per the guides I've looked at. I would be grateful for any help with this.

---

