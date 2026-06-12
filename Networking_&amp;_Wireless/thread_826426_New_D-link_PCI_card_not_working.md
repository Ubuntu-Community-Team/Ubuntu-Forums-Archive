---
title: "New D-link PCI card not working"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by chrisdl on 2008-06-11
I think my house was hit with lightning - actually I think it came through my AT&T Uverse internet connection because all my PCs network cards appear to not be working.  So I went out and bought a new D-Link DGE-530T and from the supported hardware list this one should be working.  I am using Gutsy 7.1.

When I run $lspci it says down below....
02:08.0 Ehternet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
02:0c.0 Ethernet controller: 3Com Corporation Unknown Device ffff (rev 78)

SO it appears my machine can find the new and the old ethernet adapters.

I've searched this forum and that is as far as I can get.  What do I check now?  AM I forgetting something.

BTW - My machine only boots up in low graphics mode now as well.  When my machine (an old Dell precision) it gives me a plug and play configuration error.  So something else might be wrong with the machine.

Help!

---

### Post by ene_dene on 2009-11-14
I also have a problem in Karmic Koala, I'll paste my bug report:
I just bought this card yesterday D-LINK DGE-530T revision 11. I use Karmic Koala.
The card gets detected, module skge loaded, I can setup a static ip but it doesn't work.

```
lspci | grep -i ethernet
``` gives:
```
01:06.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
```

I did a little research and it seems that module sk98lin should be used. I downloaded the drivers for Marvell Yukon 88E8001 chipset which this card uses from:
[http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=10013&term=typ.treiber+bs.Linux+produkt.SK-9821V2.0&produkt=produkt.SK-9821V2.0&typ=typ.treiber&system=bs.Linux](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=10013&term=typ.treiber+bs.Linux+produkt.SK-9821V2.0&produkt=produkt.SK-9821V2.0&typ=typ.treiber&system=bs.Linux)

I tried to install module sk98lin which should fix the problem but I got an error which I don't understand, so if someone could help:
```
sudo ./install.sh
```
now the install.log:
```
+++ Install mode: User
+++ Driver version: 10.70.1.3 (Jun-30-2008)
+++ Kernel version 2.6.31-14-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=x86_64
+++ Architecture: x86_64
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
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
make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.o
  CC [M]  /tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.o
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_init_device’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:399: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:439: error: ‘struct net_device’ has no member named ‘open’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:440: error: ‘struct net_device’ has no member named ‘stop’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:441: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:442: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:443: error: ‘struct net_device’ has no member named ‘set_mac_address’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:444: error: ‘struct net_device’ has no member named ‘do_ioctl’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:445: error: ‘struct net_device’ has no member named ‘change_mtu’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:448: error: ‘struct net_device’ has no member named ‘poll_controller’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:466: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:476: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:570: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:599: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:605: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:613: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:624: error: ‘struct net_device’ has no member named ‘open’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:625: error: ‘struct net_device’ has no member named ‘stop’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:626: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:627: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:628: error: ‘struct net_device’ has no member named ‘set_mac_address’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:629: error: ‘struct net_device’ has no member named ‘do_ioctl’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:630: error: ‘struct net_device’ has no member named ‘change_mtu’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:633: error: ‘struct net_device’ has no member named ‘poll_controller’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_resume’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1117: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_suspend’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1195: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘FreeResources’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1509: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1510: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_remove_device’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1690: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1749: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeIsr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2281: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2294: error: implicit declaration of function ‘netif_rx_schedule_prep’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2303: error: implicit declaration of function ‘__netif_rx_schedule’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeOpen’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2407: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeClose’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2727: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2770: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeXmit’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3006: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGePoll’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3096: error: implicit declaration of function ‘__netif_rx_complete’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeNetPoll’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3128: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeSetMacAddr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4166: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeSetRxMode’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4223: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeChangeMtu’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4335: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeStats’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4456: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeIoctl’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4761: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkDrvEvent’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6613: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkDrvEnterDiagMode’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6905: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6922: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6923: error: ‘struct net_device’ has no member named ‘priv’
make[1]: *** [/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘SkY2Isr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:397: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘SkY2Xmit’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:503: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘AllocateAndInitLETables’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:2873: warning: cast to pointer from integer of different size
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:2875: warning: cast from pointer to integer of different size
make[1]: *** [/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.o] Error 1
make: *** [_module_/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
+++ Compiler error
```

---

