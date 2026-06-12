---
title: "Atheros QCA9565 / AR9565: Unable to connect to wireless network"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by sabareesh2008 on 2013-12-23
Some time back my system hung following which I rebooted it. Since then nm-applet does not list wireless network. It only shows wired networks. Rfkill list all shows only Bluetooth connection. ifconfig lists only eth0 and lo and no wlan0. Additional drivers have no info about broadcom and only show a graphics related driver. Kindly help.

The network controller is shown as : Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

---

### Post by tfrue on 2013-12-24
Are you positive that the wireless card is broadcom? Type:
```
lspci | grep Network
```

Also, type:
```
 sudo nm-tool
```

Thanks,
Chris

---

### Post by Bucky Ball on 2013-12-24
This is what it is:

Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01) 

 Quite clearly shown in the first post. Nothing to do with Broadcom. Do include output of 'nm-tool' though.

What is the make/model of your machine? Also, output of:

```
sudo lshw -C network
```

... please.

---

### Post by sabareesh2008 on 2013-12-24
Output of nm-tool:- Device: eth0 ----------------------------------------------------------------- Type:              Wired   Driver:   State:   Default:   HW Address:   Capabilities:             r8169              unavailable            no         74:86:7A:42:87:DE     Carrier Detect:  yes Wired Properties     Carrier:          off Output of sudo lshw -C network:   *-network                      description: Ethernet interface        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:01:00.0        logical name: eth0        version: 07        serial: 74:86:7a:42:87:de        size: 10Mbit/s        capacity: 100Mbit/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s        resources: irq:60 ioport:4000(size=256) memory:c0700000-c0700fff memory:c0400000-c0403fff   *-network UNCLAIMED        description: Network controller        product: QCA9565 / AR9565 Wireless Network Adapter        vendor: Qualcomm Atheros        physical id: 0        bus info: pci@0000:02:00.0        version: 01        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list        configuration: latency=0        resources: memory:c0600000-c067ffff memory:9fb00000-9fb0ffff Thanks in advance

---

### Post by sabareesh2008 on 2013-12-24
Sorry for the bad formatting.

---

### Post by sabareesh2008 on 2013-12-24
It is a dell inspiron 3537.

---

### Post by Bucky Ball on 2013-12-24
Post that output again, please, and this time use ```
 tags. Highlight it, hit the 'quote' icon, and change where it says [quote] at either end to [code] or click 'Go Advanced' and use the # icon.

In the current format, it is almost unusable. Thanks.

Also post the output of this:

[code] sudo lshw -C network 
```

---

### Post by sabareesh2008 on 2013-12-25
Output of nm-tool:- 
```

Device: eth0 -----------------------------------------------------------------
 Type:              Wired   
Driver:   r8169
State:   unavailable
Default:   no
HW Address:   74:86:7A:42:87:DE
Capabilities:                                                     Carrier Detect:  yes 
Wired Properties     
Carrier:          off 


```

Output of sudo lshw -C network:  
```

 *-network                      
description: Ethernet interface       
 product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller       
 vendor: Realtek Semiconductor Co., Ltd.    
physical id: 0       
bus info: pci@0000:01:00.0        
logical name: eth0        
version: 07        
serial: 74:86:7a:42:87:de       
 size: 10Mbit/s        
capacity: 100Mbit/s       
 width: 64 bits       
 clock: 33MHz        
   capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation    
  configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s        
  resources: irq:60 ioport:4000(size=256) memory:c0700000-c0700fff memory:c0400000-c0403fff   
*-network UNCLAIMED       
  description: Network controller       
  product: QCA9565 / AR9565 Wireless Network Adapter       
  vendor: Qualcomm Atheros        
  physical id: 0       
  bus info: pci@0000:02:00.0      
  version: 01        
  width: 64 bits        
  clock: 33MHz        
  capabilities: pm msi pciexpress bus_master cap_list       
  configuration: latency=0       
  resources: memory:c0600000-c067ffff memory:9fb00000-9fb0ffff 


```
Thanks in advance

---

### Post by Bucky Ball on 2013-12-25
See here and try the solution given by chilli555 in post #1 under 'SOLVED':

[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)

---

### Post by sabareesh2008 on 2013-12-27
Yes! That worked. Thanks a lot for the help :)

The website mentioned there was not available though. So I downloaded from a different website.

---

### Post by Bucky Ball on 2013-12-27
Great news! Please mark thread as solved to help others by following link in my signature. Don't forget to post a new thread with a descriptive title for any new support issues. Enjoy! ;)

---

