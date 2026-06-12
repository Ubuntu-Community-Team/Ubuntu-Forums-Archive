---
title: "problem with attansic L1 gigabit ethernet controller and 8.10 server"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by LAA1010 on 2008-11-11
Hi all, any help with this is much appreciated.  I am having a problem with what I believe is the nic driver in my new server rig.  It is working (as in I can connect to the internet, etc...), but my max performance is stuck at 10 Mb/s.  I'm relatively new to this process so there must be something I've missed.

Some system details:
```
> uname -a
Linux HomeServer 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux

> lspci -vvnn
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1026] (rev b0)
        Subsystem: ASUSTeK Computer Inc. Device [1043:8304]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 2301
        Region 0: Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
        Region 2: I/O ports at ec00 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: ATL1e
        Kernel modules: atl1e

Router: Netgear WGT624 v3
```

Things I've tried:
```
> sudo modprobe atl1e MediaType=1
This is supposed to force the nic to link only at 100 Mb/s full duplex. It doesn't seem to do so.

> sudo modprobe atl1e TxMemSize=64

> sudo modprobe atl1e RxMemSize=512

Also tried compiling the driver with NAPI enabled, but couldn't get it to work.
> sudo make CFLAGS_EXTRA=-DAT_NAPI install
make -C /lib/modules/2.6.27-7-server/build SUBDIRS=/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-server'
  CC [M]  /home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.o
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_probeâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:419: error: â?~struct net_deviceâ?T has no member named â?~pollâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:420: error: â?~struct net_deviceâ?T has no member named â?~weightâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_sw_initâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1082: error: â?~struct net_deviceâ?T has no member named â?~pollâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1083: error: â?~struct net_deviceâ?T has no member named â?~weightâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_cleanâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1110: error: â?~struct net_deviceâ?T has no member named â?~quotaâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1110: warning: type defaults to â?~intâ?T in declaration of â?~_min2â?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1110: error: â?~struct net_deviceâ?T has no member named â?~quotaâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1137: error: â?~struct net_deviceâ?T has no member named â?~quotaâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1142: error: too few arguments to function â?~netif_rx_completeâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_openâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1318: error: implicit declaration of function â?~netif_poll_enableâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_downâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:1764: error: implicit declaration of function â?~netif_poll_disableâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c: In function â?~at_intrâ?T:
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:2530: error: â?~IMR_NONRX_MASKâ?T undeclared (first use in this function)
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:2530: error: (Each undeclared identifier is reported only once
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:2530: error: for each function it appears in.)
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:2547: error: too few arguments to function â?~netif_rx_schedule_prepâ?T
/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.c:2548: error: too few arguments to function â?~__netif_rx_scheduleâ?T
make[2]: *** [/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src/at_main.o] Error 1
make[1]: *** [_module_/home/lalford/drivers/arl1e_2/l1e-l2e-linux-v1.0.0.4/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-server'
make: *** [default] Error 2
```

Thanks for any help!

---

