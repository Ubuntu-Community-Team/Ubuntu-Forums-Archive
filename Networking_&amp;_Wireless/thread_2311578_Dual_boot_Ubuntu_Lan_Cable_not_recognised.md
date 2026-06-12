---
title: "Dual boot Ubuntu Lan Cable not recognised"
date: 2016-01-28
forum: Networking &amp; Wireless
---

### Post by prakhar2 on 2016-01-28
I have both Windows 10 and Ubuntu installed on my system and I am able to access internet through ethernet on Windows 10 and sometimes even on Ubuntu but many times it doesn't detect my lan cable showing it unplugged.
Following are some of the results of commands I found generally asked for in such situations:

sudo ifconfig -a
[sudo] password for prakhar:
eth0      Link encap:Ethernet  HWaddr 3c:07:71:59:2c:f8 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20265 (20.2 KB)  TX bytes:20265 (20.2 KB)

wlan3     Link encap:Ethernet  HWaddr b8:76:3f:c2:a3:19 
          inet6 addr: fe80::ba76:3fff:fec2:a319/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16
---------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
------------------------------------------------------------------------------
------------------------------------------------------------------------------

cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=3C:07:71:59:2C:F8,

[ifupdown]
managed=false

---------------------------------------------------------------------------
---------------------------------------------------------------------------

dmesg | grep -e eth0 -e bcm
[    1.160251] r8169 0000:0e:00.0 eth0: RTL8168g/8111g at 0xffffc90000670000, 3c:07:71:59:2c:f8, XID 0c000800 IRQ 46
[    1.160253] r8169 0000:0e:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   12.431342] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.999491] r8169 0000:0e:00.0 eth0: link down
[   20.999512] r8169 0000:0e:00.0 eth0: link down
[   20.999560] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.999894] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

------------------------------------------------------------------------
-------------------------------------------------------------------------

lshw -C Network
WARNING: you should run this program as super-user.
  *-network              
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan3
       version: 01
       serial: b8:76:3f:c2:a3:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:d1700000-d1707fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 0c
       serial: 3c:07:71:59:2c:f8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:2000(size=256) memory:d1500000-d1500fff memory:d1400000-d1403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
 
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)

These are the results I got when Ubuntu was not able to detect my lan cable
If anyone has any idea Please do share your knowledge :D

---

