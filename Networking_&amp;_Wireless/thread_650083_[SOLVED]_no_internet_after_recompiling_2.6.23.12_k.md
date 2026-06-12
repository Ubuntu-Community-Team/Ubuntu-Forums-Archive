---
title: "[SOLVED] no internet after recompiling 2.6.23.12 kernel"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by kikekurikapoo on 2007-12-25
Hi, yeah I need help with figuring out why I lose my internet connection after booting with a recompiled kernel (master kernel how-to 2.6.23.12) and (2.6.24-rc6 kernelcheck). I've recompiled about 8 times now with the last two I didn't even bother doing anything with the xconfig and just let it compile with the default options and still internet no go. Everything is working except for the internet connection (I think, haven't really checked it out yet).  Im quite new with linux btw sorry if the answer might be obvious. Oh Im using ubuntu gutsy 2.6.22-14-generic and   

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)

help is much appreciated!

---

### Post by Engessa on 2007-12-25
I'm having a similar problem except it came as soon as i installed Gusty. The strange thing is i'm using a LAN so there's no logical reason for no internet. Even stranger, i can ping other computers on the network, the router, and even some websites, although i cannot connect to any of these with a browser. If you can ping a website, maybe your having the same problem? Unfortunately, i dont know the solution.

---

### Post by kevdog on 2007-12-25
What drivers were you using in the old version?  The kernel check program is great, however it only compiles a  vanilla kernel.  Ubuntu's kernel is slightly different in that they put additional modules in their kernel such as madwifi, nvdia drivers etc.  These are not included in the vanilla kernel.  If you were using any of the restricted packages in the older kernel these will not be in the vanilla kernel.  Additionally if you were using any custom kernel module -- such as ndiswrapper -- you need to add this to the vanilla kernel.  Once you kind of grasp what kernel modules are in the vanilla kernel, what additional  modules are in Ubuntu kernels, and other modules that users can later add (such as ndiswrapper), the situation becomes much more clear.

---

### Post by kikekurikapoo on 2007-12-26
I just started using ubuntu about 3 weeks ago and I haven't used any restricted packages except for fglrx. Ubuntu's kernel and the recompiled kernel was using forcedeth.ko as a driver for it. I've read somewhere to check whether the module is 
loaded and it is 

lsmod                forcedeth              51592  0 (the screwed kernel had diff nos.)

and
 
dmesg

[    3.588000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.744000] forcedeth: using HIGHDMA
[    4.264000] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0

---

### Post by kevdog on 2007-12-26
Great -- glad you didnt run into any problem with the video driver -- perhaps this driver is included in the vanilla kernel and not an Ubuntu addition.  I thought however your original question was about networking problems?

---

### Post by kikekurikapoo on 2007-12-26
Yeah, Internet's not working...

---

### Post by kevdog on 2007-12-26
What driver module were you using before, or what kind of chipset do you have?
lshw -C network

---

### Post by kikekurikapoo on 2007-12-26
When I type in lshw -C network it just flashes PCI (sysfs) and some other things, too fast I couldn't see, but i tried lshw without any options and is this what you wanted to see?    

 *-bridge DISABLED
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:13:d4:b4:41:64
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

and I forgot to mention at startup I get a failed to initialize HAL warning, could that be it?

---

### Post by kevdog on 2007-12-26
I will have to take a look at this later, but off the cuff Im confused.  Nvidia makes network controllers?? That would be news to me although that is what it looks like.  Do a couple of things. Boot back into the old working kernel and redo lshw -C network and post this info so we can clarify the chipset and driver info.  Also look in dmesg to see if you can post that HAL problem specifically.  There are a bunch of log files located in /var/log.  I think it would be possibly under the boot log or message log.

---

### Post by kikekurikapoo on 2007-12-26
sudo lshw -C network in the working kernel does the same thing, there's no output just flashes PCI (sysfs), some other stuff.. is lshw the same as system>preferences>hardware information? because that works in the working kernel..  oh and Im sorry but I dont know what to look for regarding that HAL problem, I tried searching for eth0 and found these..

Dec 26 14:08:31 hotbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 26 14:08:37 hotbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 26 14:08:37 hotbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers


problem solved.. I saw a red asterisk at boot asking for inotify to be turned on for HAL to work.  thanks kevdog!

---

