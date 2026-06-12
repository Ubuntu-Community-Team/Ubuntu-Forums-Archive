---
title: "Installing driver help"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by freefromXP on 2007-06-04
Problem with Driver install
  
   Ok I am installing a Airlink (AWLL3026) (zd1211B) network adapter on.
 
  Dell inspiron 7500 Pii 400mhz 128m, 20g,
Fresh install of Ubuntu 6.10


  Ok now for the stuff I need help on.  I read forums and I am following this [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)")
  
I get down to where it says download driver STEP 3

THE links are not good anymore but I followed them to find this driver [http://downloads.sourceforge.net/zd1211/zd1211-firmware1.3.tar.bz2](http://downloads.sourceforge.net/zd1211/zd1211-firmware1.3.tar.bz2)

  SO I replaces the guide lines "wget http://zd1211.ath.cx/download/zd1211-driver-r83.tgz"

With the new link wget [http://downloads.sourceforge.net/zd1211/zd1211-firmware1.3.tar.bz2?modtime=1167489439&big_mirror=0](http://downloads.sourceforge.net/zd1211/zd1211-firmware1.3.tar.bz2?modtime=1167489439&big_mirror=0)
 
FIle downloaded fine.  I then followed next step

tar xvzf zd1211-driver-r83.tgz  
And replaced with
tar xvzf zd1211-firmware1.3.tar.bz2

 I get error not in gzip format how to continue with the guide to get driver installed.

Update I found the write driver and this is what I did


First downloaded
[B]
bill@laptop:~$ wget [http://www.deine-taler.de/zd1211/ZD1211LnxDrv_2_16_0_0.tar.gz](http://www.deine-taler.de/zd1211/ZD1211LnxDrv_2_16_0_0.tar.gz)[/B]
--17:42:42--  [http://www.deine-taler.de/zd1211/ZD1211LnxDrv_2_16_0_0.tar.gz](http://www.deine-taler.de/zd1211/ZD1211LnxDrv_2_16_0_0.tar.gz)
           => `ZD1211LnxDrv_2_16_0_0.tar.gz'
Resolving [www.deine-taler.de](www.deine-taler.de)... 217.160.107.63
Connecting to www.deine-taler.de|217.160.107.63|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 313,849 (306K) [application/x-tar]

100%[====================================>] 313,849       99.31K/s    ETA 00:00

17:42:46 (98.96 KB/s) - `ZD1211LnxDrv_2_16_0_0.tar.gz' saved [313849/313849]

**Then**

**bill@laptop:~$ tar xvzf ZD1211LnxDrv_2_16_0_0.tar.gz**
ZD1211LnxDrv_2_16_0_0/
ZD1211LnxDrv_2_16_0_0/Winevl_iface/
ZD1211LnxDrv_2_16_0_0/Winevl_iface/pkt_send.c
ZD1211LnxDrv_2_16_0_0/Winevl_iface/winevl_bridge.c
ZD1211LnxDrv_2_16_0_0/src/
ZD1211LnxDrv_2_16_0_0/src/zdasocsvc.c
ZD1211LnxDrv_2_16_0_0/src/zdglobal.c
ZD1211LnxDrv_2_16_0_0/src/zdos.h
ZD1211LnxDrv_2_16_0_0/src/zdmisc.c
ZD1211LnxDrv_2_16_0_0/src/zddebug.c
ZD1211LnxDrv_2_16_0_0/src/zdpci_hotplug.h
ZD1211LnxDrv_2_16_0_0/src/WS11UPh.h
ZD1211LnxDrv_2_16_0_0/src/zdsm.h
ZD1211LnxDrv_2_16_0_0/src/zdequates.h
ZD1211LnxDrv_2_16_0_0/src/zdusb.c
ZD1211LnxDrv_2_16_0_0/src/zdpci_pcmcia.c
ZD1211LnxDrv_2_16_0_0/src/WS11Ub.h
ZD1211LnxDrv_2_16_0_0/src/zdtkipseed.h
ZD1211LnxDrv_2_16_0_0/src/zd1205.h
ZD1211LnxDrv_2_16_0_0/src/zdpsmon.c
ZD1211LnxDrv_2_16_0_0/src/zd1211.h
ZD1211LnxDrv_2_16_0_0/src/zddebug2.c
ZD1211LnxDrv_2_16_0_0/src/common.h
ZD1211LnxDrv_2_16_0_0/src/zdpmfilter.c
ZD1211LnxDrv_2_16_0_0/src/zdglobal.h
ZD1211LnxDrv_2_16_0_0/src/zdtkipseed.c
ZD1211LnxDrv_2_16_0_0/src/zdapi.h
ZD1211LnxDrv_2_16_0_0/src/zddebug.h
ZD1211LnxDrv_2_16_0_0/src/WS11UPhR_Turbo.h
ZD1211LnxDrv_2_16_0_0/src/zdsorts.h
ZD1211LnxDrv_2_16_0_0/src/zdhci.h
ZD1211LnxDrv_2_16_0_0/src/zd80211.h
ZD1211LnxDrv_2_16_0_0/src/zdturbo_burst.h
ZD1211LnxDrv_2_16_0_0/src/zydas_common.h
ZD1211LnxDrv_2_16_0_0/src/zdpci_hotplug.c
ZD1211LnxDrv_2_16_0_0/src/zdlpmgt.h
ZD1211LnxDrv_2_16_0_0/src/menu_drv_macro.h
ZD1211LnxDrv_2_16_0_0/src/zdpci_pcmcia.h
ZD1211LnxDrv_2_16_0_0/src/zdencrypt.h
ZD1211LnxDrv_2_16_0_0/src/zdencrypt.c
ZD1211LnxDrv_2_16_0_0/src/zdpsmon.h
ZD1211LnxDrv_2_16_0_0/src/zdauthrsp.c
ZD1211LnxDrv_2_16_0_0/src/zdauthreq.c
ZD1211LnxDrv_2_16_0_0/src/WS11UPhm.h
ZD1211LnxDrv_2_16_0_0/src/zdcompat.h
ZD1211LnxDrv_2_16_0_0/src/zdmic.c
ZD1211LnxDrv_2_16_0_0/src/zdhci.c
ZD1211LnxDrv_2_16_0_0/src/zdversion.h
ZD1211LnxDrv_2_16_0_0/src/zd1205.c
ZD1211LnxDrv_2_16_0_0/src/zdshared.h
ZD1211LnxDrv_2_16_0_0/src/zdinlinef.h
ZD1211LnxDrv_2_16_0_0/src/zdmmrx.h
ZD1211LnxDrv_2_16_0_0/src/zdmic.h
ZD1211LnxDrv_2_16_0_0/src/zdmisc.h
ZD1211LnxDrv_2_16_0_0/src/zdreq.c
ZD1211LnxDrv_2_16_0_0/src/zdhw.c
ZD1211LnxDrv_2_16_0_0/src/zdshared.c
ZD1211LnxDrv_2_16_0_0/src/zdmmrx.c
ZD1211LnxDrv_2_16_0_0/src/zdbuf.c
ZD1211LnxDrv_2_16_0_0/src/zdtypes.h
ZD1211LnxDrv_2_16_0_0/src/zdbuf.h
ZD1211LnxDrv_2_16_0_0/src/zdlpmgt.c
ZD1211LnxDrv_2_16_0_0/src/zdsynch.c
ZD1211LnxDrv_2_16_0_0/src/zdturbo_burst.c
ZD1211LnxDrv_2_16_0_0/src/WS11Ur.h
ZD1211LnxDrv_2_16_0_0/src/zd1205_proc.c
ZD1211LnxDrv_2_16_0_0/src/zdhw.h
ZD1211LnxDrv_2_16_0_0/src/zdutils.h
ZD1211LnxDrv_2_16_0_0/src/zdreq.h
ZD1211LnxDrv_2_16_0_0/src/zdusb.h
ZD1211LnxDrv_2_16_0_0/src/zdpmfilter.h
ZD1211LnxDrv_2_16_0_0/src/WS11UPhR.h
ZD1211LnxDrv_2_16_0_0/src/zddebug2.h
ZD1211LnxDrv_2_16_0_0/src/zd1211.c
ZD1211LnxDrv_2_16_0_0/Makefile
ZD1211LnxDrv_2_16_0_0/apdbg.c
ZD1211LnxDrv_2_16_0_0/Menudbg/
ZD1211LnxDrv_2_16_0_0/Menudbg/utils.h
ZD1211LnxDrv_2_16_0_0/Menudbg/TallyReg.c
ZD1211LnxDrv_2_16_0_0/Menudbg/TallyCnt.c
ZD1211LnxDrv_2_16_0_0/Menudbg/macro.h
ZD1211LnxDrv_2_16_0_0/Menudbg/TallyReg.h
ZD1211LnxDrv_2_16_0_0/Menudbg/menudbg.c
ZD1211LnxDrv_2_16_0_0/Menudbg/zddebug2.c
ZD1211LnxDrv_2_16_0_0/Menudbg/TextForm.h
ZD1211LnxDrv_2_16_0_0/Menudbg/utils.c
ZD1211LnxDrv_2_16_0_0/Menudbg/WRITE_Handler.c
ZD1211LnxDrv_2_16_0_0/Menudbg/RegDefine.h
ZD1211LnxDrv_2_16_0_0/Menudbg/menu_drv_macro.h
ZD1211LnxDrv_2_16_0_0/Menudbg/WRITE_Handler.h
ZD1211LnxDrv_2_16_0_0/Menudbg/READ_Handler.c
ZD1211LnxDrv_2_16_0_0/Menudbg/Makefile
ZD1211LnxDrv_2_16_0_0/Menudbg/ioctl_op.h
ZD1211LnxDrv_2_16_0_0/Menudbg/TextForm.c
ZD1211LnxDrv_2_16_0_0/Menudbg/READ_Handler.h
ZD1211LnxDrv_2_16_0_0/Menudbg/ioctl_op.c
ZD1211LnxDrv_2_16_0_0/Menudbg/zddebug2.h

**THen**
**bill@laptop:~$ cd ZD1211LnxDrv_2_16_0_0 **

  [B][COLOR="Red"]This is where I have Problems[/COLOR]
[COLOR="Red"]bill@laptop:~/ZD1211LnxDrv_2_16_0_0$ sudo make both[/B]
make clean
make[1]: Entering directory `/home/bill/ZD1211LnxDrv_2_16_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[1]: Leaving directory `/home/bill/ZD1211LnxDrv_2_16_0_0'
make ZD1211REV_B=0
make[1]: Entering directory `/home/bill/ZD1211LnxDrv_2_16_0_0'
/lib/modules/2.6.17-11-386/build
/home/bill/ZD1211LnxDrv_2_16_0_0
-I/home/bill/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/bill/ZD1211LnxDrv_2_16_0_0 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bill/ZD1211LnxDrv_2_16_0_0'
make: *** [both] Error 2
[/COLOR]

---

