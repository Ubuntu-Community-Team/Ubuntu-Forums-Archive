---
title: "Driver for Dell Truemobile 1300 USB Wirless Adaptor"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by IBUA on 2008-11-18
Hey,

This will be my last post as if no-one will/can help ill assume it just won't work at all.

Basically recently i downloaded Ubuntu 8.04 onto my Dell computer (By dual booting) planning to upgrade it to ubuntu studio.

Problem is i had no internet, as my Dell Truemobile 1300 USB Wirless adaptor doesn't seem to be configured or something.

After lots and lots of searching and reading through threads and guides from other sources i still have not found anything even remotely helpful.

This has all been very very irritating and i'm starting to lose my faith in Linux, even though everything that has worked has been brilliant.

The closest thing i've got to is that i think that it's got to do with something that the drivers (possbily) is not the right one.

I downloaded NDISWRAPPER and so on, but this didn't work, even after i found a driver which was listed on the wiki, (it said BCM43xx, which for mine i think was BCM4306, but i couldn't find this driver so i attempted to use BCMWL5 which i'd read was the update) but this didn't work either.

I think it's mostly do with the driver not the right one meaning the USB wirless adaptor doesn't work... but i can't find anymore information from there onwards on what to do.

Here is some of the information from commands i was told to give on a previous post (but then got no further):

Code:

FROM COMMAND:  LSUSB



james@james-desktop:~$ lsusb

Bus 004 Device 006: ID 13fe:1f00 Kingston Technology Company Inc. 

Bus 004 Device 005: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk

Bus 004 Device 004: ID 413c:8102 Dell Computer Corp. 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

Bus 001 Device 003: ID 046d:0920 Logitech, Inc. QuickCam Express

Bus 001 Device 001: ID 0000:0000  




FROM COMMAND: IWCONFIG



james@james-desktop:~$ iwconfig


lo        no wireless extensions.


eth0      no wireless extensions.

Also the command: ndiswrapper -l
Said the drivers above (BCMwl5 and BCMwl5a) was installed, but didn't say anything about a device anywhere.

Basically these are my questions:
1. Is the wrong driver the most likely/right problem?
2. If yes could someone please head me in the right direction to sort this?
3. If not what could be the problem?


PLEASE help... i'm getting very frustrated,

Thanks for the help in advance!

---

### Post by Ayuthia on 2008-11-18
> **IBUA said:**
> Hey,

This will be my last post as if no-one will/can help ill assume it just won't work at all.

Basically recently i downloaded Ubuntu 8.04 onto my Dell computer (By dual booting) planning to upgrade it to ubuntu studio.

Problem is i had no internet, as my Dell Truemobile 1300 USB Wirless adaptor doesn't seem to be configured or something.

After lots and lots of searching and reading through threads and guides from other sources i still have not found anything even remotely helpful.

This has all been very very irritating and i'm starting to lose my faith in Linux, even though everything that has worked has been brilliant.

The closest thing i've got to is that i think that it's got to do with something that the drivers (possbily) is not the right one.

I downloaded NDISWRAPPER and so on, but this didn't work, even after i found a driver which was listed on the wiki, (it said BCM43xx, which for mine i think was BCM4306, but i couldn't find this driver so i attempted to use BCMWL5 which i'd read was the update) but this didn't work either.

I think it's mostly do with the driver not the right one meaning the USB wirless adaptor doesn't work... but i can't find anymore information from there onwards on what to do.

Here is some of the information from commands i was told to give on a previous post (but then got no further):

Code:

FROM COMMAND:  LSUSB



james@james-desktop:~$ lsusb

Bus 004 Device 006: ID 13fe:1f00 Kingston Technology Company Inc. 

Bus 004 Device 005: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk

Bus 004 Device 004: ID 413c:8102 Dell Computer Corp. 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

Bus 001 Device 003: ID 046d:0920 Logitech, Inc. QuickCam Express

Bus 001 Device 001: ID 0000:0000  




FROM COMMAND: IWCONFIG



james@james-desktop:~$ iwconfig


lo        no wireless extensions.


eth0      no wireless extensions.

Also the command: ndiswrapper -l
Said the drivers above (BCMwl5 and BCMwl5a) was installed, but didn't say anything about a device anywhere.

Basically these are my questions:
1. Is the wrong driver the most likely/right problem?
2. If yes could someone please head me in the right direction to sort this?
3. If not what could be the problem?


PLEASE help... i'm getting very frustrated,

Thanks for the help in advance!

If it is a 4306 chip, you might try the rndis driver.  Here is a link that might help:
[http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

It might be easier to try Intrepid to see if it works there.  It sounds like the rndis driver works out of the box in 2.6.27 (the Intrepid kernel).

---

### Post by opt1k on 2009-02-13
heres the answer. its a prism54 device. the linux driver included with the kernel does not work although it detects it??

---update-- i just found you can use synaptic package manager to install a package called ndisgtk where you can install and remove the drivers from a gui in your menu-- system/administration/windows wireless drivers

open terminal

$ sudo apt-get install ndiswrapper
download the attachment from this post to your desktop

"DellTruemobile1300WirelessUSB-Linux.tar.gz"

in terminal
$ cd ~/Desktop
$ tar xvzf DellTruemobile1300WirelessUSB-Linux.tar.gz
$ cd DellTruemobile1300WirelessUSB-Linux
$ sudo ndiswrapper -i oem15.inf
$ sudo modprobe ndiswrapper
$ sudo nano -w /etc/modules
at the end of the file put ndiswrapper. it should resemble:::

----------------
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper

----------------

lights should now come on your usb adapter and you shoudl be able to connect to the wireless network.

notes:
I got the inf file from my windows/inf folder. i could not find a way to extract the driver from the dell provided installation.



----------
DMESG
---
[  144.312417] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  144.452240] usb 3-4: reset high speed USB device using ehci_hcd and address 3
[  144.621385] ndiswrapper: driver oem15 (Dell,11/11/2003, 1.0.5.0) loaded
[  146.419971] wlan0: ethernet device 00:90:4b:72:3c:e3 using NDIS driver: oem15, version: 0x10005, NDIS version: 0x501, vendor: 'Dell TrueMobile 1300 USB2.0 WLAN Card', 413C:8102.F.conf
[  146.420010] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  146.420045] usbcore: registered new interface driver ndiswrapper
[  158.675723] NET: Registered protocol family 17
[  160.243884] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   96.936775] wlan0: no IPv6 routers present
[ 2478.212005] cdrom: This disc doesn't have any tracks I recognize!
[21934.998836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21948.641201] wlan0: no IPv6 routers present
----

---

### Post by h0wc0m3 on 2012-02-01
Thank you so very much for laying this out.

I know the thread is old, but I just got some real use out of this on my fresh install of Ubuntu 11.10

I will add only that I also made use of this page: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Cheers! :D

---

