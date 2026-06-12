---
title: "Useful resources for beginners setting up your wireless connection"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-29
**Basic Overview**

Wireless setup requires installation of a network driver and use of a networking tool to connect to a local network router/wireless access point.  Below are some general tips to help you setup and establish your wireless connection

**[SIZE="4"]I - Learning the basics of your Wireless Device[/SIZE]**

     Discovering the chipset of the wireless device is the first step in installation. 
     For networking cards or internal wireless devices (even those not connected to the internet or without a driver installed), at the command line type:

```
lspci -nn
```

This command lists (ls) devices connected to the pci (pci) bus (Hence the command lspci).

For USB wireless dongles, there is an equivalent lsusb command, however issuing this command does not reveal the wireless chipset of the device.  Often times you will either have to discover the chipset by either consulting the documentation that comes with the device, or googling the device to discover the chipset.

**[SIZE="4"]II - Setting up your Network Driver[/SIZE]**

      Unlike windows plug and play system were many network drivers are shipped with the operating system, ubuntu often requires installation of networking drivers.  As of 7.10 there a few open source network drivers that are "built into the operating system" -- These are the following:
      a.** Ra chipset drivers** - rt2500, rt61, rt73, rt2400, rt2570
      b. **Broadcom chipset** - the bcm43xx driver
      c.** Orinico, prism devices**
      d.** Certain Atheros chipsets** - via the madwifi drivers - consult the madwifi website directly to see if your atheros chipset is supported: [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility). 

      **Broadcom chipsets** -- in order to successfully use the built-in bcm43xx restricted driver, a working internet connection is required -- in most cases a wired connection.  Ndiswrapper is another (and in my opinion a preferred) installation method
     **Atheros chipset** - the madwifi drivers can be installed via synaptic and searching for the linux restricted package.
      **Ra chipsets **- In many cases I'm finding the built-in drivers shipped in Ubuntu 7.10 are often problematic.  If problematic, compilation and installation of the serial monkey drivers for ra based chipsets, or installation via ndiswrapper are two alternative installation methods.

      In cases where the wireless driver is not contained in contained in the default installation, or in cases where the built-in drivers do not function appropriately, drivers either need to be:
[B]     Downloaded
          Downloaded, compiled and installed from source
          Wiindows drivers installed via the ndiswrapper tool[/B]

Below is a list of posts that I have found very useful in my experience to aid users in alternative wireless driver installation.

