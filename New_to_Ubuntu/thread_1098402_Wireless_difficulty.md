---
title: "Wireless difficulty"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by robotica on 2009-03-17
Hello, I'm brand new to Ubuntu. Everything seems to be working well, but I can't get the wireless to work. ndiswrapper has changed their site and I can't find the driver list. 

Here is some info from the terminal about my connection and drivers:

> joestudent@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:0d:b3:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.101 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=32 mingnt=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:dc:a2:a1:fb:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
joestudent@ubuntu:~$ 
joestudent@ubuntu:~$ ndiswrapper -l
lsbcmnds : driver installed
	device (14E4:4320) present (alternate driver: ssb)
joestudent@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


My wireless adapter is the Linksys Wireless-G WPC54G ver.4

My ubuntu is 8.10

I would really appreciate any help. I've been to youtube, tried searching the forums, etc. Been working on this for a couple of days and I'm out of ideas.

Thanks!

:O)

---

### Post by tariquepark on 2009-03-17
hi there,
firstly why do you have two wireless adapters? I assume one is internal and the other pcmcia or usb?
this 
joestudent@ubuntu:~$ ndiswrapper -l
lsbcmnds : driver installed
device (14E4:4320) present (alternate driver: ssb)

says that the ndiswrapper driver that is loaded is for the (assumedly) internal wireless i.e. the broadcom device not the Linksys.
If you have the windows drivers for the linksys wifi simply uninstall the broadcom driver, then install the linksys drivers and cross your fingers :)
this wiki may help if you wish to use the broadcom wifi
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

cheers luke

---

### Post by anewguy on 2009-03-17
Do you have the Windows version of the driver? If you have the .sys and inf files, you can install ndiswrapper directly off of the LiveCD you used to install Ubuntu.  It can be used straight as a source into synaptic package manager, but you can access them directly:

put the CD in the drive and close out of anything that might start up

using "places", navigate the cd to the /pool/main/n folder.

in that folder you should see 2 folders:

ndisgtk  and ndiswrapper

open the ndiswrapper folder and you should see 2 files:  ndiswrapper common and ndiswrapper utilities.  Double click on each of these files and they will install.

navigate back to the /pool/main/n folder and then to the ndisgtk folder.  You should see 1 file for ndisgtk.  Double click on it to install it (it is the gui'd front end to ndiswrapper).

you should now be able to use ndisgtk to install your driver, or you can just use ndiswrapper.  If you need specific instructions on using ndiswrapper, just post back.

EDIT: OOOPPSSS - I misread your post, you already have ndiswrapper installed - sorry.  I am also a little confused - as the previous poster mentioned you have 2 wireless devices installed - which are you trying to use?  what did you already do to attempt to load a driver for which card?


Dave :)

---

### Post by robotica on 2009-03-17
> **tariquepark said:**
> hi there,
firstly why do you have two wireless adapters? I assume one is internal and the other pcmcia or usb?
this 
joestudent@ubuntu:~$ ndiswrapper -l
lsbcmnds : driver installed
device (14E4:4320) present (alternate driver: ssb)

says that the ndiswrapper driver that is loaded is for the (assumedly) internal wireless i.e. the broadcom device not the Linksys.
If you have the windows drivers for the linksys wifi simply uninstall the broadcom driver, then install the linksys drivers and cross your fingers :)
this wiki may help if you wish to use the broadcom wifi
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

cheers luke

Yes, that's right. The internal wireless doesn't work. The linksys is the one that I use. I will check the wiki article out. Thanks for your help.
BTW, can you tell me the proper command to uninstall the broadcom?

---

### Post by robotica on 2009-03-17
> **anewguy said:**
> Do you have the Windows version of the driver? If you have the .sys and inf files, you can install ndiswrapper directly off of the LiveCD you used to install Ubuntu.  It can be used straight as a source into synaptic package manager, but you can access them directly:

put the CD in the drive and close out of anything that might start up

using "places", navigate the cd to the /pool/main/n folder.

in that folder you should see 2 folders:

ndisgtk  and ndiswrapper

open the ndiswrapper folder and you should see 2 files:  ndiswrapper common and ndiswrapper utilities.  Double click on each of these files and they will install.

navigate back to the /pool/main/n folder and then to the ndisgtk folder.  You should see 1 file for ndisgtk.  Double click on it to install it (it is the gui'd front end to ndiswrapper).

you should now be able to use ndisgtk to install your driver, or you can just use ndiswrapper.  If you need specific instructions on using ndiswrapper, just post back.

EDIT: OOOPPSSS - I misread your post, you already have ndiswrapper installed - sorry.  I am also a little confused - as the previous poster mentioned you have 2 wireless devices installed - which are you trying to use?  what did you already do to attempt to load a driver for which card?


Dave :)

Yes, one wireless is internal and doesn't work. I'm going to check the wiki article. I was checking out a video that showed how to do the whole operation, but ndiswrapper has changed their page and now I can't find the list of windows drivers. I got the linksys driver from my linksys CD, but I have no idea if it will work or is installed. 

My ubuntu is a wubi install, so I don't have a CD.

Thanks for your help. :)

---

### Post by robotica on 2009-03-17
I think maybe I just have the wrong driver. Dunno... this is a pain in the butt. :(

---

### Post by iamkrazee on 2009-03-17
jockey is the right way to go..

---

