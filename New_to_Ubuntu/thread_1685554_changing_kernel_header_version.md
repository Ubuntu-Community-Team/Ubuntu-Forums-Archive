---
title: "changing kernel header version"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by markusan on 2011-02-10
I am trying to install the Marvell Yukon 88E8056 driver and I have a kernel header mismatch. I am using Ubuntu 10.04.

I have seen very similar problems on the forums, but not the exact versions so I was wondering if anyone has a good solution. The installation proceeds to the point where it checks the kernel header version.

Check kernel header version (kernel:2.6.32 != Header:2.6.32.15+drm33). [failed]

The installation script gives a list of possible solutions. One of them is to overwrite current include/version.h with the include/version.h currently running.

At the end of the installation the following is given:
Your kernel versionL2.6.32-24-generic
Your header version:2.6.32.15+drm33.5


Does anyone have a solution for my problem? I am very new to Linux in general and especially Ubuntu, so I do not feel comfortable tampering with the kernel. Any help would be greatly appreciated! :)

---

### Post by robsoles on 2011-02-12
Just in case you've made 2 beans without being welcomed: **Welcome to UF!**

Open "System"->"Administration"->"Synaptic Package Manager" and search using 'headers' (or more specific if you want to because lots results for just 'headers' :))

Go through the list of packages and look for the linux-headers package with version '2.6.32-24' and mark it for installation, accept changes (unless they are too radical for you in which case please 'screenshot' it and give us a look) and click 'apply' there.

Try to compile/install your Marvel Yukon driver again, any good?

---

### Post by markusan on 2011-02-14
Thank you for the Welcome, Robsoles!

I have since the original post switched to Ubuntu 10.10 and tried to do the installation again. Prior to running the installation script, I type:

sudo ln -s /usr/src/linux-headers-2.6.35

When I run the installation script, this is what happens:

```
Disconnect alternative devices:  (done)                                                                               [   OK   ]
Unload alternative driver (done)                                                                                           [   OK   ]
Create tmp dir (/tmp/Sk98IlOTAhmloOBBkdrfcRkBl)                                                           [   OK   ]
Check user id (0)                                                                                                                  [   OK   ]
Check kernel version (2.6.35-25-generic)                                                                            [   OK   ]
Check kernel symbol file (/proc/kallsyms)                                                                            [   OK   ]
Check kernel type (SMP)                                                                                                     [   OK   ]
Check number of CPUs (8)                                                                                                  [   OK   ]
Check architecture (found)                                                                                                  [   OK   ]
Set architecture (x86_64)                                                                                                     [   OK   ]
Check compiler (/usr/bin/gcc)                                                                                              [   OK   ]
Check mcmodel flags (kernel)                                                                                              [   OK   ]
Check module support (/sbin/insmod)                                                                                   [   OK   ]
Check make (/usr/bin/make)                                                                                                  [   OK   ]
Check kernel gcc version (4.4.5) (Kernel:4.4.5 == gcc:4.4.5)                                                [   OK   ]
Check sk98lin driver availability (not loaded)                                                                          [   OK   ]
Check kernel header files (/usr/src/linux)                                                                               [   OK   ]
Check sources for .config file (/usr/src/linux/.config)                                                              [   OK   ]
Copy and check .config file (done)                                                                                          [   OK   ]
Check the mem address space (lowmem)                                                                             [   OK   ]
Change IOMMU (enabled)                                                                                                      [   OK   ]
Create new .config file (done)                                                                                               [   OK   ]
Execute: make oldconfig (done)                                                                                              [   OK   ]
Check modpost availability (available)                                                                                      [   OK   ]
Unpack the sources (done)                                                                                                   [   OK   ]
Check firmware availability (not available)                                                                                 [   OK   ]
Check kernel header version (not recognized)                                                                          [  warn  ]
Check kernel functions (Changed: nothing)                                                                              [   OK   ]
Compile the kernel (error)                                                                                                       [ failed ]
```

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.


This is the log file that was produced:


