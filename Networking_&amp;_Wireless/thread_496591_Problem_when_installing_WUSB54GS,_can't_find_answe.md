---
title: "Problem when installing WUSB54GS, can't find answer anywhere"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by MCTom on 2007-07-09
Hey I really hope someone can help here as it is really starting to become annoying.  Whenever I try to install the drivers for my WUSB54GS USB thing it says "couln't find SourceDisksFiles section - continuing anyway..." but then the driver isnt installed correctly, anyone know whats happening?  I have tried this on both normal account and root accounts and both come up with this error.  I am using ndiswrapper and have tried the guide stickied at the top of this forum.

---

### Post by MCTom on 2007-07-09
Ok, I have actually found a way to fix this now from a support post on this forum that wasnt stickied, not sure why not :S .  I now have another problem :(  the drivers say that the USB device is connected however the lights on it do not come on since I restarted the computer.  Also when I put in the netwrok details to connect it doesn't and seems to show no information that it is even trying, can anyone help with this?

Plus, shameless bump. ;)

---

### Post by kevdog on 2007-07-09
You dont happen to know the chipset of this device do you??  What method did you try to install drivers if any??
Thanks.

Please list 
lsusb

---

### Post by MCTom on 2007-07-09
I used NdisWrapper to install the drivers, they were just the basic drivers from the original CD which came with the connector, I don't know whether a more update driver would work, or maybe a different ndis version although I think I have the latest version of that.  As for the chipset it is a WUSB54GS v2 and that's all I know really :(.

---

### Post by kevdog on 2007-07-09
Can you post the following:

lsusb
lshw -C network

---

### Post by MCTom on 2007-07-09
Ok, sorry didn't notice that the first time, here they are :)

lsusb:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 13b1:0014 Linksys 
Bus 002 Device 001: ID 0000:0000  

lshw -C network:
*-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:0c:41:13:97:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfbfe000-dfbfffff irq:16
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:3b:08:bf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:dfbfd000-dfbfdfff ioport:c8c0-c8ff irq:18


That disabled thing doesn't look helpful but I can't see where to enable it.

---

### Post by t4thfavor on 2007-07-09
Isn't there a sticky that deals with that adapter? There is like 100 pages to it or something. 

I know the process may differ between revisions of the device, but it may be a good start.

Try here
[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

---

### Post by MCTom on 2007-07-09
Yeah, I've read most of it and I'm past where that guide gets to, that only deals with installing the drivers which I have now managed, the problem is that it says the device is plugged in with ndiswrapper -l but just doesn't seem to connect to the network at all and doesn't even seem to show any connecting status beyond saying 9% (I don't know whether its meant to on Ubuntu)

---

### Post by kevdog on 2007-07-09
Not that you would know what to do with the output, but notice something from the information you posted:

> configuration: broadcast=yes [COLOR="Red"]driver=bcm43xx[/COLOR] driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g

You dont want to use bcm43xx, you want ndiwrapper.

So do the following:

```
gksu gedit /etc/modprobe.d/blacklist
```

At the end of the file add the following:
```
blacklist bcm43xx
```

If after you reboot and it still doesnt work, post the following:
lshw -C network

and the two files:
/etc/network/interfaces
/etc/iftab

Thanks

---

### Post by MCTom on 2007-07-09
Hrrm, well it now doesn't seem to show the wireless device at all, this is what I got from the lshw -C network:


  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:dfbfe000-dfbfffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:3b:08:bf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:dfbfd000-dfbfdfff ioport:c8c0-c8ff irq:22


this from interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp







auto eth0

and this from iftab:
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:11:11:3b:08:bf arp 1
eth1 mac 00:0c:41:13:97:5a arp 1

---

### Post by kevdog on 2007-07-09
The problem now is that the device isnt associated with any driver at all.  Good since we blacklisted the bcm43xx driver, bad because it isnt associated with ndiswrapper.

Try the following

sudo modprobe -r ndiswrapper

Then post the following:
ndiswrapper -v 
ndiswrapper -l

Then lets try reinserting the driver
sudo depmod -a
sudo modprobe -i ndiswrapper

Please then post:
dmesg | grep ndiswrapper wlan0

Then edit for /etc/iftab file
gksu gedit /etc/iftab

Put a # sign in front of the line with eth1

Save the file.

Then please after a reboot repost
lshw -C network
/etc/iftab

I know its a pain in the butt!

---

### Post by MCTom on 2007-07-09
Ok, all done, hope I wasn't supposed to stop at these stages and wait for what next :)

ndiswrapper -v:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 


ndiswrapper -l:

wusb54gsv2 : driver installed
        device (13B1:0014) present

dmesg | grep ndiswrapper wlan0:

grep: wlan0: No such file or directory

lshw -C network:

  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:dfbfe000-dfbfffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:3b:08:bf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:dfbfd000-dfbfdfff ioport:c8c0-c8ff irq:22


/et/iftab:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:11:11:3b:08:bf arp 1
# eth1 mac 00:0c:41:13:97:5a arp 1

Thanks loads for this by the way even if you can't manage to fix it in the end :)

---

### Post by kevdog on 2007-07-09
In desperation I pulled up information from the ndiswrapper website.  Unfortunately even though this looks like it will work, you are blessed with one of those devices otherwise known as a "pain in the a$$".

Here is what I found:
   1.
      Card: Linksys WUSB54GSv2, 802.11b/g, USB 2.0

    *
      Chipset: Broadcom - BCM4320SKFBG
    *
      usbid: 13b1:0014
    *
      Driver: You can install this driver by either of the following two methods.
    *
      *Method1: The driver for this RNDIS card doesn’t include two .sys files required (usb8023k.sys and rndismpk.sys or usb8023x.sys and rndismpx.sys), as they are part of Windows installation and don’t need to be installed in Windows. However, other drivers for different cards based on RNDIS include these .sys files. One is Belkin F5D7051uk at [http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1). You can install this driver with BCMRNDIS.INF, then, copy sys files with ‘cp USB8023K.sys /etc/ndiswrapper/bcmrndis/usb8023k.sys; cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys’. You then need to inform ndiswrapper that this driver, bcmrndis, should be used for usbid of WUSB54GSv2 (13b1:0014), by executing ‘ndiswrapper -d 13b1:0014 bcmrndis’
    *
      *Method2: Used the inf file from the CD, and the .SYS files from usr5420 available at [www.usr.com](www.usr.com) [http://www.usr-emea.com/support/s-prod-template.asp?loc=unkg&prod=5420](http://www.usr-emea.com/support/s-prod-template.asp?loc=unkg&prod=5420). Used snapshot from 13/02/2006, along with the usr system files that i had to install on a windows machine to extract. Then copied the wusb54gs.inf and wusb54gsv2.inf to the folder with the sys files - the wusb54gs.inf worked seamlessly with my device on the snapshot.!
    *
      With 2.6.16 kernels and later, you also need to configure udev; see entry for USR5421 below for details.


Ok so lets try method #1.  Try downloading what they say for now.

Lets step back for a moment to get ready for the installation of different drivers
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r wusb54gsv2
Make sure the /etc/ndiswrapper directory is void of any files or directories.  If something is in the directory then issue following command:
sudo rm -R /etc/ndiswrapper/*

Get the drivers they recommend and then we can proceed to the next step!

---

### Post by MCTom on 2007-07-10
Ok so I have now done all of that and with ndiswrapper -l it shows the device and says that it is plugged in however in the 'Network' list under admin it still does not show up and the lights on the device do not light up.  The results I got from the latest 'lshw -C network' were:


 *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:dfbfe000-dfbfffff irq:11
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:3b:08:bf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:dfbfd000-dfbfdfff ioport:c8c0-c8ff irq:18

---

### Post by kevdog on 2007-07-10
If you check
dmesg
and it gives you no indication about an error with your wireless device, it might be time to jump ship with ndiswrapper and resort the the bcm43xx cutter approach.

One last attempt before I recommend this course of action

Try rebooting one last time.
After reboot, type:
cd ~
dmesg > boot.txt
sudo modprobe ndiswrapper
dmesg > probe.txt

Compare the two files.  See if anything has changed.

Then /etc/init.d/dbus restart

Then check both ifconfig and lshw -C network

Please post
/etc/modprobe.d/blacklist
sudo modinfo ndiswrapper

---

### Post by MCTom on 2007-07-10
Hrrm, this is very annoying now, I don't think that part changed anything :(  Although the section with cd and dmesg didn't seem to do anything :(.  These are the latest things

blacklist:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist rt2570
blacklist bcm43xx


sudo modinfo ndiswrapper:

filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.47
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     FA633DF63916E1784E6852C
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

after doing d.bus restart both the wired connection and the other one disappeared from the network list (wireless was never there)  but came back after I restarted.

---

### Post by kevdog on 2007-07-10
Lastly

Lets see if the ndiswrapper module is even getting loaded after booting:

lsmod | grep ndiswrapper

Mine says 
ndiswrapper 188252 0
usbcore 134280 3 ndiswrapper,uhci_hcd

BTW:
Here is a quick way to tell if any differences are seen between the boot.txt and probe.txt files
diff boot.txt probe.txt

This will only print out the differences.

---

### Post by MCTom on 2007-07-10
Well, the results I got were:

lsmod | grep ndiswrapper:

ndiswrapper           188252  0 
usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd


which looks like it is fairly similar to yours.  Also I think I did boot/probe.txt right and there seems to be no difference. :confused:

---

### Post by kevdog on 2007-07-10
Shoot -- something tells me that the driver is incorrect, but I have no way of proving or disproving this.  The only reason that I think this is so is the following:

> product: BCM4306 802.11b/g Wireless LAN Controller -- Thats what you gave me

```
Chipset: Broadcom - BCM4320SKFBG
``` -- Thats the info from the ndiswrapper website

Just to review -- I know you have tried at least two drivers - one from ndiswrapper website, and the other came with an installation CD??  or from the Linksys website??

---

### Post by MCTom on 2007-07-10
I have tried the driver from the linksys CD which came with my USB device and the belkin one which you sent me which was from the ndiswrapper website I think.  I haven't tried the latest drivers from linksys yet though, that could make a difference :)


Hrrm, I've now tried with the correct linksys drivers again, I have done everything seemingly correctly, imported the .sys files in and now ndiswrapper -l shows that the driver is installed and the usb device connected but none of the lights on it light up and it isn't shown in the Network list, man I wish I knew what was going on here :(

---

