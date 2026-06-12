---
title: "The Driver for Marvel Yukon Ethernet Controller"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by jourman17 on 2006-12-03
Hi Guys,

I just Assembled my new PC and Iwanted to install UBUNTU 6.10 on it. I booted with live CD and it recognized everything exept my ethernet Card which is a, as Windows Reecognizes it as, **Marvell Yukon 88E8056 Gigabit Ethernet Controller.** And By the way, the Motherboard is a **Gigabyte GA-965p-S3** with Intel p965 Chipset. Apart from this every thing else is ok.

My question is is there any solution to this. I mean any kind of Driver or something or it just doesn't support this controller.

Thank a lot guys.

---

### Post by ciscosurfer on 2006-12-03
> **jourman17 said:**
> Hi Guys,

I just Assembled my new PC and Iwanted to install UBUNTU 6.10 on it. I booted with live CD and it recognized everything exept my ethernet Card which is a, as Windows Reecognizes it as, **Marvell Yukon 88E8056 Gigabit Ethernet Controller.** And By the way, the Motherboard is a **Gigabyte GA-965p-S3** with Intel p965 Chipset. Apart from this every thing else is ok.

My question is is there any solution to this. I mean any kind of Driver or something or it just doesn't support this controller.

Thank a lot guys.I have a Marvell Yukon as well (the revision and version are slightly different though -- and I use a second NIC in my machine and haven't used the Marvell for a while, but remember this being an issue with Fedora, can't recall if it was with Ubuntu or not)..these links may be of assistance:
[http://ubuntuforums.org/showthread.php?t=256867&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller](http://ubuntuforums.org/showthread.php?t=256867&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller)
[http://ubuntuforums.org/showthread.php?t=256482&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller](http://ubuntuforums.org/showthread.php?t=256482&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller)
[http://ubuntuforums.org/showthread.php?t=207916&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller](http://ubuntuforums.org/showthread.php?t=207916&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller)
[http://ubuntuforums.org/showthread.php?t=286573&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller](http://ubuntuforums.org/showthread.php?t=286573&highlight=Marvell+Yukon+88E8056+Gigabit+Ethernet+Controller)
[http://ubuntuforums.org/showthread.php?t=2457](http://ubuntuforums.org/showthread.php?t=2457)
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

So from what I've read there are fixes (read: workarounds)...some involve patching your kernel, others are more involved.  Let me know what you come up with, I'd be curious to get this problem fixed as well. ;)

PS The Marvell Yukon card I have is: 
**Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17) **
but I'm currently using my Realtek card which is: 
**Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**

---

### Post by munwin on 2006-12-04
I have the exact same motherboard / ethernet controller.
I reinstalled Winblows last night (gaming), and noticed in the driver download for the ethernet card, an "Other Driver" directory, created after extracting.

Yes, it has a Linux driver in there. I too am installing 6.10, so my next step is to try this. Back in a few minutes, to let you know how it goes...

---

### Post by munwin on 2006-12-04
OK, so the driver install.sh will create a kernel patch, or compile the kernel for you. Problem is, it errored out on the first real line of the script. It was a function declaration something like ```
function install ()
```The script errored out complaining about a ( . WTF ?!?!? ](*,) 

Anyway, I plan to get an old ethernet card in there, run all the updates, install my NVidia Drivers, THEN worry about creating a patch for the onboard NIC.:) 

If anyone has success with this, please post back here.:-k 

The driver is available on the Gigabyte website.

---

### Post by goodie on 2006-12-06
I have the same motherboard and the same problem.
Nothing is mentioned on the Gigabyte site about this.

I have searched google a lot for MARVEL YUKON UBUNTU

Pity it doesn't have an RTL8029 fallback emulation mode.

---

### Post by Dotanitis on 2006-12-08
Hello all, did you success to pass this problem because i've got the same one. :(

Dot.

---

### Post by mips on 2006-12-08
Weird, I have a gigabyte MB which works fine with dapper:

```
mips@obelix:~$ lspci -v | grep Eth
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 19)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
```

---

### Post by ciscosurfer on 2006-12-08
Well, mine ***does*** seem to work just fine (I just hadn't switched it over for so long b/c other distros that I run require the NIC and Marvell wouldn't work).  I am wondering if NDISWrapper could work for those who can't get their Marvell NIC up.  You can grab it this way```
sudo aptitude update && sudo aptitude install ndisgtk ndiswrapper-utils-1.8
```I know that it advertises itself as a wifi wrapper, but perhaps it can work for wired cards as well:

[...]"'wraps around' NDIS (Windows network driver API) drivers." >> [http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils)

---

### Post by ciscosurfer on 2006-12-10
This thread may prove useful: [http://ubuntuforums.org/showthread.php?t=297743](http://ubuntuforums.org/showthread.php?t=297743)

---

### Post by Levander on 2006-12-10
mips, mine worked fine in dapper too.  Upgrading to edgy, it stopped working.  In dapper, they used the sk98lin kernel module for it, in edgy they try to use the sky2 kernel module - and, lots of people are having problems with it.

---

### Post by lassegs on 2006-12-12
Hi. Ive got the same network card on a ASUS A8N-SLI, and none of my ethernet cards work (both the Marvell and the realtek). 

So i tried 
$ sudo modprobe -r sky2
$ sudo modprobe sky98lin
$ lsmod sky98
sk98lin               191700  0 

But still nothing shows up. 
$ sudo ifconfig eth0   <--- gives me:
eth0: error fetching interface information: Device not found

Anyone got anywhere on this?

EDIT: None of my ethernet cards shows up. Is this just me, or are you guys having the same problem?

---

### Post by lassegs on 2006-12-15
did anyone find anything out on this one? :S

---

### Post by Xaignar on 2006-12-18
> **jourman17 said:**
> Hi Guys,

I just Assembled my new PC and Iwanted to install UBUNTU 6.10 on it. I booted with live CD and it recognized everything exept my ethernet Card which is a, as Windows Reecognizes it as, **Marvell Yukon 88E8056 Gigabit Ethernet Controller.** And By the way, the Motherboard is a **Gigabyte GA-965p-S3** with Intel p965 Chipset. Apart from this every thing else is ok.

My question is is there any solution to this. I mean any kind of Driver or something or it just doesn't support this controller.

Thank a lot guys.
I have just rebuilt my computer with the same motherboard, and found a fix via a Kernel-Trap thread ([http://kerneltrap.org/node/7135)](http://kerneltrap.org/node/7135)):
> and for 88E8056 (11ab:4364) you need to add the 4364 devID into sky2.c symply search for 4363

Of course, it was kinda hard to recompile my kernel without an internet connection, so I ended up simply patching the already compiled module. This python script will work for 2.6.17-10-generic on i686, and maybe for other kernels. Run it from the dir where sky2.ko is located ($ locate sky2.ko). Use at your own risk. Also, I have to manually modprobe the module, and the interface is now eth1 compared to eth0 from before I rebuilt my system, so I had to renable it in /etc/network/interfaces. But at least it works ...

```

#!/usr/bin/env python
# -*- coding: utf8 -*-
import sys

# Calculated from the "PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4363)" entry in the sky2_id_table (sky2.c:105)
old_entry = '\xab\x11\x00\x00\x63\x43\x00\x00' + '\xff' * 4
# What we want there to be
new_entry = '\xab\x11\x00\x00\x64\x43\x00\x00' + '\xff' * 4

f = open("sky2.ko", "rb+")
module = f.read()

if module.find(new_entry) != -1:
	print "Module already patched, skipping"
	sys.exit()


pos = module.find(old_entry)
if pos == -1:
	print "Could not find entry for \"(PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4363)\""
	print "Unable to patch module"
else:
	print "Patching module"
	f.seek(pos + 4, 0)
	f.write(chr(0x64))

f.close()
```

---

### Post by tjansson on 2007-02-26
> **munwin said:**
> OK, so the driver install.sh will create a kernel patch, or compile the kernel for you. Problem is, it errored out on the first real line of the script. It was a function declaration something like ```
function install ()
```The script errored out complaining about a ( . WTF ?!?!? ](*,) 


The problem you are stating is happening since /bin/sh is a link to /bin/dash which is a bad choice. Deleting the link
```

rm /bin/sh
ln -s /bin/bash /bin/sh

```
Will make the thing above work.

---

### Post by chili555 on 2007-02-26
Here is a simpler approach. Please see posts #9 and #11. [http://www.ubuntuforums.org/showthread.php?t=365385](http://www.ubuntuforums.org/showthread.php?t=365385)

---

