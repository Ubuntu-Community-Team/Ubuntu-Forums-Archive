---
title: "RaLink RT2561/RT61 not working"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by rcy on 2008-11-29
Hi All,

I installed ubuntu 8.10 and it was great.
Anyway I add an Edimax wireless network card (that use RaLink chip:(),
Lspci : "**00:0e.0 Network controller: RaLink RT2561/RT61 802.11g PCI**".
Unfortunately it appears there is a problem with this type of chip. 

I download the latest driver version (2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2) from RaLink website and start follows the instructions (via **[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)** ), but when I try to run "make all" I get the following error:

"make –C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/chen/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/modules
Make[1]: Entering directory '/usr/src/linux-headers-2.6.27-7-generic'
Scripts/Makefile.build:46: *** CFLAGS was changed in "/home/chen/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/Makefile".
Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/chen/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] [COLOR="Red"]Error 2[/COLOR] 
make[1]: Leaving directory '/usr/src/linux-headers-2.6.27-7-generic' 
make: *** [all] [COLOR="Red"]Error 2[/COLOR]".
 
This is the first time that I am using Linux (and I start to give up), I have no idea what this error mean, how to solve it?

Does anybody succeed to work with this card or I am just wasting my time?

Any help would be appreciated    

Thanks

---

### Post by gnusci on 2008-11-29
It seems the source code was not tested in Ubuntu, so you may need to do some small changes to compile it, here some instruction:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

---

### Post by rcy on 2008-11-29
> **gnusci said:**
> It seems the source code was not tested in Ubuntu, so you may need to do some small changes to compile it, here some instruction:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

ok ,

I try to run: "sudo apt-get install linux-headers-`uname -r` build-essential gcc"

and I get:
"E: Couldn't find package linux-headers-`uname -r"

How can I get this package ?

---

### Post by gnusci on 2008-11-29
You may need to add the **Ubuntu Cdrom** to the sources **System->Administration->Software Sources**, since you have no connection. Then try again.

---

### Post by rcy on 2008-11-29
> **gnusci said:**
> You may need to add the **Ubuntu Cdrom** to the sources **System->Administration->Software Sources**, since you have no connection. Then try again.

not working :(

any author suggestion ?

---

### Post by gnusci on 2008-11-29
Please first insert the **Ubuntu CD**, then run the following commands:

[B]$ sudo apt-cdrom add
$ sudo aptitude update
$ sudo aptitude install build-essential linux-headers-`uname -r`"[/B]

Wait for a while between commands. If the CD if not mounted automatically use:

**$ sudo mount /dev/cdrom /media/cdrom**

You can also try these commands if the above ones fail
[B]
$ sudo aptitude install build-essential
$ sudo aptitude install linux-headers-`uname -r`[/B]

---

### Post by rcy on 2008-11-29
> **gnusci said:**
> Please first insert the **Ubuntu CD**, then run the following commands:

[B]$ sudo apt-cdrom add
$ sudo aptitude update
$ sudo aptitude install build-essential linux-headers-`uname -r`"[/B]

Wait for a while between commands. If the CD if not mounted automatically use:

**$ sudo mount /dev/cdrom /media/cdrom**

You can also try these commands if the above ones fail
[B]
$ sudo aptitude install build-essential
$ sudo aptitude install linux-headers-`uname -r`[/B]

great ,

at last its working:)

now I run the following line:"sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/" since dir /kernel/drivers/net/ is not exist should I use /lib/modules/2.6.27-7/kernel/drivers/net/ ?

---

### Post by rcy on 2008-11-30
.

---

### Post by katon on 2008-12-03
i;m also trying to install this card and without success /// i dont know what to do
there is a driver in restricted drivers (System >administration> hardware drivers

why people says that is working OUT OF THE BOX???

---

### Post by Shenz on 2008-12-30
Hello all,

I have the same problem installing this kind of network card (I have a D-Link DWL-G510). Although some say that network cards with this kind of chipset should work out of the box, I can't agree with it.

I've followed the instructions mentioned in [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61) but when running the command```
$ make all
``` this is the output I get:```
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
```
What does this error mean and how can I solve it?

Any support is much welcome. Thanks!

---

### Post by katon on 2008-12-30
look friend of mine...i put a wireless access point in BRIDGE mode so i don;t have to use wifi card in my PC....
wifi support plug and play in ubuntu is bad bad.

---

### Post by Rohan Kapoor on 2008-12-30
> **katon said:**
> i;m also trying to install this card and without success /// i dont know what to do
there is a driver in restricted drivers (System >administration> hardware drivers

why people says that is working OUT OF THE BOX???

Look my friend. Did you activate the restricted driver yet!!!! You will need some other network connection to activate it. Or alternately you could download it from another computer and then install it.

---

### Post by Rohan Kapoor on 2008-12-30
> **Shenz said:**
> Hello all,

I have the same problem installing this kind of network card (I have a D-Link DWL-G510). Although some say that network cards with this kind of chipset should work out of the box, I can't agree with it.

I've followed the instructions mentioned in [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61) but when running the command```
$ make all
``` this is the output I get:```
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/egwin/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
```
What does this error mean and how can I solve it?

Any support is much welcome. Thanks!

A few posts above you says:


> Please first insert the Ubuntu CD, then run the following commands:

$ sudo apt-cdrom add
$ sudo aptitude update
$ sudo aptitude install build-essential linux-headers-`uname -r`"

Wait for a while between commands. If the CD if not mounted automatically use:

$ sudo mount /dev/cdrom /media/cdrom

You can also try these commands if the above ones fail

$ sudo aptitude install build-essential
$ sudo aptitude install linux-headers-`uname -r`

Please read the thread, carefully to avoid duplicate questions!

---

