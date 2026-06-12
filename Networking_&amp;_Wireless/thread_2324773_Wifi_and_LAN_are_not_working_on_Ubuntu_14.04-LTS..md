---
title: "Wifi and LAN are not working on Ubuntu 14.04-LTS."
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by Pradeep_Chl on 2016-05-16
Ubuntu 14.04 LTS. 

The Wifi or LAN donot show up on top right corner. It is not connecting to the internet.

Please observe the following log for the commands:

```
santosh@santosh-Inspiron-3542:~$ ifconfig
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1092412 (1.0 MB)  TX bytes:1092412 (1.0 MB)


santosh@santosh-Inspiron-3542:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
lo        no wireless extensions.


santosh@santosh-Inspiron-3542:~$ sudo lshw -C network
  *-network DISABLED     
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:71:cc:00:39:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-59-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 07
       serial: b8:2a:72:9e:4c:01
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff

```
Thanks,

---

### Post by blaze24-matrix on 2016-05-16
If you are using a laptop, check the wi-fi button. Maybe it is physically stopped. Turn it ON. :confused:

---

### Post by grahammechanical on 2016-05-16
Both are listed as disabled. But both do have drivers. They are just not active.

wireless interface = broadcast=yes driver=ath9k driverversion=3.19.0-59-generic
ethernet interface = broadcast=yes driver=r8169 driverversion=2.3LK-NAPI

Is Networking disabled? Are the two devices disabled in the BIOS/UEFI settings utility or by some physical switch or in some other operating system. 

Regards.

---

### Post by bapoumba on 2016-05-16
*Thread moved to **Networking & Wireless**.*

---

### Post by Pradeep_Chl on 2016-05-17
Thanks for replies, looks like the switch is off.
It is working now.

---

