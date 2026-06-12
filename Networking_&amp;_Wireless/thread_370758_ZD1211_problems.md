---
title: "ZD1211 problems"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by frenzy05 on 2007-02-26
I searched everywhere and tried everything but I still can't get it to work. I light on the stick hasn't even come on once yet. I using the "ubuntu ultimate 1.2" pack. I need help. Thanks.

---

### Post by frenzy05 on 2007-02-26
bump, How do I find my USBID?

Edit: I have installed the  "ZD1211LnxDrv_2_16_0_0" drivers, now the light on the stick is flashing

---

### Post by tomski on 2007-09-15
how did you install the zd1211 drivers???

when i try to compile this i get errors
i have the build essential package & i have about 3 different types of zd1211 driver!!! i also have the 2.6.20-generic headrers & 2.6.20-386 headers but regardless of where i point my linux symlink i get errors!!!!

here is the output:

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
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: ‘zd_readl’ declared inline after being called
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: previous declaration of ‘zd_readl’ was here
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_validate_frame’:
/usr/src/modules/zd1211/src/zd1205.c:2806: warning: unused variable ‘len1’
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_translate_scan’:
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘U32’
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: unknown conversion type character ‘,’ in format
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: spurious trailing ‘%’ in format
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_list_bss’:
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: format ‘%2d’ expects type ‘int’, but argument 2 has type ‘U32’
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: spurious trailing ‘%’ in format
/usr/src/modules/zd1211/src/zd1205.c: At top level:
/usr/src/modules/zd1211/src/zd1205.c:7520: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7601: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7690: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7706: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c: In function ‘CalculateQuality’:
/usr/src/modules/zd1211/src/zd1205.c:10046: warning: unused variable ‘rxOffset’
make[2]: *** [/usr/src/modules/zd1211/src/zd1205.o] Error 1
make[1]: *** [_module_/usr/src/modules/zd1211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

what am i doing wrong??

---

