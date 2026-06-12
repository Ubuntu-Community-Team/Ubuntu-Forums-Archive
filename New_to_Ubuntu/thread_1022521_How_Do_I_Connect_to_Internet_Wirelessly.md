---
title: "How Do I Connect to Internet Wirelessly?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by AvocadoNia on 2008-12-26
I am using Ubuntu Intrepid (8.10) on a dual boot ASUS eeePC. I can connect to internet wirelessly on the Windows side of the partition but do not know how to do that on the Linux side. 

At my present location, at my dad's home, there is wireless access  available but I only know how to detect it and use it from a Windows environment.

I want to learn how to use the available wireless connection to internet from the Ubuntu OS.

Thank you in advance for any instructions, links or other hints you might offer me so that I can solve this problem.

---

### Post by eagle416 on 2008-12-26
I'm on KDE, but I think there's a Network Manager icon in the upper right, and you right click that to select wireless networks. It's like that in Xubuntu, anyway.

---

### Post by melojo on 2008-12-26
open a terminal and post the output of

```
 lspci 
```

and

```
 sudo lshw -C network 
```

This will give us more info.

---

### Post by AvocadoNia on 2008-12-26
Thanks for the replies. Keep 'em coming. :)

 Unfortunately, I do not recognize a and "Network Manager" icon and the output from putting "lspci" in a terminal command line was more than I could retype accurately. Selecting followed by Control C then Control V did not result in the copying and pasting of the output.

---

### Post by Racecar56 on 2008-12-26
[QUOTE=melojo]open a terminal and post the output of

Code:

 lspci

and

Code:

 sudo lshw -C network

This will give us more info. [/QUOTE]
Do this:
1. Do what melojo said (quoted above).
2. Take the output out of 1 and highlight it by dragging the mouse from begining to end and then right click on any of the highlighted text and click Copy.
3. Reply and put output of each.

---

### Post by AvocadoNia on 2008-12-26
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
$

---

### Post by Monotoko on 2008-12-26
Try this:

System -> Prefrances -> Network Configuration -> Wireless -> Add
then type in all the router info

---

### Post by AvocadoNia on 2008-12-26
$sudo lshw -C network
PCI (sysfs)
...and then with a touch of something this appeared:
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:27:cf:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.2.5 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:0d:eb:a8:b0:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
$

---

### Post by AvocadoNia on 2008-12-26
Yes, that works maybe. But what is the router information, where do I find it?

SSID, BSSID, MTU, and some other stuff...automatic, ad hoc, infrastructure....

Thank you.

---

### Post by handydan918 on 2008-12-26
Nah. Do the easy thing and install eeebuntu. i just did, and everything works out of the box. Otherwise, you'll end up fighting with that atheros wireless chip...

---

### Post by AvocadoNia on 2008-12-26
$ chown -R us base       
chown: invalid user: `us'
$ chown -R ana base
chown: cannot access `base': No such file or directorys 
$ 

I need to sleep now. I'll check back with this thread in the morning.

Thanks

---

### Post by handydan918 on 2008-12-27
> **AvocadoNia said:**
> $ chown -R us base       
chown: invalid user: `us'
$ chown -R ana base
chown: cannot access `base': No such file or directorys 
$ 

I need to sleep now. I'll check back with this thread in the morning.

Thanks

Heh. 
That's part of my siggy. If you want to run that without errors, you have to do ```
mkdir base && adduser us
``` first. But all it means is the shell equivalent of "All you base are belong to us."

Sorry for your confusion...):P

---

### Post by Miljet on 2008-12-27
I have the exact same wireless adapter that you have. When I originally installed Gutsy, it automatically found and installed a restricted driver called "Atheros Hardware Access Layer (HAL)". Then when I upgraded to Hardy, it automatically added another driver called "Support for Atheros 802.11 wireless LAN cards".

I don't know where these drivers came from, but my wireless card has always worked flawlessly. These drivers are found under System-> Administration-> Hardware Drivers.

I just did a search under Synaptic Package Manager and couldn't find anything.You might check under Hardware Drivers and see if they are there and just not enabled.

---

### Post by Gtone on 2008-12-27
Hi all!

i just installed 8.04 on an Acer Apire one and i have ni wifi at all. the network icon at the notification area is not showing me any wireless networks at all. I have both restrictred drivers in use (HAL & Support for Atheros...) but no wireless. 

What could i do?

---

### Post by AvocadoNia on 2008-12-28
Okay. I see that I have a non-restricted driver that supposedly is active. It's the same one that was mentioned by a previous responder. Thanks.

In the synaptic manager I searched for "atheros" and 3 items came up. The first one "alt-2" seems to be a driver particularly for the eeePC. There is a collection of items that need to be in place for it to work properly so "32 packages will be held back and not upgraded, 115 packages will be installed."

So now I need to unplug the desktop and use the wire to plug my eeePC into internet, so to speak. That's the only way to download the goods...right now I don't have wireless internet on the Ubuntu side of the partition...

If it works I'll report back and mark this thread solved.

---

### Post by handydan918 on 2008-12-29
Again, if it doesn't work easily, just [d/l and install eeebuntu]("http://www.eeebuntu.org/index.php")

---

