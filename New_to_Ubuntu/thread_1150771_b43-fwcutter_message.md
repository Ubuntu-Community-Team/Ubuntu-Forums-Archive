---
title: "b43-fwcutter message"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by loren41 on 2009-05-06
I upgraded from Intrepid to Jaunty and now receive the following message when installing updates.

E: b43-fwcutter: subprocess post-installation script returned error exit status 1

This message means nothing to me.

---

### Post by andrew.46 on 2009-05-07
Hi loren41,

> **loren41 said:**
> I upgraded from Intrepid to Jaunty and now receive the following message when installing updates.
```

E: b43-fwcutter: subprocess post-installation script returned error exit status 1
```

This message means nothing to me.

'b43-fwcutter' is software that extracts firmware for broadcom wireless chips. Do you have such a wireless chip and is it working ok?

Andrew

---

### Post by albinootje on 2009-05-07
> **loren41 said:**
> 
E: b43-fwcutter: subprocess post-installation script returned error exit status 1


Can you post the output of :
```

dpkg -l|grep fwcutter

```

---

### Post by loren41 on 2009-05-09
The output follows:

loren@loren-laptop:~$ dpkg -l|grep fwcutter 
iF  b43-fwcutter          1:011-5                                  Utility for extracting Broadcom 43xx firmware
rc  bcm43xx-fwcutter      1:006-3                                  Utility for extracting Broadcom 43xx firmware

---

### Post by albinootje on 2009-05-09
> **loren41 said:**
> The output follows:

loren@loren-laptop:~$ dpkg -l|grep fwcutter 
iF  b43-fwcutter          1:011-5                                  Utility for extracting Broadcom 43xx firmware
rc  bcm43xx-fwcutter      1:006-3                                  Utility for extracting Broadcom 43xx firmware

Thanks. Can you try the following :
```

sudo apt-get update
sudo apt-get -d install b43-fwcutter
sudo dpkg -P b43-fwcutter
sudo apt-get install b43-fwcutter
sudo apt-get -f install

```

---

### Post by thenubsauce on 2009-05-10
So after all of this is done, how do I know that the driver is actually installed? Obviously I tried using my wireless, and it didn't work. When I go to system --> administration --> hardware drivers, I don't see the b43 driver. So there something else I need to do to turn it on?

---

### Post by albinootje on 2009-05-10
> **thenubsauce said:**
> So after all of this is done, how do I know that the driver is actually installed? 

The b43-fwcutter is only providing the firmware for the wifi card, and not the driver.
Perhaps you need to use Ndiswrapper to make your wifi card work, please post the output of the following here :
```

lspci
lshw -C network

```

---

### Post by thenubsauce on 2009-05-10
jay@jay-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
09:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
jay@jay-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:ec:3c:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.1.100 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:65:a4:61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:59:61:48:81:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jay@jay-laptop:~$ 


i remember that when it asked me to check for firmware, I clicked yes. I saw that it was installing something.

---

### Post by albinootje on 2009-05-11
> **thenubsauce said:**
> product: BCM4312 802.11b/g

Okay, this might help :
[http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html](http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html)

---

### Post by thenubsauce on 2009-05-11
When I go to system --> administration --> hardware devices, shouldn't Broadcom b43 show up? I've searched everywhere and I've noticed people mention it. So my problem is that I can't even see on the list.

---

### Post by albinootje on 2009-05-11
> **thenubsauce said:**
> When I go to system --> administration --> hardware devices, shouldn't Broadcom b43 show up? I've searched everywhere and I've noticed people mention it. So my problem is that I can't even see on the list.

Did you try this howto ?
[http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html](http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html)

I think that when a wifi-card depends on a setup with Ndiswrapper, then there's nothing showing up in the "Hardware Devices".

---

