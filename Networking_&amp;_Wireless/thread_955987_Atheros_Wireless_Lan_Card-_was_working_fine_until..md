---
title: "Atheros Wireless Lan Card- was working fine until..."
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by vineetvb on 2008-10-22
Hi all, 

The following events occured-  

1. I install ubuntu on Acer aspire 4520 and my wireless card (Atheros) 
works out of the box. 
2. Few days ago I change my D-link WBR-1310 WLAN router password. 
3. My wireless internet stops getting detected altogether, even at Starbucks or my Univiersity Wi-fi or anywhere else for that matter. 

4. I do this 
vineet@vineet-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

5.then this
vineet@vineet-laptop:~$ sudo lshw -C network
[sudo] password for vineet: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:91:8c:9d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
6. I post this message. 

Other facts: 
Wireless still works with Windows Vista.
WLAN card LED is always turned off in Ubuntu (even when the connection worked).

Please help.

---

### Post by vineetvb on 2008-10-24
I get no reply yet. 
Please help!

---

### Post by melojo on 2008-10-24
Did the system do an update?

Sounds like a driver problem to me.

Try this link below and see if it helps you get it working again.  
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

### Post by vineetvb on 2008-10-25
Thanks melojo! 
Internet up and running again. 
gabsik's post in the link helped.
I guess i was just lazy to re-install the drivers.

---

