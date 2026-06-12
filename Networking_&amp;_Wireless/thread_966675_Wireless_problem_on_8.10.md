---
title: "Wireless problem on 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by arnarg on 2008-11-01
**I'm sorry if this has already been answered, I couldn't find the answer.**
I just upgraded from 8.04 (to 8.10) using the update manager, but now I can't connect to the wireless internet. At first it had some problems in 8.04, it got better when I installed ndiswrapper but it was good when the Broadcom STA driver was released. Now I'm using the STA driver and it "Sometimes" detects my wifi but never connects. I've tried to connect to wired internet to check for updates and successfully connected but there were no updates. Also, I have deactivated the STA driver and activated again.

lspci
> 02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

lshw -C network
> *-network               

       description: Wireless interface

       product: BCM4311 802.11b/g WLAN

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth1

       version: 01

       serial: 00:1b:fc:27:87:3c

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

  *-network

       description: Ethernet interface

       product: L2 100 Mbit Ethernet Adapter

       vendor: Attansic Technology Corp.

       physical id: 0

       bus info: pci@0000:06:00.0

       logical name: eth0

       version: a0

       serial: 00:1b:fc:67:1f:b5

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 module=atl2 multicast=yes

iwconfig
> lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11  Nickname:""

          Access Point: Not-Associated   

Help?

---

### Post by andbelo on 2008-11-03
Exactly the same problem with a new installation of 8.10. BCM4311. wl loading correctly.

```
$iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

```

---

### Post by pbjazzy007 on 2008-11-03
I as well cannot connect after the upgrade.  Getting ready to backup and try a fresh install.  My card is an RT2500 pci.  Everything else works like a charm.  All wireless networks within range are detected, but it will not connect.  I tried unloading and reloading the drivers, but it still didn't work.  Any help would be appreciated.

---

### Post by NawaMan on 2008-11-14
Me too have exactly the same problem.

---

### Post by superprash2003 on 2008-11-14
are you connecting to a wifi network with WEP or WPA encryption?

---

### Post by pjomega on 2008-11-14
I had the same problem with my hp compaq (a bcm 4312 rev 2 here). iwlist scan would detect networks as soon as the driver loaded, but connection attempts would time out, and eventually scanning wouldn't show anything. Actually, my problem was even worse. CPU frequency scaling also locked at 50%--try using gnome on an 800MHz amd. 

Try appending "noapic" to your kernel boot options in grub. 

Apparently kernel 2.6.27 included some major changes to the ACPI/APIC hardware interfacing. I can't find the bug report at the moment, but apparently it's caused a bunch of issues. "acpi=noirq" fixed the scaling, but the wireless problems continued. Disabling the apic subsystem completely did it for me. Good luck.

---

### Post by nexusnode on 2008-11-14
Does it sound like this thread:

[http://ubuntuforums.org/showthread.php?t=963379](http://ubuntuforums.org/showthread.php?t=963379)

---

### Post by pjomega on 2008-11-14
Can't speak for the original poster, but i've seen this on numerous threads, including that one. I mentioned my chipset, but it's not the only one that has this problem. A friend of mine with an AR242x atheros chipset had the same connection difficulties due to apic problems.

---

### Post by Bigneil on 2008-11-15
I am  NOOOB here. i have installed Ubuntu on my old laptop, and it works great but i can't get the wireless card to work. i have it connected via ethernet at the moment. there must be some drivers or some clever wee thing i can type into the terminal to get it to work????

The card is just a cheepie.  i could always buy another that is compatible?????

---