```
+++ Install mode: User
+++ Driver version: 10.61.3.3 (Jul-07-2008)
+++ Kernel version 2.6.35-25-generic
+++ smp_count=1
+++ cpu_number=8
+++ kernel_machine=x86_64
+++ Architecture: x86_64
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
make: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2le.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skdim.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skaddr.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skgehwt.o
  CC [M]  /tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skgeinit.o
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:308: error: unknown field &#8216;get_stats_count&#8217; specified in initializer
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:308: warning: initialization from incompatible pointer type
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;sk98lin_init_device&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:412: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:454: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:455: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:456: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:457: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:458: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:459: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:460: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:463: error: &#8216;struct net_device&#8217; has no member named &#8216;poll_controller&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:481: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:483: error: &#8216;struct net_device&#8217; has no member named &#8216;poll&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:484: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:487: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:489: error: &#8216;struct net_device&#8217; has no member named &#8216;poll&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:490: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:577: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:603: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:609: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:611: error: &#8216;struct net_device&#8217; has no member named &#8216;poll&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:612: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:615: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:617: error: &#8216;struct net_device&#8217; has no member named &#8216;poll&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:618: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:626: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:627: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:628: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:629: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:630: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:631: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:632: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:635: error: &#8216;struct net_device&#8217; has no member named &#8216;poll_controller&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetSettings&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:216: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetDrvInfo&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:279: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetWolSettings&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:309: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetPauseParam&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:330: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetCoalesce&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:370: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;sk98lin_resume&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1124: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;sk98lin_suspend&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1202: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetRxCsum&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:435: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetStrings&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:457: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeGetEthStats&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:512: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetSettings&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:557: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;FreeResources&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1517: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1518: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetWolSettings&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:645: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetPauseParam&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:673: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetCoalesce&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:781: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetRxCsum&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:972: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGePhysId&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:997: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:1016: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:1024: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;toggleLeds&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:1101: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:1109: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c: In function &#8216;SkGeSetTSO&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.c:1199: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;sk98lin_remove_device&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1699: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:1760: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeIsr&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2303: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
make[1]: *** [/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skethtool.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2315: error: implicit declaration of function &#8216;netif_rx_schedule_prep&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2318: error: implicit declaration of function &#8216;__netif_rx_schedule&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeIsrOnePort&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2473: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeOpen&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2593: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeClose&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2915: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:2958: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeXmit&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3190: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGePoll&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3249: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3250: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3250: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_min2&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3250: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3271: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3275: error: implicit declaration of function &#8216;netif_rx_complete&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeNetPoll&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:3304: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeSetMacAddr&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4348: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeSetRxMode&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4406: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4432: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_list&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4433: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4433: error: dereferencing pointer to incomplete type
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4435: error: dereferencing pointer to incomplete type
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeChangeMtu&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4518: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeStats&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4641: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkGeIoctl&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:4946: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkDrvEvent&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:6804: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c: In function &#8216;SkDrvEnterDiagMode&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:7096: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:7113: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.c:7114: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c: In function &#8216;SkY2Isr&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:397: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:428: error: implicit declaration of function &#8216;__netif_rx_schedule_prep&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:429: error: implicit declaration of function &#8216;__netif_rx_schedule&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c: In function &#8216;SkY2Xmit&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:500: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
make[1]: *** [/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/skge.o] Error 1
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c: In function &#8216;SkY2Poll&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:663: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:665: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:665: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_min2&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:665: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:672: error: &#8216;struct net_device&#8217; has no member named &#8216;quota&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:694: error: implicit declaration of function &#8216;netif_rx_complete&#8217;
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c: In function &#8216;AllocateAndInitLETables&#8217;:
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:2857: warning: cast to pointer from integer of different size
/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.c:2859: warning: cast from pointer to integer of different size
make[1]: *** [/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all/sky2.o] Error 1
make: *** [_module_/tmp/Sk98IlOTAhmloOBBkdrfcRkBl/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
+++ Compiler error
(END)
```




