---
title: "Atheros AR242x"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by joelbrochill on 2008-07-18
hey there,
So I'm a bit of a noobie...I have given up on linux previously because of my wireless issues...but I was determined to get it down this time.  

So I installed ndiswrapper.  At first I tried using the drivers from HP's website, but none of them worked, ndiswrapper would install the driver but no hardware would be found.  So I followed the instructions of this forum post: [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

For the first time, ndiswrapper said hardware found when I installed those drivers, however, when I open network, my wireless does not show up.
When I typed  lshw -C network into the terminal it gave me this:


```

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:c9:c4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.141 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

The first one is my wired connection, obviously.  the second is my wireless...I don't completely understand what all of that means though...the "network UNCLAIMED" worries me.

Any help here would be awesome...I've spent the last two hours around these forums and google without too much help.

---

### Post by joelbrochill on 2008-07-19
I also have tried the guide from [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

the install seems to go smoothly, but once i type 
```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```

into the terminal it just goes to the next line with no printout or anything, as if it isn't doing anything.

---

### Post by cybrsaylr on 2008-07-19
joelbrochill,
I was having the same problem on my Toshiba laptop, counldn't get my wireless to work. I followed your advice above and now have a functioning wireless network. 
Thanks.

---

### Post by wannadumpwindows on 2008-07-19
For Atheros chipsets, there's always Madwifi. It's pretty simple to install and they offer just about any info you could need. It runs my cards great.

Download the source, and then just follow this guide:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") (How-To)

[http://madwifi.org/]("http://madwifi.org/") (Main Page and Download)

---

### Post by ojinxy on 2008-07-19
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:85:0d:31
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.6 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

I also have the same problem been trying to fix it for the past eight hours. Its just not working i tried like 50 foroumns anf guided nothing works. Can someon please help me go through this i love linux but hate having a laptop thats not wireless. PLEASEEEEEEEE HELLLLLPPPP!!!!!

---

### Post by CB500Pete on 2008-12-26
I have exactly the same problem, same wireless card on an Acer A110.
Fantastic netbook, LOVE Ubuntu.
However, it isnt easy to work around wireless. It was working fine, then just stopped working. I ahve reinstalled Ubuntu as I have spent so much time googling for answers, I just cant find anything in any forum that has helped. Ive tried for DAYS and am getting a bit grumpy :(

results OF LSHW:
*-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:68:b8:44:d6
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

<REMOVED TXT>

*-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

Any help would be greatly appreciated. It shouldn't be THIS hard to get wireless working should it??????

---

### Post by CB500Pete on 2008-12-27
Sorted!

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

---

