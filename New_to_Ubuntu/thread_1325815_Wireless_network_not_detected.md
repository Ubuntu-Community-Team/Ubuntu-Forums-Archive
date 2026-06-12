---
title: "Wireless network not detected"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by georgepag on 2009-11-13
I have Ubuntu 9.1.  It detected my wireless at home with no problems but I am now trying to connect to a different wireless network (that I control)  but it does not see the network. Rright now I'm hard wired to the router.  I know the router and wirelesss works because I was able to connect with Vista.  Any ideas?  Here is the output of   sudo lshw -C network if that helps.   The router is a Linksys WRT160N thanks.

george@george-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:4b:58:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:d9500000-d9501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:cb:31:d6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:5000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
george@george-laptop:~$

---

### Post by brandonsh on 2009-11-13
Sorry, I'm going to have to ask you a generic question:
Is the router set as visible?

---

### Post by georgepag on 2009-11-13
Hi,

Yes it is with WEP security.

---

### Post by georgepag on 2009-11-13
sme as my other wireless network but it has a different SSID

---

### Post by brandonsh on 2009-11-13
Have you tried changing some of the router's settings? If that's too much trouble because you have computers connected or something, I'm kinda stumped. ;)

---

### Post by georgepag on 2009-11-13
All i can say is..DUHHH.  I didn't notice that when I booted Umbutu the wireless never powered on.  Once I turned the wireless on it found the network fine.
But, I have noticed with both network connections that the network indicator light flashes from blue to red to blue, seemingly randomly.  Is this typical?  It doesn't seem to affect the connection.

---

### Post by stormvinyl on 2009-11-13
Y

---

### Post by georgepag on 2009-11-13
OK.  But why does it do this?  I'm curious and want to understand what is going on.  It is different behavior from windows.

thanks for all the help.  I'm going to need a lot more.  Graphics drivers will be the next topic. :D

---