I have no clue what to do with this problem at this point. The installation program obviously does not recognize the kernel header version and most likely cannot compile the kernel as a result.

---

### Post by Kirboosy on 2011-02-14
Please add code brackets around your post. that way it makes it easier to read. :)

(Highlight the portion of code and click the # button from the forum menu.)


I have found compiling kernels in Ubuntu to be very difficult. Meanwhile compiling in gentoo is pretty easy.

I'm not sure why its failing. You have all the compilers installed....

What command did you use to run the installation script?

---

### Post by markusan on 2011-02-14
I ran the installation using:

sudo bash ./install.sh

Install.sh is the installation script that comes with the Marvell Yukon drivers. I do not know if the error is due to the driver is too old and incompatible with the kernel I am using. In this case I do not know what to do about it since I have no experience compiling kernels.

---

### Post by sandyd on 2011-02-14
Grab newer version of drivers.
Kernels >= 2.6.31 have the old net_device api removed.

---

### Post by markusan on 2011-02-14
I think I am out of luck with the Marvell Yukon LAN. As far as I know Marvell has not released any newer drivers for Linux. I have ordered a PCI-X network card that won't require drivers. Thanks for all your replies though!

---

### Post by TheSteelRider on 2011-02-18
> **sandyd said:**
> Grab newer version of drivers.
**Kernels >= 2.6.31 have the old net_device api removed.**

Specifically, it looks like the get_stats_count API was removed in 2.6.33.

```
# diff -Naur linux-2.6.32.27/include/linux/ethtool.h linux-2.6.33/include/linux/ethtool.h | head -36
--- linux-2.6.32.27/include/linux/ethtool.h    2010-12-09 15:29:45.000000000 -0600
+++ linux-2.6.33/include/linux/ethtool.h    2010-02-24 12:52:17.000000000 -0600
@@ -49,13 +49,14 @@
     return (ep->speed_hi << 16) | ep->speed;
 }
 
+#define ETHTOOL_FWVERS_LEN    32
 #define ETHTOOL_BUSINFO_LEN    32
 /* these strings are set to whatever the driver author decides... */
 struct ethtool_drvinfo {
     __u32    cmd;
     char    driver[32];    /* driver short name, "tulip", "eepro100" */
     char    version[32];    /* driver version string */
-    char    fw_version[32];    /* firmware version string, if applicable */
+    char    fw_version[ETHTOOL_FWVERS_LEN];    /* firmware version string */
     char    bus_info[ETHTOOL_BUSINFO_LEN];    /* Bus info for this IF. */
                 /* For PCI devices, use pci_name(pci_dev). */
     char    reserved1[32];
@@ -357,8 +358,6 @@
     __u32                flow_type;
     /* The rx flow hash value or the rule DB size */
     __u64                data;
-    /* The following fields are not valid and must not be used for
-     * the ETHTOOL_{G,X}RXFH commands. */
     struct ethtool_rx_flow_spec    fs;
     __u32                rule_cnt;
     __u32                rule_locs[0];
@@ -497,13 +496,10 @@
     u32     (*get_priv_flags)(struct net_device *);
     int     (*set_priv_flags)(struct net_device *, u32);
     int    (*get_sset_count)(struct net_device *, int);
-
-    /* the following hooks are obsolete */
-    int    (*self_test_count)(struct net_device *);/* use get_sset_count */
-    int    (*get_stats_count)(struct net_device *);/* use get_sset_count */
     int    (*get_rxnfc)(struct net_device *, struct ethtool_rxnfc *, void *);
```

---

### Post by ubun2geek on 2011-02-18
why do you want to do that?

---

### Post by Odur on 2011-03-11
Have you tried with the latest driver (10.87.3.3)?
Get it from here: [http://extranet.marvell.com/drivers/driverDisplay.do?driverId=153](http://extranet.marvell.com/drivers/driverDisplay.do?driverId=153)

---

### Post by mathia on 2011-03-30
Hi,
Odur is right. Installing the latest driver (10.87.3.3) should fix this issue.

Please try it and let us know.

---

