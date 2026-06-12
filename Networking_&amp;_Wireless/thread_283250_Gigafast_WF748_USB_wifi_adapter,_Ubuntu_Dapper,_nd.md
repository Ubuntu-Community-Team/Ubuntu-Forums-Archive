---
title: "Gigafast WF748 USB wifi adapter, Ubuntu Dapper, ndiswrapper \ HOWTO"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by jeremynd01 on 2006-10-23
This is a quick HOWTO on getting the Gigafast WF748-CUI USB2.0 wifi b/g adapter to work in Ubuntu Dapper using ndiswrapper.  I tried a number of the zd1211 drivers and none of them worked (more info on this below), and ONLY the -b driver (zd1211b, that is) worked, as did ndiswrapper.

**[SIZE="4"]Installing the WF748 using the zd1211b driver[/SIZE]**
Ubuntu comes with a driver, zd1211.ko, which didn't work for me at all.  It  would load, but it wouldn't associate with the adapter.  So you have to go get the source and compile it.  I used the driver found at [http://zd1211.ath.cx/](http://zd1211.ath.cx/).  Note that there are two drivers there: the zd1211 driver and the zd1211rw.  The -rw is the rewrite project for the kernel (i.e. the one that comes with Ubuntu and doesn't work).  Get the other one.  I got release r83.

Untar the file and enter the directory
  $ tar zxvf zd1211-driver-r83.tgz
  $ cd zd1211-driver-r83
We have to modify the Makefile to reflect the kernel version and location, as well as to make the zd1211b module.
  $ sudo vim Makefile
The following lines should be present:
  KERN_26=y
  KERNEL_SOURCE=/usr/src/linux
  ZD1211REV_B=1         #default is 0, if present

Now you can make the file
  $ make
and I forwent using make install in favor of replacing the driver myself
  $ sudo cp zd1211b.ko /lib/modules/`uname r`/kernel/driver/usb/net/
  $ sudo depmod -a
The second command will update the driver database.  Now we can load up the driver
  $ sudo modprobe -v zd1211b
If the driver is not found or fails, go back to the beginning and figure out what you missed!  This should allow you to bring up the card
  $ sudo ifup wlan0


**[SIZE="4"]Installing the WF748 with ndiswrapper[/SIZE]**
First, we need to get the ndiswrapper-utils (this assumes you've updated your /etc/apt/sources.list, as any Ubuntu starter guide will tell you)
  $ sudo apt-get install ndiswrapper-utils

Next, configure ndiswrapper to use a windows driver for the adapter.  I used the driver from the CD it came with (<cdrom>/Drivers/Windows_XP/).  In particular, I used the zd1211b (note the 'B') driver, after sticking the adapter in a windoze box and seeing what it wanted.  If you need to get the driver off the 'net, you'll find it at [http://www.gigafast.com/products/product_drivers/WF748-UI_drivers.htm](http://www.gigafast.com/products/product_drivers/WF748-UI_drivers.htm).
  Change directory to the one containing the driver
  $ sudo ndiswrapper -i ZD1211BU.INF
My driver was in all caps - yours may differ.  Check to see if that worked:
  $ ndiswrapper -l
  Installed ndis drivers
  zd1211b                driver present, hardware present
And you can load it up
  $ sudo modprobe ndiswrapper

Hopefully, you see this message.  If you don't, then something is amiss, and you should check the logs ($ dmesg |less) to see if something particular is to blame.

Now we can load it up at boot
  $ sudo ndiswrapper -m
  $ echo ndiswrapper | sudo tee -a /etc/modules

Finally, we need to configure the card.
  $ ifconfig -a
will list all of the available adapters, even if they're not active.  If it is there, start it up with
  $ sudo ifup wlan0
And you can add the following lines into Ubuntu's network startup script
  $ sudo vim /etc/network/interfaces
  auto wlan0
  iface wlan0 inet dhcp


**[SIZE="4"]About the zd1211 drivers[/SIZE]**
If this doesn't work for you, then here's what I found out about the zd1211 drivers.

The driver that comes with linux is the zd1211rw driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/).  It is a rewrite of the original open source driver to be compliant with kernel standards.

The open source zd1211 driver can also be found at [http://zd1211.ath.cx/](http://zd1211.ath.cx/).  If you get this, expect that you may have to modify the Makefile to indicate the correct kernel, its location, and whether or not to compile the -b driver.  I don't know much about the origin of the -b driver, except it works for me!

The 'original' ZyDAS driver is available from [http://www.atheros.com/RD/downloads/download_ZD1211.htm](http://www.atheros.com/RD/downloads/download_ZD1211.htm), as Atheros bought out ZyDAS.  There are two available: version 2.6.x.x is the standard driver and 2.15.x.x, which is the -b driver.  I actually tried both, and neither worked for me.

---

