---
title: "Wireless Net not working in Ubuntu"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by somitras on 2008-06-05
I am unable to connect to the WiFi net using my Ubuntu. The same thing works fine on the Windows boot on the same machine. Its a thinkpad R60. The output of some commands are listed below. I will appreciate if anyone could you help me with the issue. I am looking for an early reply. 

Kindly help.

{ifconfig, dmesg, lsmod |grep -i ath} are the commands that I tried. The outputs from these are shown below. I also tried a module ndiswrapper but got the message that "Module ndiswraper not found.".

Information about the network:
------------------------------
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d3:38:66:41
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 

1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 

firmware=5751m-v3.56 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:ee000000-ee00ffff irq:20
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:d8:2e:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=0 

multicast=yes wireless=IEEE 802.11g
       resources: iomemory:edf00000-edf0ffff irq:21

------------------------------------------------------------
ifconfig:
--------
ath0      Link encap:Ethernet  HWaddr 00:19:7D:D8:2E:67  
          inet6 addr: fe80::219:7dff:fed8:2e67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:19:7D:D8:2E:67  
          inet addr:169.254.6.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:D3:38:66:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4598 (4.4 KiB)  TX bytes:4598 (4.4 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-D8-2E-67-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50314 errors:0 dropped:0 overruns:0 frame:18515
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5149648 (4.9 MiB)  TX bytes:2633 (2.5 KiB)
          Interrupt:21 

------------------------------------------------------------
System > Administration > Restricted Drivers

Atheros Hardwae Access Layer (HAL) - Enabled - In use.

------------------------------------------------------------

lsmod |grep -i ath

ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204868  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci

------------------------------------------------------------

dmesg | grep ipw

No output is shown.

---

### Post by superprash2003 on 2008-06-05
please post your iwconfig output

---

