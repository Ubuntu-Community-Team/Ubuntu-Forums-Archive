---
title: "intel pro wireless 2200bg -- can´t connect with wify"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by jj662 on 2008-10-28
I have a HP nc6220 laptop.
My Wired connection is working great (I am actually on line with it as I am typing right now), but the wireless is not cooperating. Arrrgggghhhh. 

I have the Intel PRO/Wireless 2200BG [Calexico2]Network Connection [rev5] installed per Ubuntu. This seems to line up with the hardware that this HP nc6220 has noted on it&#347; tech support site per the extended model number.

I did the Terminal window commands: iwconfig and sudo lshw -C network and this is what came up. (EDGEMONT is the name of my home router.)

jeffj@HPLaptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSID:"EDGEMONT"
Mode:Managed Frequency:2.437 GHz Access Point: 00:13:46:A6:E8:98
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=79/100 Signal level=-50 dBm Noise level=-91 dBm
Rx invalid nwid:0 Rx invalid crypt:14169 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.


jeffj@HPLaptop:~$ sudo lshw -C network
[sudo] password for jeffj:
*-network
description: Ethernet interface
product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:10:00.0
logical name: eth0
version: 11
serial: 00:15:60:b0:30:c3
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751m-v3.29a ip=192.168.0.105 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
*-network
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0
logical name: eth1
version: 05
serial: 00:15:00:17:7a:d3
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: da:bf:88:24:ad:ee
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

In another thread it was suggested to make sure the network-manager was installed, so I did that too.


jeffj@HPLaptop:~$ sudo apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
network-manager-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
libarts1c2a kdelibs4c2a libartsc0 kdelibs-data liblualib50 libavahi-qt3-1
libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


When Windows was installed on this same HP Laptop, the wireless worked fine with this router.

I am very new to Linux. This install is only a few days old on this machine. I installed Unbuntu 8.04, and under the Network configuration I could at least see my home router, but it wouldn´t go ahead and connect, getting an IP address from the router. It would not appear in the list of available networks either. Last night I updated to 8.10 in an effort to see if that would work better.
Same basic problem, but this time it won´t browse since everything is now under the Network Connections applette.

So,
what do I do next or where do I go from here??
Sorry for the long thread.
JeffJohnson
Portland, OR

---

### Post by jj662 on 2008-10-28
The plot thickens.

I ditched both Version 8.04 and 8.10 and found a download of Gutsy Gibbon version 7.10.

The wireless worked out of the gate like a racehorse.

Huh ????????????????

So, what did you developers do to break wireless Ethernet for the Intel Pro/Wireless 2200BG with the version 8 upgrade??? It is, afterall, one of the built in drivers.

I am staying with Gutsy Gibbon for now and able to use Wifi with NO issues.

This might be a quicker solution for others as well.

---

### Post by markofealing on 2008-10-28
I've got the same problem on one of my two laptops, both run Kubuntu 8.04 and both have IPW2200 cards in them. On my HP XE4500 the card works and connects using Wireless Assistant, I could never get it to work with Network-Manager-KDE but that's another story.

On my Dell Latitude C640, the wireless stopped working this week. I removed network-manager and net-tools (something of a mistake, when I realised I had lost all networking) but re-installed the missing packages of the Alternate is 8.04 CD. wired networking came back but wireless still does not work. I can see my wireless card, when I try to connect via network-manager it gets to 57% and fails. I'm using WEP encryption 64-bit HEX, I think this where the problem lies.

Following this post [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) for WEP I got as far as

sudo iwconfig eth1 key xxxxxxxx

and then got 
"Error for wireless request "Set Encode" (8B2A)
SET failed on device eth1 Operation not supported"

This suggests that there is som sort of problem with WEP.

The etc/network/interfaces file contains nothing worth noting. In fact it contains nothing about eth1, but as it is similar to the file on my working HP I assume this is okay.

What really sickens me is that the Dell is dual boot and Windows XP works just fine wirelessly so the hardware is okay.

Anybody got any suggestions. Ditching Linux is not one of them, although at times the thought does cross my mind!!:mad:

---

### Post by markofealing on 2008-10-29
I've now eliminated my IPW2200BG wireless card totally as I've just booted off a Gutsy Gibbon Live CD and using terminal connected using WEP to my wireless network using the commands  in this post [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495). The same commands which do not work in 8.04!

I assume that any wireless configuration is stored outside the users Home directory so one option is to:

1. Backup my Home folder (anyone know the best way of doing this?)
2. Make a note of my installed applications
3. Reinstall Kubuntu

A bit of a sledgehammer to crack a walnut approach but I can't establish what component is stopping me to connect to my wireless using my WEP key.

The only thing which still does not work with the live CD is "Network-Manager" but there again this addition to Kubuntu has always seemed like a half baked idea which never worked properly from the start.

Alternatively, wait until 8.10 is released (only a few days away)and hope it fixes the problem.

Anyone got any better ideas?

---

### Post by markofealing on 2008-11-09
Well an upgrade sort of worked Java6 refused to install and so did mscompress. A manual install on reboot fixed the later, however wireless was still knackered.

Only solution, trash the laptop and re-install!

---

### Post by Arabiest on 2008-11-09
my solution was a tuff one to decide and that is to make a fresh installation from Ubuntu 8.10 live CD and all the wireless problems solved forever.

make sure you back up your important documents before going ahead with this solution.

enjoy!

---

### Post by markofealing on 2008-11-17
The fresh install worked for me, knetwork manager now connects faultlessly to my wireless.

Whilst it was a pain to do the end result was worth it.

KDE4 is rapidly growing on me as well!

---

