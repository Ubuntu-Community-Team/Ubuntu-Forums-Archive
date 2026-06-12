---
title: "Not sure the instructions on sticky pertain"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by bower on 2008-03-17
I just downloaded and installed Ubunta.  i have the rt2561/rt61.  the issue may be different than what the sticky suggests.  it seems to accept the card it shows mine and close by wireless networks but when i put in the wep key it thinks for awhile then asks me for the key again.  i have toyed with the options but it just wont link up.  do i need to follow the instructions on the sticky of manually installing the driver and not use network manager or is it something all together different.  i am brand new to linux so please help and clear on instructions if you can.  thank you to all of  you for your help. Bower

---

### Post by bower on 2008-03-17
this is bower again i forgot i only have internet on a windows xp machine.  thanks again

---

### Post by uberlube on 2008-03-17
This seems to be a recurring problem with some cards. You need to manually connect to your router via the command line. I'm not sure how to do this myself as I have never had to but if you do some searching around in the threads on this subject, you will find your answer. I remember reading about how to do it recently in the wireless section so it shouldnt be too hard to find.

---

### Post by uberlube on 2008-03-17
Try what buddy did in this thread:

[http://ubuntuforums.org/showthread.php?t=698785](http://ubuntuforums.org/showthread.php?t=698785)

---

### Post by bower on 2008-03-17
I followed the instructios in the sticky titled Sticky:  HOWTO: RT2500, etc. wireless cards

now my network monitor which is on the top right of top tool bar does not show any of the wireless networks like it did before i ran the commands in this post.  only manual and enable network.  i plugged everything in the manual window but to no avail.  also before  the icon on tool bar would light part way and try and conect.  any help would gladly received.

thank you   bower

below is what i did







 HOWTO: RT2500, etc. wireless cards
Dapper Drake users should take a look at this thread if this one doesn't work.
--
Please post to this Launchpad bug report with all of your specs, if you have problems with a Ralink based wireless adapter.

This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either Network Manager or WICD).

INSTRUCTIONS:

    * Get the latest version of the Windows driver for your card from Linksys' website or from the CD that came with your device (whatever vendor).

    * Install "ndiswrapper" package with working internet connection (Ethernet):
      Quote:
      sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

    * Install "ndiswrapper" package without working internet connection (alternatively, install it via Synaptic/Adept):
      Quote:
      sudo apt-cdrom add
      sudo apt-get update
      sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

    * Load new driver module (may not be necessary any longer, but does no harm either):
      Quote:
      sudo depmod -a
      sudo modprobe ndiswrapper

    * Add the module to "/etc/modules" to have it load automatically:
      Quote:
      echo 'ndiswrapper' | sudo tee -a /etc/modules

    * Create alias directive:
      Quote:
      sudo ndiswrapper -m

    * Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):
      Quote:
      rt2500usb
      rt2500pci
      rt2500
      rt2570
      rt73usb
      rt73pci
      rt73
      rt61usb
      rt61pci
      rt61
      rt2x00usb
      rt2x00lib

    * Blacklist Ralink driver:
      Quote:
      echo 'blacklist <your_ralink_driver>' | sudo tee -a /etc/modprobe.d/blacklist

    * Now unzip the driver archive you have just downloaded (e.g. in your home directory):
      Quote:
      unzip <driver_archive>.exe

    * Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):
      Quote:
      sudo ndiswrapper -i <your_ralink_driver>.inf

    * Make sure it has installed correctly:
      Quote:
      ndiswrapper -l

    * The output should yield something like this:
      Quote:
      rt2500usb : driver installed
      device (13B1:000D) present (alternate driver: rt2500usb)

    * Last but not least open this file...
      Quote:
      sudo gedit /etc/network/interfaces

    * ...and add these 2 lines if they are not there yet [also try without adding them if Network Manager does not pick up the card & reboot]:
      Quote:
      auto wlan0
      iface wlan0 inet dhcp

You can now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.).

Feedback is - as always - appreciated.

CHANGE LOG:
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.
07/11/2007: Bug fix for Network Manager.
12/11/2007: Updated blacklist & module section.
13/01/2008: Launchpad bug report.
__________________
How secure is WEP?
Need to back up your files?
Trouble with Ralink wireless adapter?
Need to secure your wireless network with WPA?
Last edited by wieman01 : January 13th, 2008 at 12:18 PM.
Thanks Reply With Quote

---

### Post by wieman01 on 2008-03-18
Please post:
> sudo iwlist scan
> sudo lshw -C network
> sudo ndiswrapper -l
> sudo cat /etc/network/interfaces

---

### Post by bower on 2008-03-18
Here is what you requested.




I had the network set up for manual and had the static ip set to what I thought to be the right ip address and this first command worked but the network did not work.  now it is on roaming, the network says it is connected at 83% but no internet and it keeps asking for the wep key.



travis@travis:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 
 
travis@travis:~$ 


travis@travis:~$ sudo lshw -C network 
  *-network:0 DISABLED     
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 6 
       bus info: pci@0000:05:06.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:1a:70:ac:62:eb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 9 
       bus info: pci@0000:05:09.0 
       logical name: eth0 
       version: 10 
       serial: 00:1b:fc:1f:77:06 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
travis@travis:~$  


travis@travis:~$ sudo ndiswrapper -l 
rt61 : invalid driver! 
travis@travis:~$  



travis@travis:~$ sudo cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
travis@travis:~$

---

### Post by wieman01 on 2008-03-18
Number one, you have probably blacklisted the wrong driver. Blacklist this one:
> rt61pci
Second you have also deployed the wrong driver:
> rt61 : invalid driver! 
What version of Ubuntu are you on (32-bit or 64-bit) and where did you get the driver from? Could you include a link?

---

### Post by bower on 2008-03-18
I think your right, i black listed the wrong driver, i also black listed  rt61.inf.  with the inf after the dot  could that be the issue

I  have 64 bit ubunta from their web site a couple days ago.  the driver for the  card for windows came from the installation disk and ndiswrapper came from ubuntu dvd i burned a couple days ago.

thanks,

Bower

---

### Post by wieman01 on 2008-03-18
> **bower said:**
> I think your right, i black listed the wrong driver, i also black listed  rt61.inf.  with the inf after the dot  could that be the issue

I  have 64 bit ubunta from their web site a couple days ago.  the driver for the  card for windows came from the installation disk and ndiswrapper came from ubuntu dvd i burned a couple days ago.

thanks,

Bower
So you are on 64-bit then... Mmm... you also need to install the 64-bit version of the Windows driver. I somehow doubt it is on the installation CD. Could you get hold of the latest version from the vendor's website? The 32-bit version won't work.

---