**Ra chipsets** - rt2500, rt73, rt61, rt2570 drivers - [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey) - Author diepruis
**Rt2500 driver installation in Gusty** [http://ubuntuforums.org/showthread.php?t=584657](http://ubuntuforums.org/showthread.php?t=584657) - Author - zoiks
**Ndiswrapper installation for Broadcom chipsets** - [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) - Author Jamie Jackson
**Ndiswrapper General Installation Guide - SVN, Troubleshooting Tips (My Personal Guide)** - [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) - Author KevDog
**Madwifi website for certain Atheros Chipset**s - [http://madwifi.org/](http://madwifi.org/) -- If your Atheros chipset is listed on this website - it should work out of the box with installation of the linux restricted drivers package for your kernel version
**Realtek win98 driver** - [http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html](http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html) - For use with ndiswrapper if native r818x, r8187 driver is buggy
**Realtek win98 driver installation** - [http://ubuntuforums.org/showthread.php?t=493958&highlight=8187](http://ubuntuforums.org/showthread.php?t=493958&highlight=8187) - Author Panurge
**Realtek - Installation with Native Driver** - [http://ubuntuforums.org/showthread.php?t=567505](http://ubuntuforums.org/showthread.php?t=567505)

**[SIZE="4"]III - Using your Wireless Card[/SIZE]**

Once wireless drivers are installed, often times a wireless GUI is needed to configure the wireless device and connect to the wireless network.  

**Network Manager** is the default wireless GUI shipped by default with Ubuntu.  In some cases however network manager does not function appropriately with certain setups (ra based chipsets).  Alternatives do exist and are oftentimes necessary.  These alternatives include

     **The command line** (configuring and connecting manually) - For all chipsets
     **WICD** - For all chipsets.  For any WICD installation I recommend installing the latest testing version over the stable version
     **Rutilt** - For ra based chipsets

References:
**Connecting Wireless at the Command Line** - [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) - Author Kevdog
**Rutilt - A Network Manager Like GUI for Ra Chipsets** - [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt) - Author sulilogs
**WICD** [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

**[SIZE="4"]IV - Wireless Security[/SIZE]**

**WEP** - In most cases WEP is built-in to the wireless management GUI.  
**WPA** - For cases other than ra-based chipsets, the wpasupplicant package needs to be installed (via synaptic, apt, aptitude) prior to utilizing WPA.

**[SIZE="4"]V - Helpful Command-Line Wireless Commands[/SIZE]**

**ifconfig** - lists IP address (similar to ipconfig in Windows)
**iwlist scan** - shows wireless networks that are available in the area along with basic encryption information
**lshw -C network** - Shows interface and driver associated with each networking device
**lspci -nn** - Shows hardware connected to the pci bus
**lsusb** - Shows USB connected hardware
**lshw -C usb** - Additional info on USB related hardware (good for USB dongles)
**cat /etc/modprobe.d/blacklist** - List modules that will not be loaded by the Operating System at boot time
**lsmod** - lists currently loaded kernel modules.  (Example usage - lsmod | grep ndiswrapper)
**route -n** - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
**sudo route add default gw 192.168.1.1** - Example of how to set the default gateway to 192.168.1.1 
**sudo route del  default gw  192.168.1.1** - Example of how to delete the default gateway setting
**sudo modprobe ******* - Loads the kernel module **** .  (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
**sudo modprobe -r ****** - Unloades the kernel module ****.  (Example usage - sudo modprobe -r ndiswrapper)
**sudo ifup/ifdown <interface>** - Brings up/down the interface and clears the routing table for the specified interface
**sudo ifconfig <interface> up/down** - Brings up/down the interface for the specified interface 
**sudo dhclient <interface>** - Request IP address from DNS server for specified interface
**sudo dhclient -r <interface>** - Release IP address associated with specified interface
**sudo iptables -L** - Lists firewall rules 
**dmesg | more** - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
**uname -r** - Displays kernel version
**/etc/iftab (Feisty and pre-releases (Edgy, etc)) -  /etc/udev/rules.d/70-persistent-net.rules (Gutsy)** - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
**cat /etc/resolv.conf** - Lists DNS servers associated with network connections (Network Manager)
**/etc/dhcp3/dhclient.conf** - File which sets or modifies dns (domain name servers) settings

**[SIZE="4"]VI- Other Useful Guides[/SIZE]**

**DNS related problems?? - Configuration for OpenDNS servers** - [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) - Author noob12
**Turn off/Disable IPv6** - [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) - Author mark
**Quit Having Network Manager asking for a Password to Connect to Known Wireless Networks** - [http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=8](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=8) - Author Blueshift

---

### Post by Lambert on 2007-10-30
You put a decent amount of time writing these helpful posts. Have you considered contributing this info to the help site?

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Posts get buried and the search function can be difficult in the forum. The wifidocs section gives a central location to find help.

---

### Post by kevdog on 2007-10-30
No I didnt know about this site.  I think that may be part of the problem.  A lot of the same questions are asked over and over again.  It seems in my opinion a lot of new users come to the forums, DO NOT do an exhaustive search about their problems, and then post many of the same questions.  The stickies at the top of the networking section while they are good, are far too specific for beginners and the moderators hardly ever change them.  I have no idea how many users actually read the documentation since Ive rarely seen people say, "I read this in the wiki documentation, however I tried this and it doesnt work".  Ubuntu is great, but the documentation is poorly organized.  There are a bunch of useful posts in the forums but they are buried.  Ive tried to compile a list that seems useful in my opinion from often visiting these forums, however I know the list is not exhaustive.  Perhaps right now Id like it for people to keep submitting posts that they think they are helpful, so I can add them to the list.  Im really on the look out for general re-occuring topics (ndiswrapper, ipv6, routing, network bonding), or specifically feisty and gusty posts for various networking cards.  Useful hardware solution problems (acer laptops for example) could also be included.

Im open to any ideas you have.

---

### Post by JoJerome on 2007-10-31
Way useful - thanks!

Now that I've got my friend's laptop up and running I'm bookmarking this page for him in case he runs into any more trouble. 

And bookmarking it for myself, for that beautiful day when I can afford a lappy of my own. :KS

- Jo

---

### Post by Lambert on 2007-11-03
> **kevdog said:**
> No I didnt know about this site.  I think that may be part of the problem.  A lot of the same questions are asked over and over again.  It seems in my opinion a lot of new users come to the forums, DO NOT do an exhaustive search about their problems, and then post many of the same questions.  The stickies at the top of the networking section while they are good, are far too specific for beginners and the moderators hardly ever change them.  I have no idea how many users actually read the documentation since Ive rarely seen people say, "I read this in the wiki documentation, however I tried this and it doesnt work".  Ubuntu is great, but the documentation is poorly organized.  There are a bunch of useful posts in the forums but they are buried.  Ive tried to compile a list that seems useful in my opinion from often visiting these forums, however I know the list is not exhaustive.  Perhaps right now Id like it for people to keep submitting posts that they think they are helpful, so I can add them to the list.  Im really on the look out for general re-occuring topics (ndiswrapper, ipv6, routing, network bonding), or specifically feisty and gusty posts for various networking cards.  Useful hardware solution problems (acer laptops for example) could also be included.

Im open to any ideas you have.

You nailed it with poorly organized. There's a lot of information out there and most of it is fragmented or overwhelming, or detailed, hard to find. A couple years back I was working on a wiki setting up a foundation to work from and things pulled me away  from continuing. That data was lost. I'd be willing to work/collaborate on setting up an organized foundation that can be built off of to gather all networking information into a single place. I'm going to start putting down an outline of my thoughts and will come back later to show where my mind is wandering.

---

