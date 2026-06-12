---
title: "No driver support for PCI express Asus wifi adapter?"
date: 2015-09-16
forum: Networking &amp; Wireless
---

### Post by adamftzptrck on 2015-09-16
Dear beloved ubuntu users,

I have scavenged the internet and read through many-a-book but cannot find a simple answer.
I have a Desktop running ubuntu 14.04, everything is working pretty well - of course there are some problems but I'm enjoying climbing the obstacles as I'm sure many of you are. 
However I built this desktop on the premise of being able to use wireless (router middle floor, im upstairs, you get it). Now I bought a usb dongle and it worked fine. barely fine. I was getting very low speeds (we have 60mbps download available I was getting 5). So i bought a Asus wifi adapter pci-express (model pce-ac56, yes it looks awesome). and I plugged her in, but the CD in of course its only supported on windows. (not listed anywhere else). 
So no drivers for me on my system.

Here's the question.
Is there a way for me to download the drivers so it is compatible with my system, and where would I find the "how" part?

I'll be active for the next hour or so, and then I'll be back on again later.
If anyone can help me... I will give you a gold star. or something..

//adam

---

### Post by Bucky Ball on 2015-09-16
Plug it in, open a terminal, issue these two commands, hitting enter after each:

```
lsusb
sudo lshw -C network
```

Post the results of both commands back here between code tags thanks (see the last link in my signature).

Forget about the install disk that came with it. Usually useless to Linux users and generally means little to nothing about whether your device is supported in Linux. :)

* Just a tip for your learning curve backpack: generally a good idea to do some research on what USB wireless dongles are going to work with Ubuntu *before* buying one. :) 

Despite that, let's see how we go. If this is a very new device that has been on the market for, like, a week, it might not be well. You're generally better off with a bog standard $10 or $20 generic dongle which has been out for a year or so. The last one I bought was about $5 dollars.

---

### Post by adamftzptrck on 2015-09-16
I actually did read something like this about USB dongles, thats why I did purchase one! it was the best one I could get for 20 bucks. I'm not working on the pci express wifi adapter [here it is]("https://www.asus.com/Networking/PCEAC56/")

```

i believe the next step would be to do the similar lspci, here are those results
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port F)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 6939 (rev f1)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aad8
02:00.0 USB controller: ASMedia Technology Inc. Device 1242
03:00.0 USB controller: ASMedia Technology Inc. Device 1142
04:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

as for the  sudo lshw -C network command 
```

*-network UNCLAIMED     
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fe600000-fe607fff memory:fe400000-fe5fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: d8:cb:8a:74:41:1b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:89 ioport:d000(size=256) memory:d0304000-d0304fff memory:d0300000-d0303fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@10:2.4
       logical name: wlan0
       serial: 48:f8:b3:78:96:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.16.0-49-generic firmware=0.29 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11abgn


```


I hope I got your code tags correctly -thanks for the tip I'll try and pass that on.

---

### Post by Bucky Ball on 2015-09-16
In that case, good buy! :)

Yes, code tags correct and all good. Keeps formatting, neater and easier to read.

What you could try first is plugging the dongle in, getting online with a cable, doing an update (make sure you are online and use the Software Updater) and then check 'Additional Drivers'. Is there anything there like STA driver for wireless? If so, tick it and install it as that's what you need for that card (yes, we should be able to get this working). Wireless may pop up immediately or you may need to reboot (unplug the cable on reboot so just USB dongle in). If there is a notification you have wireless networks available, unplug the cable and connect to yours.

If that doesn't work (and if you have the STA driver it should) plug the dongle in, get online with a kernel and try the instructions for 12.04 from the top of the page [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29").

---

### Post by adamftzptrck on 2015-09-16
okay so I found the STA driver and "checked" that. I'm going to restart the computer. I have an introduction to Linux class to attend at my college I'll check back in later and let you know what I've found.

Thanks!

---

### Post by adamftzptrck on 2015-09-16
For those wondering and for the confirmation that this is solved - here is what worked for me. Thank you Bucky Ball. I should have known to check in the software updater!!! 

"What you could try first is plugging the dongle in, getting online with a  cable, doing an update (make sure you are online and use the Software  Updater) and then check 'Additional Drivers'. Is there anything there  like STA driver for wireless? If so, tick it and install it as that's  what you need for that card (yes, we should be able to get this  working). Wireless may pop up immediately or you may need to reboot  (unplug the cable on reboot so just USB dongle in). If there is a  notification you have wireless networks available, unplug the cable and  connect to yours."

---

### Post by Bucky Ball on 2015-09-16
Yea. Good news and thanks for marking thread solved. :)

See ya round the forums.

PS: Check out the wireless script link in my signature if you want to have a closer look at what's going on. A very close look! Generally though, click network icon> Edit> Wireless edit> change or check. You would set up a static IP here, for instance.

The STA driver is proprietary. Did you have 'install third-party software' unchecked when you installed? That's fine but possibly why the STA didn't install. 

Good luck and enjoy the ride.

---

