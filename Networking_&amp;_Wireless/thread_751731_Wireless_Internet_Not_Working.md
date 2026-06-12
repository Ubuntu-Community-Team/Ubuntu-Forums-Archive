---
title: "Wireless Internet Not Working"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by joeshmoe on 2008-04-10
I am trying to find out why the wireless internet on my laptop is not working.  After searching google I found these two commands lspci and lshw -c network.  But I still can't find out why it won't connect.

When I use the lspci command it shows that it is detecting the wireless network card. Then when I enter the sudo lshw -C network command right after the password it says *-network DISABLED. I think this is why I am not able to access the internet. Could someone help me enable the connection? It is not encrypted.

```
paul@paul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```


```
paul@paul-laptop:~$ sudo lshw -C network
[sudo] password for paul:
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:ce:73:66:ba
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:39:70:ef
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5752-v3.19 latency=0 link=no module=tg3 multicast=yes port=twisted pair
```

---

### Post by dstew on 2008-04-11
Go to System --> Administration --> Networking, click on the wireless interface, and check the Enable box.

---

### Post by senortighto on 2008-04-15
i have a similar problem, but the wireless networking option isn't available for me to click on, BUT, i can still search for wireless networks if i just click on the icon.  also i don't get a logical name for my network card (intel 2200bg) when i run  the lshw -C network command.

thanks for any help on this

---

### Post by dstew on 2008-04-15
If you have Network Manager installed, only one interface is allowed. If you have a working wired interface, the wireless will not be enabled. Try unplugging the wired interface, reboot, and see if the wireless interface can be enabled.

---

### Post by joeshmoe on 2008-04-15
I pressed the the box next to the wireless connection. It said changing interface configuration for a few seconds, but the internet still doesn't work.

---

