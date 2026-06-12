---
title: "make both error when installing ZyDas 1211 driver"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by sadalmelik57 on 2006-12-30
I've run into an error installing the driver for my Gigafast WF748-CUI USB Wireless Adapter.  I am using the guide at [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29) but when I get to step 5 to use the "make both" command I get the following output:

:~/zd1211-driver-r83$ sudo make both
make ZD1211REV_B=0
make[1]: Entering directory `/home/l/zd1211-driver-r83'
/lib/modules/2.6.17-10-386/build
/home/l/zd1211-driver-r83
-I/home/l/zd1211-driver-r83/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/l/zd1211-driver-r83 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/l/zd1211-driver-r83'
make: *** [both] Error 2


I have verified that /lib/modules/2.6.17-10-386/build exists, and I've verified that /home/l/zd1211-driver-r83 modules also exists.  I previously used this same guide successfully on another computer, so I was confident I'd have no trouble!  Can you help?

Many thanks!

---

### Post by sadalmelik57 on 2007-01-01
I solved the problem.  It was due to the fact the Linux Headers did not install properly in step 3.  I reinstalled linux headers and make both worked.

---

