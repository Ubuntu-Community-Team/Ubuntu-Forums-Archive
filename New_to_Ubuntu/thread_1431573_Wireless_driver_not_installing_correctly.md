---
title: "Wireless driver not installing correctly?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by karasuman on 2010-03-16
I just bought a new laptop and installed Karmic on it.  I can't seem to get a wireless connection, though.  

First of all, when I right-click on the network icon, there is no option to enable wireless.  So I followed the instructions in the help file, and it doesn't look like my wireless card is being recognized:

```
beth@grumpy-laptop:~/Downloads/R239087$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:24:78:78
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.45 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:33 ioport:3000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

```

I checked the details from when I ordered the laptop, and it looks like my wireless card is listed as "Dell Wireless 1397 802.11g Half Mini Card."

I followed the instructions at [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper"), but the process breaks down...

```
beth@grumpy-laptop:~/Downloads/R239087$ ndiswrapper -l
bcmwl6 : invalid driver!

```

I notice that after downloading the file(s) and unzipping them, the only .inf files are at the path .../R239087/DRIVER_US/ instead of simply in the main driver folder as the wiki implies.

---

### Post by albert s on 2010-03-16
if I am correct and you have a broadcom chipset then it may be cured by simply hard wiring to the internet,
mine was cured that way as soon as my laptop had the updates required it was simply plug and play so to speak.

---

### Post by exodus_ on 2010-03-16
Hello there,

The previous poster is right.. if you can get a hard-wired ethernet connection going, simply going to System > Administration > Hardware Drivers and enabling the "Broadcom STA Wireless Driver" should do the trick.. You're on the same chipset as I am for wireless, and it works very well once the driver is installed.

That being said, if for some reason you can't connect via ethernet, you can still manually install the driver.  I have to do this because the ethernet adapter in my notebook is fried.  Hopefully though you can just connect with the ethernet adapter, and install the driver.  It's really easy once you know where to go.

Post back to let us know how it goes :)

I hope this is of some help to you!

---

### Post by wojox on 2010-03-16
I've got the product: BCM4312 802.11b/g. I installed:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

Then unplug your Ethernet cable and reboot and when it loads click the nm-applet and choose you Wireless Network.

---

### Post by 2hot6ft2 on 2010-03-16
If the previous suggestions don't get it working there is a thread for your card which is a Broadcom BCM4312 here:
[**[SOLVED] The Definitive 9.10 Broadcom Solution Guide**]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by karasuman on 2010-03-16
Thank you all for your help!  I love how friendly the Ubuntu community is.  :)

Simply updating did not fix the problem, but the solution of using the hardware drivers tool did.  Works like a charm!

---

### Post by exodus_ on 2010-03-16
> **karasuman said:**
> Thank you all for your help!  I love how friendly the Ubuntu community is.  :)

Simply updating did not fix the problem, but the solution of using the hardware drivers tool did.  Works like a charm!

Hey again!

I'm glad we were able to help you out with that!  I hope you have fun with ubuntu, it's quite a nice distro :)

---

