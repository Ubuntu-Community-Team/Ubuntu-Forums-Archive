---
title: "help me to install wifi max usb dongle"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Countra on 2008-01-20
Ok, so the most of the other guides [here on the forum] doesent work right now since i got a more "up-to-date" kernell.. Anyways, when i try to compile the drivers for my WiFi MAX, i get this:
> arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ make install
/lib/modules/2.6.22-14-generic/build
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0
-I/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:42:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.h:663: warning: ‘__packed__’ attribute ignored
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:244: warning: function declaration isn’t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:245: warning: function declaration isn’t a prototype
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘write’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘fd’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘buf’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:439: error: expected declaration specifiers or ‘...’ before ‘count’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:440: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:445: error: ‘dot11A_Channel’ undeclared here (not in a function)
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_house_keeping’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:1441: warning: unused variable ‘tmpvalue’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_config’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2313: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘U32’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_validate_frame’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:2688: warning: unused variable ‘len1’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_rx_isr’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:3927: error: ‘struct sk_buff’ has no member named ‘mac’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_close’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4608: warning: implicit declaration of function ‘re_initFdescBuf’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_xmit_frame’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_watchdog’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5335: warning: unused variable ‘ssidLenToDump’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5334: warning: unused variable ‘cbTemp’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setiwencode’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:5724: warning: unused variable ‘bReconnect’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205wext_siwscan’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6595: warning: implicit declaration of function ‘zd_CmdProbeReq’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6539: warning: unused variable ‘ul_mac_ps_state’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6538: warning: unused variable ‘oldMacMode’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6537: warning: unused variable ‘i’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_translate_scan’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: unknown conversion type character ‘,’ in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6715: warning: spurious trailing ‘%’ in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_list_bss’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:6891: warning: spurious trailing ‘%’ in format
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_ioctl’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7163: warning: implicit declaration of function ‘verify_area’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7940: warning: implicit declaration of function ‘open’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7957: warning: implicit declaration of function ‘read’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7961: warning: implicit declaration of function ‘close’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:8113: warning: implicit declaration of function ‘write’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zdcb_AssocRequest’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: implicit declaration of function ‘HashSearch’
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘zd1205_set_zd_cbs’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c: In function ‘CalculateQuality’:
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.c:9425: warning: unused variable ‘rxOffset’
make[2]: *** [/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/arsham/Desktop/ZD1211LnxDrv_2_2_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
arsham@arsham-desktop:~/Desktop/ZD1211LnxDrv_2_2_0_0$ 


yes, it is really annoying> and i really want to set up this WiFi MAX device as an access point now for my Nintendo DS [and wii] as it was made for to do.
What am i doing wrong?

---

