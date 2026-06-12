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

(You will need the kernel source here, and make a build environment.  I'll update this later)

Now you can make the file
  $ make
and I forwent using 'make install' in favor of replacing the driver myself
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

### Post by BliND123 on 2006-11-21
Hey, I just bought this adapter and was trying to install it with your instructions in the terminal (Ctrl-Alt-F1)...I got to the part where it says $ make and I get "command not found"...what am I supposed to do?  I was thinking maybe I had to get out of the zd1211-driver-r83 directory but same command not found.

---

### Post by FrodoB on 2006-11-21
Detailed instructions for using the native drivers:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by BliND123 on 2006-11-21
Thanks for the link....now the make command worked but after I put the `sudo make both` command this stuff showed up 

```

....(buncha stuff before this)
make -C /lib/modules/2.6.15-26-powerpc/build SUBDIRS=/home/blind/zd1211-driver-r83 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-powepc/build: No such file or directory. Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/blind/zd1211-driver-r83`
make: *** [both] Error 2

```

The link says I might get warnings, but should'nt get errors...so what is wrong?

---

### Post by FrodoB on 2006-11-21
Looks like you new headers are not linked into the /lib/modules directory somehow. Carefully go through all of step 2.

---

### Post by BliND123 on 2006-11-21
Oh, I see, I think I might have skipped the second half of step 2 :P.  Looks like the first half of step 5 is working now.

Edit: Its done, I see it in Network-Admin, I just set it up but I noticed I have my router with WPA security, the settings in linux ask for WEP.  I put in WPA key anyways and it doesn't work...so I go to router settings and turn off security just to try it and it still doesn't work...It is detecting network I think because my routers ESSID was in there already in the drop down list settings.

---

### Post by BliND123 on 2006-11-21
I changed all the settings I needed to get this working (in the network-admin, and my router)but I still cant get a connection on it.

Edit:  Figured it out. Seems my WF748-CUI is set to B mode... :P Had router for only G...is there some way to get it to do G?  Or is it B because its on my Lombard (which the USB connections are supposed to be 1.1, right?).  Should still get enough range, right?

---

### Post by samsonee on 2007-04-04
I am a newbie in linux. I am trying to install the driver for my Gigafast WF748-CUI USB Wireless Adapter. I am using the guide at:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

It works fine for the first 5 steps, but when I Insert my usb wireless adapter into a usb connector on my machine, the computer does not seem to recognize it as a wlan device. When I type iwconfig, it gives me the following:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

I also checked use lsusb, it shows the following:

Bus 001 Device 006: ID 0457:0163 Silicon Integrated Systems Corp.
Bus 001 Device 001: ID 0000:0000

anyone can help? Thanks.

---

### Post by awiggin on 2007-04-09
I have been following the directions from the link above.  However, when I get to step 2, where it says:

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  

I get the following response:

E:  Couldn't find package linux-headers-uname-r



So - going on with the other steps doesn't work since I am bogged down at this step.

Please help!  My wife is tired of having CAT5 wire strung across my bedroom.

---

