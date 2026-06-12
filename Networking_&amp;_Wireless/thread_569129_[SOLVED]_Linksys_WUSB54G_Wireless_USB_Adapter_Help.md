---
title: "[SOLVED] Linksys WUSB54G Wireless USB Adapter Help"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by wbrady4927 on 2007-10-06
I have a Linksys WUSB54G v2 wireless USB adapter and I am running the latest version of Gutsy. I tried to install ndiswrapper, but I ran into installation problems on the very first step. Is that the best way to make my wireless USB adapter work? Is that even a possible solution to making it work?

I am using the installation instructions for ndiswrapper from [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")

If so, here is what I did to run into my error while installing ndiswrapper:
1. I downloaded and installed the latest version of ndiswrapper (which is version 1.48). I extracted the ndiswrapper-1.48/ folder to my home folder.
2. I then ran *make distclean* (which was the first command I was instructed to run) from the ndiswrapper-1.48/ directory and it gave me the following error:

make -C driver clean
make[1]: Entering directory `/home/wbrady/ndiswrapper-1.48/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.22-13-rt/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/wbrady/ndiswrapper-1.48/driver'
make: *** [clean] Error 2


If anybody has any solutions please PLEASE let me know.
All ideas are welcomed

---

### Post by Lambert on 2007-10-07
> **wbrady4927 said:**
> I have a Linksys WUSB54G v2 wireless USB adapter and I am running the latest version of Gutsy. I tried to install ndiswrapper, but I ran into installation problems on the very first step. Is that the best way to make my wireless USB adapter work? Is that even a possible solution to making it work?

I am using the installation instructions for ndiswrapper from [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")

If so, here is what I did to run into my error while installing ndiswrapper:
1. I downloaded and installed the latest version of ndiswrapper (which is version 1.48). I extracted the ndiswrapper-1.48/ folder to my home folder.
2. I then ran *make distclean* (which was the first command I was instructed to run) from the ndiswrapper-1.48/ directory and it gave me the following error:

make -C driver clean
make[1]: Entering directory `/home/wbrady/ndiswrapper-1.48/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.22-13-rt/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/wbrady/ndiswrapper-1.48/driver'
make: *** [clean] Error 2


If anybody has any solutions please PLEASE let me know.
All ideas are welcomed

Before trying to compile latest version of ndiswrapper, did you install the packages build-essential and kernel-headers?

Also post output of this command, curious what chipset is in v2

```

sudo lshw -C bus

```

---

### Post by wbrady4927 on 2007-10-07
I see that I did not have build-essential installed. I did have the linux-headers installed. I got ndiswrapper to work using the graphical tool. The only problem I REALLY have right now is that whenever I turn on my computer it does not automatically have my wireless usb adapter listed as a connection under network settings. Although, when I open up the GUI of ndiswrapper it shows that I still have the correct driver installed and that the hardware is present. If I remove that driver and re-install it again then the wireless usb adapter shows up as a connection in my network settings. 

Do you know how to set it up so that it automatically detects my wireless usb adapter when I turn on the computer and tries to connect to my wireless network??

Here is the output of *sudo lshw -C bus*:

 *-core                  
       description: Motherboard
       product: Kelut
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 2.02
       serial: MB-1234567890
       slot: LPT1
  *-firewire
       description: FireWire (IEEE 1394)
       product: IEEE 1394 Host Controller
       vendor: VIA Technologies, Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm ohci bus_master cap_list
       configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
  *-ide:0
       description: IDE Channel 0
       physical id: 0
       bus info: ide@0
       logical name: ide0
       clock: 33MHz
  *-ide:1
       description: IDE Channel 1
       physical id: 1
       bus info: ide@1
       logical name: ide1
       clock: 33MHz
  *-usb:0
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:1
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:2
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:3
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.3
       bus info: pci@0000:00:10.3
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:4
       description: USB Controller
       product: USB 2.0
       vendor: VIA Technologies, Inc.
       physical id: 10.4
       bus info: pci@0000:00:10.4
       version: 86
       width: 32 bits
       clock: 33MHz
       capabilities: pm ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=32 module=ehci_hcd

---

### Post by Lambert on 2007-10-07
See section 3.7 from the following page about auto loading at start up

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-14c464a0166a533357d567f6d8be44384b8f5c70](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-14c464a0166a533357d567f6d8be44384b8f5c70)

---

### Post by wbrady4927 on 2007-10-07
It seems to be working smoothly.

Thank you very much!

I will post a reply if I run into any more problems

---

