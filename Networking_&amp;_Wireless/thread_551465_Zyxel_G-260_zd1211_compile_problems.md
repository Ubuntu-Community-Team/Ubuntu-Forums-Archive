---
title: "Zyxel G-260 zd1211 compile problems"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by tomski on 2007-09-15
when i try to compile this i get errors
i am running feisty 7.04
I have installed:
gcc 4.4
build essential
Linux Headers 2.6.20-generic & 386
linux symlink which currently points to the generic headers

 3 different types of zd1211 driver:
ZD1211LnxDrv_2_16_0_0
ZD1211LnxDrv_2_18_0_0
zd1211.tar.bz2 (from apt-get)

all of which fail to compile

here is the usb ID for this device:
Bus 004 Device 004: ID 0586:3408 ZyXEL Communications Corp. 


here is the output for the compile of the zd1211 apt-get will give you:

```

make clean && make && make install
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd
/lib/modules/2.6.20-16-generic/build
/usr/src/modules/zd1211
-I/usr/src/modules/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/modules/zd1211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/zd1211/src/zd1205.o
/usr/src/modules/zd1211/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/zd1211/src/zd1205.c:42:
/usr/src/modules/zd1211/src/zd1205.h:1332: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: &#8216;zd_readl&#8217; declared inline after being called
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: previous declaration of &#8216;zd_readl&#8217; was here
/usr/src/modules/zd1211/src/zd1205.c: In function &#8216;zd1205_validate_frame&#8217;:
/usr/src/modules/zd1211/src/zd1205.c:2806: warning: unused variable &#8216;len1&#8217;
/usr/src/modules/zd1211/src/zd1205.c: In function &#8216;zd1205_translate_scan&#8217;:
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;U32&#8217;
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: unknown conversion type character &#8216;,&#8217; in format
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: spurious trailing &#8216;%&#8217; in format
/usr/src/modules/zd1211/src/zd1205.c: In function &#8216;zd1205_list_bss&#8217;:
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: format &#8216;%2d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;U32&#8217;
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: spurious trailing &#8216;%&#8217; in format
/usr/src/modules/zd1211/src/zd1205.c: At top level:
/usr/src/modules/zd1211/src/zd1205.c:7520: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7601: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7690: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7706: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c: In function &#8216;CalculateQuality&#8217;:
/usr/src/modules/zd1211/src/zd1205.c:10046: warning: unused variable &#8216;rxOffset&#8217;
make[2]: *** [/usr/src/modules/zd1211/src/zd1205.o] Error 1
make[1]: *** [_module_/usr/src/modules/zd1211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

here is the output from ZD1211LnxDrv_2_16_0_0:

```

make
make both
make[1]: Entering directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make clean
make[2]: Entering directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
/lib/modules/2.6.20-16-generic/build
/usr/src/ZD1211LnxDrv_2_16_0_0
-I/usr/src/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/ZD1211LnxDrv_2_16_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: warning: initialization from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;write&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;buf&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;count&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall3&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;_syscall3&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: &#8216;dot11A_Channel&#8217; undeclared here (not in a function)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function &#8216;zd1205_xmit_frame&#8217;:
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5025: warning: ISO C90 forbids mixed declarations and code
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5026: warning: assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5029: warning: assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function &#8216;zd1205_load_card_setting&#8217;:
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8708: warning: implicit declaration of function &#8216;open&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8725: warning: implicit declaration of function &#8216;read&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8729: warning: implicit declaration of function &#8216;close&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function &#8216;zd1205_save_card_setting&#8217;:
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8881: warning: implicit declaration of function &#8216;write&#8217;
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function &#8216;zd1205_set_zd_cbs&#8217;:
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10344: warning: assignment from incompatible pointer type
make[4]: *** [/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/ZD1211LnxDrv_2_16_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make: *** [all] Error 2

```

Here is the output from ZD1211LnxDrv_2_18_0_0:

```

make
make both
make[1]: Entering directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
make clean
make[2]: Entering directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
/lib/modules/2.6.20-16-generic/build
/usr/src/ZD1211LnxDrv_2_18_0_0
-I/usr/src/ZD1211LnxDrv_2_18_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/ZD1211LnxDrv_2_18_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.o
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:452: warning: initialization from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:480: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;write&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:480: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:480: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;buf&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:480: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;count&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:481: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall3&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:481: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;_syscall3&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:486: error: &#8216;dot11A_Channel&#8217; undeclared here (not in a function)
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c: In function &#8216;zd1205_xmit_frame&#8217;:
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:5028: warning: ISO C90 forbids mixed declarations and code
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:5029: warning: assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:5032: warning: assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c: In function &#8216;zd1205_load_card_setting&#8217;:
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:8713: warning: implicit declaration of function &#8216;open&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:8730: warning: implicit declaration of function &#8216;read&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:8734: warning: implicit declaration of function &#8216;close&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c: In function &#8216;zd1205_save_card_setting&#8217;:
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:8886: warning: implicit declaration of function &#8216;write&#8217;
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c: In function &#8216;zd1205_set_zd_cbs&#8217;:
/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.c:10349: warning: assignment from incompatible pointer type
make[4]: *** [/usr/src/ZD1211LnxDrv_2_18_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/ZD1211LnxDrv_2_18_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/ZD1211LnxDrv_2_18_0_0'
make: *** [all] Error 2

```



what am i doing wrong?? or do i need something else?? i have followed many howto's and they all say to do the same thing:
modprobe -r zd1211 (which tells me that it is not present!!)
install headrs for running kernel image & build essential 
then cd to zd1211 dir 
then run make clean && make && make install

is my version of gcc to blame or is this down to a makefile config issue & also if i am running a generic kernel howcome there is not a generic module  as i can see this very popular

---

