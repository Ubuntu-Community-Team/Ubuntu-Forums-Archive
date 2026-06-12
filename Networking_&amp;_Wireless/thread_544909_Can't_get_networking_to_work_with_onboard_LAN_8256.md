---
title: "Can't get networking to work with onboard LAN 82566dc or PCI realtek rtl8139 LAN card"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by lexhider on 2007-09-06
Hi,
I'm out of ideas on getting networking working on my new computer.
I bought an Intel D695OT mobo, which has Intel 82566dc onboard LAN.

After playing around with this I couldn't get it working.
So I put in a PCI network card, Realtek RTL8139.
I can't seem to get it working either.

Hopefully someone has any idea of where I'm going wrong.

Here's some relevant info.

Internet connection is fine. I'm posting this from my old computer running off an ubuntu live cd.

PCI LAN card doesn't work regardless of if onboard LAN is enabled/disabled in BIOS.

I have tried latest test versions of ubuntu and fedora with same results.

lspci gives:
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsmod gives:
e1000                 126272  0
8139cp                 25088  0
8139too                27776  0
mii                     6528  2 8139cp,8139too

dmesg gives [note: this includes me switching cable from one port to another]:
[   36.855312] 8139too Fast Ethernet driver 0.9.28
[   37.505637] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   41.549468] eth1: RealTek RTL8139 at 0xf8862000, 00:0e:2e:9e:ac:a2, IRQ 23
[   41.549470] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   46.437794] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   47.366114] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   86.791862] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   97.715031] eth1: no IPv6 routers present
[  379.082856] eth1: link down
[  384.870151] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  384.870158] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  384.873192] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  395.423126] eth0: no IPv6 routers present

ifconfig eth0:
eth0      Link encap:Ethernet  HWaddr 00:19:D1:E3:1E:0A 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:920118 (898.5 KB)  TX bytes:8687 (8.4 KB)
          Base address:0x30e0 Memory:50300000-50320000

ifup eth0:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:d1:e3:1e:0a
Sending on   LPF/eth0/00:19:d1:e3:1e:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory

ifconfig eth1:
eth1      Link encap:Ethernet  HWaddr 00:0E:2E:9E:AC:A2 
          inet6 addr: fe80::20e:2eff:fe9e:aca2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:827278 (807.8 KB)  TX bytes:7109 (6.9 KB)
          Interrupt:23 Base address:0x2000

ifup eth1:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:2e:9e:ac:a2
Sending on   LPF/eth1/00:0e:2e:9e:ac:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory


Thanking you in advance,

Lex

---

### Post by trooper666 on 2007-09-07
if you have realtek 8139**D** chipset (like me and oithers) it apparently doesn't work anymore (it used to work in fc6 just fine) i dont know why and what changed but something did

---

### Post by Joe325 on 2007-09-07
I  have just put a new pc together with the following stats:
E6750 CPU
2GB RAM@800Mhz
ATI HD2600XT Pro
ECS P35T-A mobo
Pioneer DVD±RW
250 SATA HDD
I had Ubuntu 610 running on a Dell previously without any hiccups ever. Now, when checking if all my hardware works on 704, my NIC wont detect. It is a 82566DC-2 Intel Pro adapter and I cant get it to detect.
Dmesg shows nothing; lspci- same. I have vista Business I wanna dual boot with, but without a working NIC, its hard to operate. I copied ndiswrapper and the driver folder off my Mobo disc to an x-HDD nad tried to install it that way, but ndiswrapper goes thru with all errors within the terminal.....  Any Ideas????:(

---

### Post by Joe325 on 2007-09-23
*****  IVE WORKED IT OUT *******

I downloaded the e1000 driver from Intel website
Extracted the file to the desktop nad cd into directory
run ' sudo make install '
run rmmod e1000
then sudo modprobe e1000

The little network icon will start to spin around & BANG.... **You are now connected to the wired network !!!**  ;)

---

### Post by noob12 on 2007-09-23
Two threads:

For the Realtek try this:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

For the Intel Pro/1000  e1000 build this:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

ADDED:
On closer inspection, your e1000 problem might not be addressed by the more recent driver, but give it a try.
If you still have trouble, post back.

---

