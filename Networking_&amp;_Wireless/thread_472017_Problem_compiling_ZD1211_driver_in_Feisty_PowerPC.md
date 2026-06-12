---
title: "Problem compiling ZD1211 driver in Feisty PowerPC"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Deben_69 on 2007-06-12
I'm trying to compile from source the ZyDAS 1211 driver (Not RW - it doesn't work for me either) for my Planex GW-US54GD USB WIFI Dongle in Feisty (2.6.20-16-powerpc) and this is the result:

...laptop:~/Downloaded_Files/ZD1211LnxDrv_2_4_0_0$ sudo make both
make clean
make[1]: Entering directory `/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[1]: Leaving directory `/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0'
make ZD1211REV_B=0
make[1]: Entering directory `/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0'
/lib/modules/2.6.20-16-powerpc/build
/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0
-I/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-16-powerpc/build SUBDIRS=/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-powerpc'
  CC [M]  /home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0/src/zd1205.o
[B]cc1: error: unrecognized command line option "-fno-stack-protector"
cc1: error: unrecognized command line option "-Wno-pointer-sign"[/B]
make[3]: *** [/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0/src/zd1205.o] Error 1
make[2]: *** [_module_/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-powerpc'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/daven/Downloaded_Files/ZD1211LnxDrv_2_4_0_0'
make: *** [both] Error 2



when I connect the USB Device and I type dmesg :

[11062.399121] usb 2-1: new high speed USB device using ehci_hcd and address 2
[11062.532695] usb 2-1: configuration #1 chosen from 1 choice

when I type lsusb :

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
**Bus 002 Device 002: ID 2019:ed01**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 05ac:8205 Apple Computer, Inc.
Bus 001 Device 003: ID 05ac:030a Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000

Can someone help me with this problem?  ;)

Ps. I Also tried in my PC (Feitsy Linux 2.6.20-16-generic) and it give me the same errors... I followed the instructions and HOW-TOs in the ZD1211 threads !

---

