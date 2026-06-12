---
title: "Help on Aztech WL230 USB"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by taktak2 on 2007-07-14
I tried installing this usb wireless card. It came with a driver compressed in .tar.gz

After I untar it on the desktop, I go to the directory (on the terminal) and run "make".

This is what it came out

/lib/modules/2.6.20-15-generic/build
/home/hafiz/Desktop/WL
-I/home/hafiz/Desktop/WL/src/include -fomit-frame-pointer -O2 -Wall -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DZD1211B -DZDCONF_LP_SUPPORT=1
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/hafiz/Desktop/WL modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/hafiz/Desktop/WL/src/zd1205.o
/home/hafiz/Desktop/WL/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/home/hafiz/Desktop/WL/src/zd1205.c:466: error: expected declaration specifiers or â€˜...â€™ before â€˜writeâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:466: error: expected declaration specifiers or â€˜...â€™ before â€˜fdâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:466: error: expected declaration specifiers or â€˜...â€™ before â€˜bufâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:466: error: expected declaration specifiers or â€˜...â€™ before â€˜countâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:467: warning: type defaults to â€˜intâ€™ in declaration of â€˜_syscall3â€™
/home/hafiz/Desktop/WL/src/zd1205.c:467: error: expected â€˜,â€™ or â€˜;â€™ before â€˜_syscall3â€™
/home/hafiz/Desktop/WL/src/zd1205.c:472: error: â€˜dot11A_Channelâ€™ undeclared here (not in a function)
/home/hafiz/Desktop/WL/src/zd1205.c: In function â€˜zd1205_validate_frameâ€™:
/home/hafiz/Desktop/WL/src/zd1205.c:2760: warning: unused variable â€˜len1â€™
/home/hafiz/Desktop/WL/src/zd1205.c: In function â€˜zd1205_load_card_settingâ€™:
/home/hafiz/Desktop/WL/src/zd1205.c:8384: warning: implicit declaration of function â€˜openâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8401: warning: implicit declaration of function â€˜readâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8405: warning: implicit declaration of function â€˜closeâ€™
/home/hafiz/Desktop/WL/src/zd1205.c: In function â€˜zd1205_save_card_settingâ€™:
/home/hafiz/Desktop/WL/src/zd1205.c:8557: warning: implicit declaration of function â€˜writeâ€™
/home/hafiz/Desktop/WL/src/zd1205.c: In function â€˜zdcb_setup_next_sendâ€™:
/home/hafiz/Desktop/WL/src/zd1205.c:8945: warning: unused variable â€˜loopCntâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8973: warning: unused variable â€˜tmpDataTimeâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8972: warning: unused variable â€˜LastDataâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8982: warning: label â€˜TX_LOOPâ€™ defined but not used
/home/hafiz/Desktop/WL/src/zd1205.c:8880: warning: unused variable â€˜LP_CNT_LAST_LATENCYâ€™
/home/hafiz/Desktop/WL/src/zd1205.c:8824: warning: unused variable â€˜tbdidxâ€™
/home/hafiz/Desktop/WL/src/zd1205.c: In function â€˜CalculateQualityâ€™:
/home/hafiz/Desktop/WL/src/zd1205.c:10220: warning: unused variable â€˜rxOffsetâ€™
make[2]: *** [/home/hafiz/Desktop/WL/src/zd1205.o] Error 1
make[1]: *** [_module_/home/hafiz/Desktop/WL] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

Can anybody help with this?
The folder name is WL.
I've installed the build-essential from the cd. I'm using Ubuntu. 7.04

---

### Post by apoth on 2007-07-14
I'm not sure, but perhaps try:

```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by taktak2 on 2007-07-14
What does the command do?

I'm installing a usb card to connect to the internet, so of course I can't connect to the internet right now using Ubuntu. I only have the Ubuntu installation cd.

---

