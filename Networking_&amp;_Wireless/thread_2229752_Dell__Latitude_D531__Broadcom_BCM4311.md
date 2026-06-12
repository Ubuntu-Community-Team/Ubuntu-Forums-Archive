---
title: "Dell  Latitude D531 / Broadcom BCM4311"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by finn2 on 2014-06-15
Hi all, Any advice please? I've been trying to solve this for ages but i'm just going round in circles.
I've got a Dell Latitude D531 - No OS was on it so i installed Ubuntu yesterday. **I can connect successfully online with a wire but the dedicated Wifi button on the keyboard does not work (no light appears when pressing).**
I accessed the BIOS and it looks like wifi and the switch are not turned off.
Tried numerous things - really dont know what the problem is. Below is the results of some commands, any help appreciated!

```
**$ sudo lshw -C network;lsb_release -a;uname -a;sudo rfkill list;dmesg|grep -i firm;sudo iwlist scan**

*-network
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=wl latency=0
resources: irq:17 memory:fe8fc000-fe8fffff
*-network
description: Ethernet interface
product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:1c:23:af:7d:65
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5755m-v3.29 ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:43 memory:fe7f0000-fe7fffff
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty
Linux ellie-Latitude-D531 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux
[ 0.000000] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[ 0.144344] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[ 0.232891] [Firmware Warn]: MTRR: CPU 1: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[ 0.626951] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

**$ lspci -nnk | grep -iA2 net**
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
Subsystem: Dell Device [1028:0206]
Kernel driver in use: tg3
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
Kernel driver in use: wl
[B]
$ lspci -v[/B]
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
Subsystem: Dell Device 0206
Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fe900000-feafffff
Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
Capabilities: <access denied>

00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
Memory behind bridge: fe800000-fe8fffff
Capabilities: <access denied>
Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
Memory behind bridge: fe700000-fe7fffff
Capabilities: <access denied>
Kernel driver in use: pcieport

...................(deleted some of the results i dont think are needed ) ..........................................

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
Subsystem: Dell Device 0206
Flags: 66MHz, medium devsel
I/O ports at 10c0 [size=16]
Capabilities: <access denied>
Kernel driver in use: piix4_smbus

03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
Subsystem: O2 Micro, Inc. Firewire (IEEE 1394)
Flags: bus master, medium devsel, latency 64, IRQ 23
Memory at fe6ff000 (32-bit, non-prefetchable) [size=4K]
Memory at fe6fe800 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: firewire_ohci

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
Subsystem: Dell Device 0206
Flags: bus master, fast devsel, latency 0, IRQ 43
Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: <access denied>
Kernel driver in use: tg3

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: wl

**$ sudo iwconfig**
lo no wireless extensions.
eth0 no wireless extensions.
**no wlan0 ??????????**
```

---

### Post by howefield on 2014-06-15
Have you tried installing the proprietary driver with the additional drivers application (with the wired connection) ?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by finn2 on 2014-06-15
Hi - thanks for the reply.

**$ sudo apt-get install bcmwl-kernel-sourc**e
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.

I ran the above(after get update), not sure if that was the required instruction, i cant see any change.
Sorry but i'm 24 hours new to Ubuntu so not really sure what i'm doing.

---

### Post by Bucky Ball on 2014-06-15
What Howefield is saying is look in 'Additional Drivers' (or maybe 'Hardware Drivers' in your release) after an update and you may see something referring to b43 available for the card. 

You need to be online with a cable, though. Catch 22.

---

### Post by Hadaka on 2014-06-15
hi Finn2
Ubuntu loads the incorrect wireless driver by default
you have..
configuration: driver=wl latency=0

the wl driver...your card requires the linux-firmware-nonfree

open a terminal....ctrl/alt/t ..make sure you are connected to
the internet with the cable, we need to load the correct driver.
at the terminal  COPY and paste one line at a time.

this removes the incorrect driver
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf # this line may fail,,,not to worry
```

this installs the correct driver
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot
remove the cable and test the wireless

go here and mark solved it this works for you ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

*DELL keyboard WIRELESS on/off ... pess the fn and f2 keys together ONE time for on  ONE time for off

---

### Post by Bucky Ball on 2014-06-15
What the anchovy, herring and squid pizza craving Hadaka said ... with clam sauce. Hmm, I'm hungry! :)

Give the commands provided a go and see if it fixes. That wl driver is wrong for that card, as mentioned. Older card, strange how wl is still being installed by default for it. :-k

---

### Post by finn2 on 2014-06-15
Hi - many thanks for the advice

i done the get update then:-

$ **sudo apt-get install linux-firmware-nonfree**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  dkms fakeroot libfakeroot
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
$** sudo modprobe b43**
# prompt just flashes here.....

when i run the modprobe b43, the prompt moves to the next line and starts flashing, ive waited a few minutes and the command prompt doesnt return? I cant seem to break out of it to restore a command prompt. I left it a few minutes but nothings happening?

---

### Post by finn2 on 2014-06-15
Hi All
Working!!!:D
I dont know if it made any difference but i ran:-
sudo apt-get install b43-fwcutter firmware-b43-installer
[FONT=arial]
It done some unpacking, i then rebooted and when i logged in the wifi switched on. 
And all the time i was doing this there was a voice inside my head singing "*You dont know what your doing...*":D
Not sure if the above command was necessary but its working anyway.
Thanks all for your input, wouldnt have resolved this without your help!
Cheers[/FONT]

---

### Post by Hadaka on 2014-06-15
GREAT !! glad you got it going, me and Bucky Ball
are very proud.
please mark your thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

### Post by Bucky Ball on 2014-06-15
> **Hadaka said:**
> GREAT !! glad you got it going, me and Bucky Ball
are very proud.


+1. Enjoy. ;)

---

### Post by ski_phreak on 2014-10-29
Even though it's solved, a summary might be useful.

I just gave new life to a dell Latitude 630 with Kubuntu LTS 14.04, and had the same wifi hassles.  (stupid proprietary drivers.)  The bcmwl driver is the only driver that appears in the "Driver Manager," even after installing the correct ones (bw43 and linux-firmware-nonfree.  

On to the terminal!

The **problem** seems to be caused by *buntu installers defaulting to the wrong driver, and preventing b43 from loading.

To [B]remove the wrong driver:
[/B]```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf # this line may fail,,,not to worry
sudo shutdown -r now

```

I don't **know** that a shutdown here is needed, but it can't hurt.

to **install the right ones**:
```

sudo apt-get install linux-firmware-nonfree b43-fwcutter firmware-b43-installer
sudo shutdown -r now
sudo modprobe b43

```

This shutdown (before modprobe-ing) is required.  Without it, I got exactly the same result--flashing cursor and a lockup in Konsole/terminal.

All fixed as soon as I modprobed.  No reboot needed...unlike that **other** so-called operating system.

---[SIZE=1]

(If Windows is an operating system...I think the only operation it performs must be a spay/neuter.)[/SIZE]

---

### Post by Bucky Ball on 2014-10-29
Thanks for sharing.

*Thread closed.*

---

