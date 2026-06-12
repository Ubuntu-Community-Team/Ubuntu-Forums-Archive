---
title: "WIreless card not detected - Dell Inspiron 9200"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by ubnewb on 2005-11-20
Hi,

Brand new default install.  eth0 works fine, but no detection of wlan0.  I know there is internal wireless card (I used it successfully in WinXP prior to reformatting with Ubuntu).  Any advice on how to have the internal wireless nic detected?  Thanks guys.

foo@dell9200:/var/www$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


foo@dell9200:/var/www$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device

---

### Post by Lambert on 2005-11-20
Searching looks like the chipset of your nic is an intel 2200bg which should be the ipw2200 drive.

Since you have nothing showing when you run iwconfig, that pretty much says there is no driver associated with the device currently.

Run this command 

```
sudo lshw -businfo
``` 
Look for the wireless device and notice what class it falls under.

After that type

```
sudo lshw -C <class>
``` 
Notice the configuration: line and see if it says driver=XXXX

If not then try this

```
sudo modprobe ipw2200
``` 
Try the lshw command again and see now and you can also run iwconfig if there's any output. If not then you'll probably have to use ndiswrapper with the windows drivers.

See link in my signature about ndiswrapper

If there is output and you have a driver then go into system>admin>network and enter your network info and try to activate

---

### Post by ubnewb on 2005-11-20
Hi Lambert.  Thanks for the quick and informative reply!  Running:

[INDENT]sudo lshw -businfo[/INDENT]

I see the line

[INDENT]pci@02:03.0            network        BCM4309 802.11a/b/g[/INDENT]

Then I ran:
[INDENT]
sudo lshw -C network[/INDENT]

and saw:

[INDENT]  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:faffa000-faffbfff irq:11[/INDENT]


I don't see a driver=XXXX line in that output.

I also ran:

[INDENT]sudo modprobe ipw2200[/INDENT]

which had no output and did not change the output of the lshw command.  I feel we're closer.  Any further advice?

Thanks!

---

### Post by Lambert on 2005-11-20
BCM4309 is a broadcom chipset so it's not the 2200bg like I saw in a search.

You will need to use ndiswrapper with the windows drivers. 

If you have internet access while logged into ubuntu (wired or another way) install an app called ndisgtk (if you don't know how to install then click on lifepreserver in top panel, read the 5.10 starter guide)

Click on system>admin>windows wireless drivers. Have your drivers ready and follow the prompts.

Otherwise click on link in my signature about ndiswrapper as that will guide you to installing the driver through the command line.

You can also search using ndiswrapper as key word in the forum and you'll find hundreds of posts about it.

---

### Post by msi911 on 2005-11-21
I am completely new to Linux myself but have just installed Ubuntu 5.10 on my PC. I also couldn't get my PC on the net using my wireless pci-card (Linksys WMP54GS) which has a broadcom BCM4306 802.11 b/g controller.

Following this thread and installing ndisgtk and ndiswrapper and downloading the driver from linksys' web page at [http://www1.linksys.com/international/driver.asp?coid=48&intdlid=19]("http://www1.linksys.com/international/driver.asp?coid=48&intdlid=19") actually solved the problem. It installed perfectly by going to System/Admin/Windows Wireless Drivers and just pointing to the unzipped win-drivers .inf file on my desktop.

Thanks a lot Lambert :razz:

---

### Post by Ranjan_Hegde on 2008-01-21
I followed the steps and wireless works fine but everytime I reboot I can not find wireless networks. Any Idea why. BCM driver is blacklisted and I am not sure what is going on.

blacklist bcm43xx

---

