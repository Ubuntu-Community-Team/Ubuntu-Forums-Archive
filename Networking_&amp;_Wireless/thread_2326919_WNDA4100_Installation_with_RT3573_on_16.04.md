---
title: "WNDA4100 Installation with RT3573 on 16.04"
date: 2016-06-06
forum: Networking &amp; Wireless
---

### Post by Mike_Cook on 2016-06-06
Hello!
 So I just downloaded Ubuntu and the first problem i have is that the NETGEAR WNDA4100 USB wireless adapter isn't compatible with Linux. I've been following [this]("http://askubuntu.com/questions/219575/how-would-i-install-drivers-for-n900-wnda4100-wireless-adapter") guide hoping it would help and so far it has, the only problem is that its giving me an error about time.

```
make[1]: Entering directory '/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.{cmd,flags,d}
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.{cmd,flags,d}
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory '/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux'
rm -rf os/linux/Makefile
root@Muffin-System-Product-Name:/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO# sudo make
make -C tools
make[1]: Entering directory '/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools'
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/Makefile
make -C /lib/modules/4.4.0-21-generic/build SUBDIRS=/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-21-generic'
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.o
In file included from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_os.h:42:0,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_comm.h:56,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rt_config.h:36,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/crypt_aes.h:38,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:35:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1466:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/os/rt_linux.h:642:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1466:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1561:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/os/rt_linux.h:642:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_aes.c:1561:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.o
In file included from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_os.h:42:0,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_comm.h:56,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rt_config.h:36,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c:30:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c:563:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/os/rt_linux.h:455:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/mlme.c:564:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/os/rt_linux.h:455:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/action.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_radar.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.o
In file included from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_os.h:42:0,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rtmp_comm.h:56,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/rt_config.h:36,
                 from /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c:28:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c:1972:29: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/include/os/rt_linux.h:642:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_asic.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.o
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.c: In function ‘RTMPReadChannelPwr’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../chips/rtmp_chip.c:1336:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
  UCHAR  Tx2ALC = 0, Tx2FinePowerCtrl = 0;
  ^
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/connect.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.o
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlShow’:
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.c:4905:85: error: macro "__DATE__" might prevent reproducible builds [U][B][-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.c:4905:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                     ^[/B][/U]
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1396: recipe for target '_module_/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux' failed
make[1]: *** [_module_/home/muffintop/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-21-generic'
Makefile:372: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
```

Sorry if most of that wasnt needed, while new to Umbunu im also new to code.  I bolded and underlined what I think the issue stopping me from completing my task is.
 I've spent hours searching the web for fixes, one thing that came up that made sense was [this]("http://askubuntu.com/questions/593566/how-to-disable-werror-date-time-macro-date-might-prevent-reproducible-bui"): 
 
> The date-time warning is new in gcc 4.9 I think - it is possibly turned on implicitly by -Wall (and turned into an error implicitly by -Werror). 
 You could try turning it off explicitly using the -Wno- form i.e. by adding
  -Wno-error=date-time 
  to the CFLAGS.   
  
But i havent the slitest clue on what the CFLAGS is, or were to find it.
 If anyone can help, i'd be thankful :grin:

---

### Post by howefield on 2016-06-06
Thread moved to the "*Networking & Wireless*" forum.

---

