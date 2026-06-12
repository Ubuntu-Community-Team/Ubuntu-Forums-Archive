---
title: "wireless no show"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by nnjond on 2009-01-12
Hi, can anyone help me please?

I have installed Ibex on a new laptop but it hasn,t detected any of the wireless networks that showup in my  vicinity?

Sorry I can't remember the command that delivers all the relevant info on the laptop?

---

### Post by anewguy on 2009-01-12
If it's an internal wireless card, post back the output of:

lspci


Also, please post back the output of:

sudo lshw -C network


That will give us a little more info to look at.

Thanks!
Dave :)

---

### Post by Michael.Godawski on 2009-01-12
hi,

here are some basic commands which should give us some details about your network status:
```

sudo iwlist scan
iwconfig
sudo lshw -C network
```

---

### Post by SteveNorman on 2009-01-12
In addition to anewguy's stuff,,have you connected to a wired lan successfully? what type of computer? acer aspire is the one I use. My understanding is that the driver for your wifi card will probably have to be installed by you since no proprietary drivers come with the install. I would google: " your computer type + 8.10 ubuntu" to find tutorials for post-install configurations. They will be different from one type to another. For instance on mine I found this to be spot on for my acer:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

plus do a "things to do after installing 8.10 ubuntu" search and look through those.

---

### Post by nnjond on 2009-01-12
THanks to everyone/

nnjond@nnjond-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
nnjond@nnjond-laptop:~$ sudo lshw -C network
[sudo] password for nnjond: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6b:c2:9d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.65 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:d6:ae:9c:e9:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
nnjond@nnjond-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

nnjond@nnjond-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

nnjond@nnjond-laptop:~$

---

### Post by SteveNorman on 2009-01-12
Im not seeing a wireless adaptor, what brand of laptop? did you build it?

---

### Post by nnjond on 2009-01-12
Not Sure what you mean?  Am running this laptop from a telephone line at the moment. But as it has a dual boot with Vista i can see it detects networks in the vinicity and I want access the to the net in ubuntu when i'm on the move.

---

### Post by anewguy on 2009-01-13
Well, the output from what we asked you to do indicates that Ubuntu doesn't even detect your wireless adapter.  Based on that information, we need to know the following additional information in our quest to try to help:

- what brand/model is the laptop?

- is the wireless adapter built into the laptop, or is it either PCMCIA or USB?  What brand/model?

- if USB, please post back the following (with the adapter plugged in)

lsusb


Hopefully that will give us more information to work with.  Right now, not knowing what the adapter is, we can't do much.

Dave :)

---

