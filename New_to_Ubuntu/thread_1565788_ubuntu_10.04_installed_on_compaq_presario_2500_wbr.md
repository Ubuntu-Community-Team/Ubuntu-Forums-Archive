---
title: "ubuntu 10.04 installed on compaq presario 2500 w/broadcom fails to detect any sigs"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by REOALEXKING on 2010-09-01
**New to Linux (Ubuntu 10.04.1), installed on COMPAQ PRESARIO 2500 (2570US with Broadcom 802.11b/g WLAN), went OK except that although WIFI is displayed on top bar, no signals of any kind are detected.**
**WIFI works fine when booted up using Microsoft Windows XP (dual-boot Ubuntu/XP config).**
**I had no available Internet connection during the initial Ubuntu install. Would a re-install of the Ubuntu OS with a now available LAN link to Internet cure my problem? Or ???**
**Any suggestions/recommendations will be appreciated.**

---

### Post by anewguy on 2010-09-01
There are more than 1 way to get this working, but the easiest and preferred way is as follows:

IF YOU CAN HARDWIRE YOUR PC TO THE ROUTER:

- open a terminal window (Applications/Accessories/Terminal)

-  type:

sudo apt-get update <press enter>  When prompted, enter your normal ubuntu password

- close the terminal window by typing:

exit <press enter>

- unplug the physical hard wire cable to the router


COMMON STEPS

- look in System/Administration/Hardware Drivers and see if there is a driver listed for your wireless - if so, enable it

- wait a minute or 2

- right-click on the network manager icon and be sure "Enable Wireless" is checked

- check for wireless networks

Please note that if you are trying to connect to your own network that you need to be aware of how your router is set up:

- if the router is not broadcasting the ESSID (e.g., it's not broadcasting a network name), you will need to left click on the network manager icon and manually setup the connection to a hidden network

- if the router has MAC filtering enabled, be sure your PC's MAC address is in the routers accepted MAC addresses list

- if you have security enabled, such as WEP, WPA, WPA2, etc., you will need to provide the security type and the password/passphrase when you connect.  On the first such successful attempt you will probably be asked to enter a network keyring password - use your normal ubuntu password to avoid being prompted everytime it tries to connect.  The only exception I know of is if you have your logon set to automatic (e.g., you don't logon when ubuntu starts) - if that is the case you will be prompted for the keyring password each time it tries to connect to the network.

If you can't get this to work or have any questions, please post back.  If it does work, please let us know and mark the thread as "solved" via the thread tools.

Dave ;)

---

### Post by markandey on 2010-09-26
I had the same problem I found that its problem of improper broadcom firmware 
1.Open Software Center
3.Search b43-fwcutter
install this and your firmware will be upgraded. Thats it reboot your computer and you will find that 

Puting some more information ( so that people having same problem  will get this page from google) 
Linux version : Ubuntu 10.04.1 LTS
PC: Compaq CQ 45 (207 tu) Series Laptop 
Problem: network disabled when we type lshw -C network
open terminal and type 
**sudo lshw -C network**

You should get following output 
```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:98500000-98503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:e5:3d:6a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:3000(size=256) memory:92410000-92410fff(prefetchable) memory:92400000-9240ffff(prefetchable) memory:92420000-9243ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:52:42:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.101 multicast=yes wireless=IEEE 802.11bg


```


You should automatically get all wifi network listed in your system tray!!

Thanks,
Markandey

---

