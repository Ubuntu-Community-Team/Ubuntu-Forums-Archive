---
title: "Still having ndiswrapper problems"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by genapollo on 2008-08-26
Ok, i've been through a few howtos and so far nothing has worked.  I started all over again and i may have found the problem but i don't know how to fix it.  It appears that ndiswrapper isn't installing properly. Here is the cmd line:

tyler@tyler-laptop:~$ tar xvzf ndiswrapper-1.46.tar.gz
ndiswrapper-1.46/
ndiswrapper-1.46/AUTHORS
ndiswrapper-1.46/ChangeLog
ndiswrapper-1.46/INSTALL
ndiswrapper-1.46/Makefile
ndiswrapper-1.46/README
ndiswrapper-1.46/ndiswrapper.spec
ndiswrapper-1.46/ndiswrapper.8
ndiswrapper-1.46/loadndisdriver.8
ndiswrapper-1.46/utils/
ndiswrapper-1.46/utils/Makefile
ndiswrapper-1.46/utils/ndiswrapper
ndiswrapper-1.46/utils/loadndisdriver.c
ndiswrapper-1.46/utils/ndiswrapper-buginfo
ndiswrapper-1.46/driver/
ndiswrapper-1.46/driver/divdi3.c
ndiswrapper-1.46/driver/hal.c
ndiswrapper-1.46/driver/iw_ndis.c
ndiswrapper-1.46/driver/iw_ndis.h
ndiswrapper-1.46/driver/loader.c
ndiswrapper-1.46/driver/loader.h
ndiswrapper-1.46/driver/longlong.h
ndiswrapper-1.46/driver/Makefile
ndiswrapper-1.46/driver/crt.c
ndiswrapper-1.46/driver/ndis.c
ndiswrapper-1.46/driver/ndis.h
ndiswrapper-1.46/driver/ndiswrapper.h
ndiswrapper-1.46/driver/ntoskernel.c
ndiswrapper-1.46/driver/ntoskernel.h
ndiswrapper-1.46/driver/ntoskernel_io.c
ndiswrapper-1.46/driver/pe_linker.c
ndiswrapper-1.46/driver/pe_linker.h
ndiswrapper-1.46/driver/pnp.c
ndiswrapper-1.46/driver/pnp.h
ndiswrapper-1.46/driver/proc.c
ndiswrapper-1.46/driver/rtl.c
ndiswrapper-1.46/driver/usb.c
ndiswrapper-1.46/driver/usb.h
ndiswrapper-1.46/driver/winnt_types.h
ndiswrapper-1.46/driver/workqueue.c
ndiswrapper-1.46/driver/wrapmem.h
ndiswrapper-1.46/driver/wrapmem.c
ndiswrapper-1.46/driver/wrapper.c
ndiswrapper-1.46/driver/wrapndis.h
ndiswrapper-1.46/driver/wrapndis.c
ndiswrapper-1.46/driver/lin2win.h
ndiswrapper-1.46/driver/win2lin_stubs.S
tyler@tyler-laptop:~$ cd ndiswrapper-1.46
tyler@tyler-laptop:~/ndiswrapper-1.46$ make distclean
make -C driver clean
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/driver'
make -C utils clean
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/utils'
rm -f *~
rm -fr ndiswrapper-1.46 ndiswrapper-1.46.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/driver'
make -C utils distclean
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/utils'
rm -f .\#*
tyler@tyler-laptop:~/ndiswrapper-1.46$ make
make -C driver
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/driver'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/tyler/ndiswrapper-1.46/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/tyler/ndiswrapper-1.46/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/tyler/ndiswrapper-1.46/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/driver'
make: *** [all] Error 2
tyler@tyler-laptop:~/ndiswrapper-1.46$ sudo make install
make -C driver install
make[1]: Entering directory `/home/tyler/ndiswrapper-1.46/driver'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/tyler/ndiswrapper-1.46/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/tyler/ndiswrapper-1.46/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/tyler/ndiswrapper-1.46/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tyler/ndiswrapper-1.46/driver'
make: *** [install] Error 2
tyler@tyler-laptop:~/ndiswrapper-1.46$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
tyler@tyler-laptop:~/ndiswrapper-1.46$ 

I realize that there are newer versions of ndiswrapper - i've tried them already.  Obviously there are some errors going on but i don't know why and i don't know how to fix them.  I'm running a presario 2500 with a broadcom 4603 (rev2)

here is lshw -C network:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a8:eb:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.105 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:41:0a:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
This might be to much info or maybe not enough - if you can help please do! I love ubuntu so far but i just moved to an apartment with wifi.  Thanks i appreciate all you people out there!

---

### Post by caljohnsmith on 2008-08-26
Is there any special reason you are trying to compile ndiswrapper yourself? If not, ndiswrapper is available through the repositories and also on your Live CD:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
So if apt-get complains it can't find those packages, just make sure you have your Live CD in your CD-ROM drive and have enabled the Live CD in System > Admin > Software Sources, under the "Third-Party Software" tab where you can hit the "add CD-ROM" button.

---

### Post by genapollo on 2008-08-27
Thanks for the direction - unfortunately i'm still having trouble.  here is what a ran into:

tyler@tyler-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
tyler@tyler-laptop:~$ mkdir ~/bcm43; cd ~/bcm43xx
tyler@tyler-laptop:~/bcm43xx$ wget [http://myspamb8.googlepages.com/WPC54Gv2_40826.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826.zip)
--22:29:02--  [http://myspamb8.googlepages.com/WPC54Gv2_40826.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826.zip)
           => `WPC54Gv2_40826.zip'
Resolving myspamb8.googlepages.com... 209.85.173.118
Connecting to myspamb8.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:29:02 ERROR 404: Not Found.

tyler@tyler-laptop:~/bcm43xx$ wget [http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip)
--22:30:33--  [http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip)
           => `WPC54Gv2_40826-pruned.zip.1'
Resolving myspamb8.googlepages.com... 209.85.173.118
Connecting to myspamb8.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 152,420 (149K) [application/octet-stream]

100%[=================================================================================>] 152,420      470.61K/s             

22:30:33 (469.84 KB/s) - `WPC54Gv2_40826-pruned.zip.1' saved [152420/152420]

tyler@tyler-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmw15.inf
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
tyler@tyler-laptop:~/bcm43xx$ 

Is there something wrong with where ndiswrapper is being saved to? do i need to change its directory or something?  Your help is greatly appreciated in this matter!

---

### Post by caljohnsmith on 2008-08-27
> **genapollo said:**
> 
22:30:33 (469.84 KB/s) - `[COLOR="Blue"]WPC54Gv2_40826-pruned.zip.1[/COLOR]' saved [152420/152420]

tyler@tyler-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmw15.inf
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
tyler@tyler-laptop:~/bcm43xx$ 

Tyler, I think the problem is simply that the drivers you downloaded are zipped together, i.e. the file you have is "WPC54Gv2_40826-pruned.zip.1". You need to first unzip that file:
```

cd ~/bcm43xx
unzip WPC54Gv2_40826-pruned.zip.1

```
After that use "ls" and "cd" (if necessary) to change into the directory where the "bcmw15.inf" driver is. Then you can run that "sudo ndiswrapper -i bcmw15.inf" command. Let me know how it goes.

---

### Post by genapollo on 2008-08-28
Ok i feel really dumb now - what i thought was bcmw15.inf is actually bcmwl5.inf - the one is actually an 'l.' Oh heavens!  Thanks anyway for all the help -if i continue to have problems i'll come back thanks!

---

