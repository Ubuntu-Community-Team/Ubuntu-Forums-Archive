---
title: "hp550 wireless help"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by q1gzn on 2009-01-15
hi  all  
iam  very new in  ubuntu and  like it  so much 
but i have hp550 
please i need wireless driver step by step installing

---

### Post by ja660k on 2009-01-15
hi, 

type into terminal 
```
iwconfig 
```
and this
```
lspci
```
and paste results

and do you still have the windows partition on your HDD

---

### Post by superprash2003 on 2009-01-15
output of lshw -C network

---

### Post by q1gzn on 2009-01-16
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
```

and the  second was


```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
 thanks

---

### Post by q1gzn on 2009-01-16
```
 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:64:54:97:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 ip=10.10.10.254 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:67:55:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:06:b8:ab:58:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

hi it me again 
please i found that my wrlss adapter is already listed but  it is disabled
please any one  help me how to enable it ? 
thanks  alot

---

