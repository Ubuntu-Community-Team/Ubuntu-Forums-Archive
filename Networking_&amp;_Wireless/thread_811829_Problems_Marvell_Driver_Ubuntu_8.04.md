---
title: "Problems Marvell Driver Ubuntu 8.04"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by ohashijr on 2008-05-29
I try several tutorials in the net...

I downloaded the Marvell driver and 

executing ./install.sh 

I got the following error message:

+++ Install mode: User
+++ Driver version: 10.60.2.3 (Apr-28-2008)
+++ Kernel version 2.6.24-16-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=x86_64
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.4/
2.4/skdim.c
2.4/sky2.c
2.4/skethtool.c
2.4/Makefile
2.4/skge.c
2.4/h/
2.4/h/skdrv1st.h
2.4/h/skdrv2nd.h
2.4/skproc.c
2.6/
2.6/skdim.c
2.6/sky2.c
2.6/skethtool.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skproc.c
common/
common/skgehwt.c
common/skgeasf.c
common/sk98lin.htm
common/skgeinit.c
common/sktwsi.c
common/skvpd.c
common/sky2le.c
common/sk98lin.4
common/skfops.c
common/skgespilole.c
common/skgeasfconv.c
common/skgemib.c
common/skaddr.c
common/skcsum.c
common/skgepnmi.c
common/vpdcheck.c
common/sklm80.c
common/skqueue.c
common/sktimer.c
common/skrlmt.c
common/skgespi.c
common/skxmac2.c
common/skgesirq.c
common/h/
common/h/sktypes.h
common/h/skpcidevid.h
common/h/skqueue.h
common/h/skrlmt.h
common/h/skgepnm2.h
common/h/skgeasfconv.h
common/h/skaddr.h
common/h/skdebug.h
common/h/mvyexhw.h
common/h/skgehw.h
common/h/skgehwt.h
common/h/skfops.h
common/h/sktimer.h
common/h/skgepnmi.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skerror.h
common/h/sktwsi.h
common/h/skcsum.h
common/h/skversion.h
common/h/xmac_ii.h
common/h/sky2le.h
common/h/skgeasf.h
common/h/skgespi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/lm80.h
common/h/skgedrv.h
common/sk98lin.txt
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.o
  CC [M]  /tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.o
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c: In function ‘sk98lin_init_device’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:483: error: ‘struct net_device’ has no member named ‘poll’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:484: error: ‘struct net_device’ has no member named ‘weight’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:489: error: ‘struct net_device’ has no member named ‘poll’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:490: error: ‘struct net_device’ has no member named ‘weight’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:611: error: ‘struct net_device’ has no member named ‘poll’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:612: error: ‘struct net_device’ has no member named ‘weight’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:617: error: ‘struct net_device’ has no member named ‘poll’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:618: error: ‘struct net_device’ has no member named ‘weight’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c: In function ‘SkGeIsr’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:2342: error: too few arguments to function ‘netif_rx_schedule_prep’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:2345: error: too few arguments to function ‘__netif_rx_schedule’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c: In function ‘SkGeIsrOnePort’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:2513: error: too few arguments to function ‘netif_rx_schedule_prep’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:2518: error: too few arguments to function ‘__netif_rx_schedule’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c: In function ‘SkGePoll’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:3277: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:3277: warning: type defaults to ‘int’ in declaration of ‘_y’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:3277: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:3298: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.c:3302: error: too few arguments to function ‘netif_rx_complete’
make[1]: *** [/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/skge.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c: In function ‘SkY2Isr’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:428: error: implicit declaration of function ‘__netif_rx_schedule_prep’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:429: error: too few arguments to function ‘__netif_rx_schedule’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c: In function ‘SkY2Poll’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:665: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:665: warning: type defaults to ‘int’ in declaration of ‘_y’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:665: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:672: error: ‘struct net_device’ has no member named ‘quota’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:694: error: too few arguments to function ‘netif_rx_complete’
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c: In function ‘AllocateAndInitLETables’:
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:2857: warning: cast to pointer from integer of different size
/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.c:2859: warning: cast from pointer to integer of different size
make[1]: *** [/tmp/Sk98IADeMUWLppcXCMpTemcbY/all/sky2.o] Error 1
make: *** [_module_/tmp/Sk98IADeMUWLppcXCMpTemcbY/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
+++ Compiler error

---

### Post by chili555 on 2008-05-29
```
cd DriverInstall/
sudo gedit install.sh
```Change the very first line from #!/bin/sh to #!/bin/bash. Save and close gedit. Then do:```
./install.sh
```Did your errors disappear?

---

### Post by Baltuki on 2008-05-30
I get the same error when i try to compile the sk98lin driver.
I have changed the first line of the install.sh script, installed build-essential, linux-headers, linux sources, compiler tools and everything i read in many tutorials, but always appears the same compile error.

---

### Post by javier-es on 2008-06-13
I'm getting exactly the same error as ohashijr reported when I try to compile the sk98lin module. I've also tried to peek into the failing C code, attempting to "fix" it if possible, with no results at all. I've read a lot of posts about this topic on the Internet, but I just can't get this thing to work.

Any help with this would be greatly appreciated. Thanks in advance.

---

### Post by Mengus on 2008-08-04
Im having the exakt same problem right now. I notice this thread is old. But I cant find the answer to this problem. IF enyone knows how to fix it please tell me. thx

---

### Post by caljohnsmith on 2008-08-04
Just out of curiosity, which Marvell driver are you trying to compile, i.e  which Marvell wireless chipset does your NIC have? I have a Marvell 88w8335 that works great with ndiswrapper, and of course all I needed was the Windows drivers from my wireless card's install CD.

---

### Post by jlindbergh on 2008-08-04
I'm trying to compile this driver and I get exactly the same error too!
I have all the correct headers, and I'm running install.sh via bash.

I have an on-board Marvell 88E8001 controller and I'm trying to compile this new driver because of this:
[http://ubuntuforums.org/showthread.php?t=876256](http://ubuntuforums.org/showthread.php?t=876256)

regards
/jl

---

### Post by cjb on 2008-09-13
I'm having similar problems. 

I downloaded the Marvell drivers from [http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204) and tried to install them. I changed #!/bin/sh to #!/bin/bash. The installer started up, but eventually bombed out.
The last few lines of the install.log file (full text attached) are:

make[1]: *** [/tmp/Sk98IZoYBFrBkpcjrRSJTObZW/all/sky2.o] Error 1
make: *** [_module_/tmp/Sk98IZoYBFrBkpcjrRSJTObZW/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
+++ Compiler error

Anyone know how to fix that?

SW - Ubuntu 8.04.1, 64-bit server edition.

HW details - mobo DFI LanParty UT NF4 Ultra-D motherboard ([http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US](http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US)). Twin core AMD64 CPU, 4GB installed RAM.

Any help or pointers appreciated.
thanks,
James

---

### Post by fgking on 2011-02-17
I am having the same problem, I got the .INF file from the driver's disc  and installed it with ndiswrapper. It seems to accept but it keeps telling that no hardware is present. the wireless usb is definately inserted but no light is on. this device work fine on windows. Is the INF. driver file the only thing ubuntu needs or do I have to include sys and the cat files as well. Could some one help please.

---

### Post by mathia on 2011-03-30
Hi all,

**[B]Installing Marvell Yukon driver on Ubuntu**:[/B]

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "e.g. 88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - v10.87.3.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by foresto on 2011-10-23
I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

