---
title: "Wireless stopped working on Dell 1420 Ubuntu"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by bbddnn07 on 2008-03-01
Hey UF, I'm new to Linux and I would really appreciate it if someone would walk me through the issue I am having, because the other threads on this topic really lost me. 

Anyway, I had my wireless connection working fine on my Dell 1420 Inspiron Ubuntu until I made some changes at some point and rebooted, after which the wireless option no longer appeared in the Network Settings box.  Let me know what commands I should run to give some insight into the problem.  Here is what I get when I run lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

So it looks like the card is still in there.  How can I turn it back on???

---

### Post by jan quark on 2008-03-02
please post the results of these terminal commands:

```
iwconfig
```
```

sudo lshw -C network
```

```
cat /etc/network/interfaces
```


try to restart your network with:
```

sudo /etc/init.d/networking restart
```

---

### Post by bbddnn07 on 2008-03-02
Thanks for responding Jan.  Here are the results of those commands:

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

**sudo lshw -C network:**
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fd:59:82
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.1.107 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

**cat /etc/network/interfaces:**
auto lo
iface lo inet loopback

#mapping hotplug
#script echo
#map ath0

#iface <ath0> inet dhcp
#  wireless-defaultkey 1 (specifies which key is default)

#  auto <ath0>

iface eth1 inet dhcp
netmask 255.0.0.0
address 76.124.144.126
wireless-essid astrohouse

auto eth1

**sudo /etc/init.d/networking restart:**
 * Reconfiguring network interfaces...                                          eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.


Thanks in advance!

---

### Post by unutbu on 2008-03-02
"sudo /etc/init.d/networking restart" will bring no joy until iwconfig shows eth1.
Try

```

sudo ifup eth1

```

If the ifup command looks successful, try

```

sudo /etc/init.d/networking restart

```

again.

If unsuccessful, you should check that the driver module is loaded into your kernel. To that end, run and post

```

lsmod | grep ipw3945

```

---

### Post by bbddnn07 on 2008-03-02
Thanks unutbu.  It looks like my computer doesn't recognize eth1, here's what I get for sudo ifup eth1:
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

and then for  lsmod | grep ipw3945:
ipw3945               120224  0 
ieee80211              34248  1 ipw3945

---

### Post by unutbu on 2008-03-02
It appears that although the ipw3945 driver module is loaded into the kernel, the device is not being successfully associated with eth1.

I don't know why this is so, but removing the driver and doing a fresh re-install of the driver sometimes works. 

A google search of ipw3945 yields this link:

[http://sourceforge.net/project/showfiles.php?group_id=158253](http://sourceforge.net/project/showfiles.php?group_id=158253)

I don't know what version of the ipw3945 you have. Perhaps this one, version 1.2.2 dated July 31,2007 is newer? Even if it is the same as what you currently have, perhaps something corrupted your current installation, and a re-install of the driver might cure your current woe.

Also, a google search of 3945ABG yields a driver straight from intel:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

If the ipw3945 driver above does not work, you might want to try installing intel's linux driver.

---

