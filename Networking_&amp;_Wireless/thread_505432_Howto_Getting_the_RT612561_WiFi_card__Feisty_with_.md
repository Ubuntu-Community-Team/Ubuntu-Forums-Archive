---
title: "Howto: Getting the RT61/2561 WiFi card  Feisty with Network Manager WPA"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by menisk on 2007-07-20
I have had a wireless card with the RT61/2561 chipset for about a year. When I first installed it under Ubuntu 6.10 Edgy, it worked absolutely perfectly. Then when the upgrade to Ubuntu 7.04 fiesty happened it all went to hell. The drivers that come with fiesty were hellishly inconsistent for me and would refuse to connect to my WPA networks, not to mention the fact I couldn't use it with the brand new network manager applet. After hours of searching I only found guides using native linux driver. This guide shows you how to use the ndiswrapper module to use the windows drivers under linux with full support for the network manager applet.

First we need to remove the ndiswrapper module that comes with Ubuntu 7.04 fiesty so we can compile our own.
> sudo rmmod ndiswrapper
> sudo apt-get remove ndiswrapper-utils

Now we need to get some addition packages to compile our new ndiswrapper module.
> sudo apt-get update
> sudo apt-get install build-essential linux-headers-`uname -r`

Now we need to download the ndiswrapper source to compile
> wget [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)

We'll also need some Windows drivers to install with ndiswrapper.
> wget [http://asia.giga-byte.com/FileList/Driver/comm_wp01gs_v11.zip](http://asia.giga-byte.com/FileList/Driver/comm_wp01gs_v11.zip)

Lets extract the ndiswrapper source so we can compile
> tar -xzvf ndiswrapper-1.47.tar.gz

Time to blacklist the native drivers so that we can use ndiswapper without any issues.
> sudo su
> sudo echo blacklist rt61 >> /etc/modprobe.d/blacklist

[SIZE="5"][COLOR="Red"]REBOOT NOW[/COLOR][/SIZE]

Time to compile the ndiswrapper module and install the drivers. So lets open the terminal again.
> cd ndiswrapper-1.47

Time to remove the crumbs of the old module. (Run this until it says there is nothing to remove)
> sudo make uninstall

Now we compile the new one.
> sudo make

Install it...
> sudo make install
Go back to the home directory.
> cd ../

Into the drivers directory.
> cd GN-WP01GS/Drivers/xp2k

Now we install the drivers.
> sudo ndiswrapper -i rt61.inf

List all drivers installed in ndiswrapper, to make sure the ones we just installed appear.
> sudo ndiswrapper -l

You want an output like this...
> netrt61g : driver installed
	device (1814:0302) present (alternate driver: rt61)

It may look slightly different but something similar to that is good.

Finish installing the drivers.
> sudo ndiswrapper -m

Start the drivers
> sudo modprobe ndiswrapper

That should be it, test your wireless with the network applet. If you have any issues please post in the comments and I'll try to help you.

---

### Post by bmeyer on 2007-07-22
Thanks much for the comprehensive guide -- I was getting pretty tired of using ifup ;)

---

### Post by kevdog on 2007-07-22
I think in feisty that the serial monkey drivers need to be compiled from the latest cvs release, installed, and then everything will work as normal as it did in Edgy.  For the upcoming gusty release I think new native ra drivers are to be included.  Congrats on the ndiswrapper approach.

---

### Post by mikonro on 2007-07-23
This guide should suit my system, but I think I did some damage before.. maybe updated kernel somehow. I could see (but not use) wlans before, but now I can't anymore. They disappeared before I tried with this guide.

However all went fine until 
```

sudo ndiswrapper -i rt61.inf
driver rt61 is already installed
```
and then
```
sudo ndiswrapper -l
rt61 : invalid driver!
```

Can anyone help me?

---

### Post by menisk on 2007-07-27
mikonro sounds like you've tried to install these drivers before. You need to completely remove all the ndiswrapper folders. 

> sudo gnome-search-tool

Search ndiswrapper

Remove all the folders except the one in your home directory, assuming you still have it.

Now jump to the ndiswrapper folder in your home dir.

And follow all the directions in the guide starting with > sudo make uninstall

hope it works. :)

---

### Post by mikonro on 2007-07-29
First of all, thank you for the reply.

> **menisk said:**
> mikonro sounds like you've tried to install these drivers before. You need to completely remove all the ndiswrapper folders. 
Search ndiswrapper
Remove all the folders except the one in your home directory, assuming you still have it.
Now jump to the ndiswrapper folder in your home dir.
And follow all the directions in the guide starting with 
hope it works. :)

All the folders were in my home directory or it's subfolder. I think I'm going to re-install ubuntu. I have most likely done some damage when trying to sort this out before. And then I'll try again. I let you know how things are then. Anyway it'll take maybe a week before I can burn installion cd. My cdrom doesn't work either. :(

---

### Post by sherlockhomez on 2007-08-01
Thanks heaps for the guide, nice and easy to follow, and it worked perfectly for my system :)

---

### Post by rdtinman on 2008-03-29
With these instructions the installation went like a charm... Thanks. However, i am running from within a virtual window call virtualbox hosted by Windows Vista and trying to attach directly to my wireless adapter using the rt61 drivers and it doesn't seem to detect the device at all. The only network hardware detected are those setup during the configuration of the virtual window.

Curious if it is even possible to setup the hardware from within VirtualBox at all. Any thoughts?

---

