---
title: "installing usb wireless driver - how??"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-16
I've just installed Hardy on a 5-year-old PC and want to get it connected to the internet. I have a USB wireless adapter, which is meant to be Linux-compatible. I have tried to follow the instructions but being a newbie, I got quite lost.

Any guidance would be much appreciated! I've attached the instructions pdf, if anyone has a moment to have a look.

I've successfully carried out the first step of the instructions: extracting the files from the .tar.gz archive. However, I can't then get the makefile to work!

I typed in "make" in Terminal after going to the directory containing the makefile, and I got some error messages that I don't understand...

---

### Post by cosmicappuccino on 2009-02-16
Here's the output from Terminal when I type in "make":

> user@mydesktop:~/ZD1211LnxDrv_2_16_0_0$ make
make both
make[1]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make clean
make[2]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
/lib/modules/2.6.24-23-generic/build
/home/user/ZD1211LnxDrv_2_16_0_0
-I/home/user/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/user/ZD1211LnxDrv_2_16_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: warning: initialisation from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòwrite‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòfd‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòbuf‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòcount‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: warning: type defaults to ‚Äòint‚Äô in declaration of ‚Äò_syscall3‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: error: expected ‚Äò,‚Äô or ‚Äò;‚Äô before ‚Äò_syscall3‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: ‚Äòdot11A_Channel‚Äô undeclared here (not in a function)
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_rx_isr‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4218: error: ‚Äòstruct sk_buff‚Äô has no member named ‚Äòmac‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_xmit_frame‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5025: warning: ISO C90 forbids mixed declarations and code
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5026: warning: assignment from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5029: warning: assignment from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_load_card_setting‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8708: error: implicit declaration of function ‚Äòopen‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8725: error: implicit declaration of function ‚Äòread‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8729: error: implicit declaration of function ‚Äòclose‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_save_card_setting‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8881: error: implicit declaration of function ‚Äòwrite‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzdcb_rx_ind‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9913: error: implicit declaration of function ‚Äòeth_copy_and_sum‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_set_zd_cbs‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10344: warning: assignment from incompatible pointer type
make[4]: *** [/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/home/user/ZD1211LnxDrv_2_16_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make: *** [all] Error 2


Any suggestions about what I should do to get it to work, please..? :confused:

---

### Post by gn2 on 2009-02-16
You might find these instructions more up to date and easier to follow:

[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

---

### Post by trepid666 on 2009-02-16
Do you need to sudo make?

---

### Post by cosmicappuccino on 2009-02-16
It's working now :)
Thanks for your replies...

> **gn2 said:**
> You might find these instructions more up to date and easier to follow:

[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

@gn2: Thanks, very relevant!

---

