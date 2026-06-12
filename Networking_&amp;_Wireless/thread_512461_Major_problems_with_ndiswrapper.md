---
title: "Major problems with ndiswrapper"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by davehkent on 2007-07-29
I have just loaded ubuntu 7.04 Feisty Fawn onto an old pc running windows 98, and I now have a dual-boot pc. Everything appears to be ok, except I cannot get internet access through ubuntu with my Netgear WG121 usb 2.0 wireless adapter. I have followed instructions from other posts on this site about installing ndiswrapper, but I've obviously done something wrong, so any help in clearing up the mess will be greatly appreciated.Current situation is this.....

ndiswrapper -v
module version is too old!
utils version '1.9', utils version needed by module '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586
You may need to upgrade driver and/or utils to latest version available at [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

ndiswrapper -l
ndisgtk-0.6-0ubuntu3_all.deb: invalid driver!
ndiswrapper-1.47: invalid driver!
ndiswrapper-1.47.tar.gz: invalid driver!
ndiswrapper-common_1.38-1ubuntu1_all.deb: invalid driver!
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb: invalid driver!
netwg121: invalid driver!

The Netwg121 .inf & .sys files were copied from the windows partition, if that's any help.

---

### Post by kevdog on 2007-07-29
Although it doesnt look right I think the first part of what you posted is OK -- I too get this output sometimes even though everything is working! (I compiled from source, hopefully you did also)

> ndiswrapper -v
module version is too old!
utils version '1.9', utils version needed by module '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586
You may need to upgrade driver and/or utils to latest version available at [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

I dont understand the second part of your post.  To install the driver, make sure the /etc/ndiswrapper directory is completely empty: sudo rm -R /etc/ndiswrapper/*

Then try installing the driver again:
sudo ndiswrapper ****.inf <---With sys file in same directory

If you first installed ndiswrapper from repository or somewhere else then installed from source on top, you might have problems!

---

### Post by davehkent on 2007-07-29
kevdog

Thanks for the reply. Did what you suggested, still no go.
"ndiswrapper -l" now says - netwg121: invalid driver!

I think I've done what you mentioned - I installed ndiswrapper through .deb files downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com) first, and when that didn't work I downloaded the 1.47.tar.gz file from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and tried to install it that way.

Maybe I need to clear everything off my system and start again?

---

### Post by kevdog on 2007-07-29
You cant install the source version on top of the repository version.  First run synaptic to uninstall the .deb version.  Then take a look here how to manually uninstall remnants on your system, then reinstall the source.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

### Post by davehkent on 2007-07-30
kevdog

Thanks for the reply. I'll do as you suggest and get back to you (hopefully with it working!)

---

### Post by davehkent on 2007-08-12
Kevdog

Yes, it now works! Followed the instructions about removing ndiswrapper, then reinstalled again from the 1.47.tar.gz source file, plugged the Netgear adapter in, and the lights came on!

I've now configured the network connection through my Netgear router and I am now online!

Thanks for your help

---

