---
title: "PCE-n53 Not installing"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by Thugkitty on 2015-12-04
Not sure what else to do but here is my log.. 

```
thugkitty@thugkitty-MS-7721:~$ sudo apt-get install linux-headers-generic
[sudo] password for thugkitty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thugkitty@thugkitty-MS-7721:~$ cd'/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326' 
bash: cd/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326: No such file or directory
thugkitty@thugkitty-MS-7721:~$ cd '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326' 
thugkitty@thugkitty-MS-7721:~/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ sudo su
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
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
make[1]: Leaving directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf os/linux/Makefile
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# make
make -C tools
make[1]: Entering directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
cp -f os/linux/Makefile.6 /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile
make -C /lib/modules/4.2.0-19-generic/build SUBDIRS=/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-19-generic'
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_md5.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.o
In file included from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_aes.h:31,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:28:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1459:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:665:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1459:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1554:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:665:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1554:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.o
In file included from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:28:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:527:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:472:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:528:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:472:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
In file included from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/mac_pci.h:33:0,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_chip.h:37,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:38,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:28:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c: In function &#8216;RTMPAdjustFrequencyOffset&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:583:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;FreqOffset&#8217; will never be NULL [-Waddress]
  if (_pVal1 != NULL)        \
             ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;HighCurrentBit&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wep.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/action.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_init.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_aes.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_sync.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/eeprom.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_info.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.o
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_radar.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.o
In file included from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:28:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:1972:29: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:665:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro &#8216;DBGPRINT&#8217;
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rt_channel.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_profile.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.o
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_T
                            ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_T
                            ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/ps.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/uapsd.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/assoc.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/auth.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sync.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sanity.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.o
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/connect.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/wpa.o
  CC [M]  /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o
In file included from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:28:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3953:30: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:665:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3953:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPIoctlShow&#8217;:
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:4896:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1398: recipe for target '_module_/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux' failed
make[1]: *** [_module_/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-19-generic'
Makefile:381: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# make install
make -C /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;rt5592sta.ko&#8217;: No such file or directory
Makefile.6:294: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
Makefile:474: recipe for target 'install' failed
make: *** [install] Error 2
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# '/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/Makefile' 
bash: /home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/Makefile: Permission denied
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# ^C
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# ^C
root@thugkitty-MS-7721:/home/thugkitty/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326# 

```

This is were i got all my info from: [http://ubuntuforums.org/showthread.php?t=2203226&page=2](http://ubuntuforums.org/showthread.php?t=2203226&page=2)

---

### Post by Thugkitty on 2015-12-05
update

```
thugkitty@thugkitty-MS-7721:~$ sudo iwconfig wlan0 power off
[sudo] password for thugkitty: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
thugkitty@thugkitty-MS-7721:~$ echo 'install rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > /sys/bus/pci/drivers/rt2800pci/new_id' | sudo tee /etc/modprobe.d/rt2800pci.conf
install rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > /sys/bus/pci/drivers/rt2800pci/new_id
thugkitty@thugkitty-MS-7721:~$ sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
linux-headers-4.2.0-19-generic is already the newest version.
linux-headers-4.2.0-19-generic set to manually installed.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
thugkitty@thugkitty-MS-7721:~$ wget http://www.elektronenblitz63.de/downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
--2015-12-04 23:55:58--  http://www.elektronenblitz63.de/downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
Resolving www.elektronenblitz63.de (www.elektronenblitz63.de)... 82.165.83.231
Connecting to www.elektronenblitz63.de (www.elektronenblitz63.de)|82.165.83.231|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.elektronenblitz63.de/download/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz [following]
--2015-12-04 23:55:58--  http://www.elektronenblitz63.de/download/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
Reusing existing connection to www.elektronenblitz63.de:80.
HTTP request sent, awaiting response... 404 Not Found
2015-12-04 23:55:58 ERROR 404: Not Found.

thugkitty@thugkitty-MS-7721:~$  wget http://dlcdnet.asus.com/pub/ASUS/wirele … 3_1008.zip
--2015-12-04 23:57:31--  http://dlcdnet.asus.com/pub/ASUS/wirele
Resolving dlcdnet.asus.com (dlcdnet.asus.com)... 23.205.120.57, 23.205.120.33
Connecting to dlcdnet.asus.com (dlcdnet.asus.com)|23.205.120.57|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2015-12-04 23:57:32 ERROR 404: Not Found.

idn_encode failed (3): ‘Non-digit/letter/hyphen in input’
--2015-12-04 23:57:32--  http://%E2%80%A6/
Resolving … (…)... failed: Name or service not known.
wget: unable to resolve host address ‘…’
idn_encode failed (3): ‘Non-digit/letter/hyphen in input’
--2015-12-04 23:57:32--  http://%E2%80%A6/
Resolving … (…)... failed: Name or service not known.
wget: unable to resolve host address ‘…’
--2015-12-04 23:57:33--  http://3_1008.zip/
Resolving 3_1008.zip (3_1008.zip)... 127.0.53.53
Connecting to 3_1008.zip (3_1008.zip)|127.0.53.53|:80... failed: Connection refused.
thugkitty@thugkitty-MS-7721:~$ cd Linux
bash: cd: Linux: No such file or directory
thugkitty@thugkitty-MS-7721:~$ wget http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch
--2015-12-04 23:58:29--  http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch
Resolving gridlox.net (gridlox.net)... 70.114.175.247
Connecting to gridlox.net (gridlox.net)|70.114.175.247|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12300 (12K) [text/x-diff]
Saving to: ‘rt5592sta_fix_64bit_3.15.patch’

rt5592sta_fix_64bit 100%[=====================>]  12.01K  --.-KB/s   in 0.003s 

2015-12-04 23:58:29 (4.17 MB/s) - ‘rt5592sta_fix_64bit_3.15.patch’ saved [12300/12300]

thugkitty@thugkitty-MS-7721:~$ cd '/home/thugkitty/Desktop/Linux' 
thugkitty@thugkitty-MS-7721:~/Desktop/Linux$ DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2: command not found
thugkitty@thugkitty-MS-7721:~/Desktop/Linux$ tar -xvjpf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/rate_ctrl/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/rate_ctrl/alg_legacy.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/rate_ctrl/alg_ags.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/rate_ctrl/ra_ctrl.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/rate_ctrl/alg_grp.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/Makefile
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STACard.dat
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta_ate_iwpriv_usage.txt
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/rtmp_chip.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/rt3290.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/rt5592.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/rt30xx.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/chips/rt28xx.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/Makefile
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/iwpriv_usage.txt
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.ap.soc
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/vr_bdlt.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.4.netif
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_linux_symb.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.ap.usb
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/br_ftph.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_pci_rbus.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_proc.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/config.mk
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_profile.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_linux.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/pci_main_dev.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_rbus_pci_drv.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/inf_ppa.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/cfg80211.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_main_dev.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.4
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Kconfig.ap.soc
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.4.util
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/cfg80211drv.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.6.util
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.6
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_symb.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/vr_ikans.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/sta_ioctl.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Kconfig.ap.usb
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.libautoprovision.6
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.6.netif
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.clean
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt_rbus_pci_util.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile.sta.soc
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Kconfig.sta.soc
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rtmp_init_inf.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_video.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/crypt_aes.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_aes.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rt_rf.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_wpa.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_asic.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/ee_prom.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/crypt_arc4.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/eeprom.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_mac_pci.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_sync.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/frq_cal.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/crypt_sha2.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rtmp_mcu.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_cfg.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_radar.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/spectrum.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/crypt_md5.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/ba_action.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_cs.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/ps.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/ee_efuse.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_data.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/misc.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rt2860.bin
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rt_led.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/netif_block.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/client_wds.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/mlme.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rtmp_timer.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_cmd.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rt_channel.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rtmp_init.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_tkip.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/action.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_data_pci.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_wep.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_profile.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_info.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/cmm_sanity.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/rt_os_util.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/uapsd.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/common/crypt_hmac.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_iface.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/eeprom.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_sha2.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_timer.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/sta_cfg.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chlist.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/video.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_chip.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_def.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/netif_block.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/frq_cal.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/spectrum_def.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_dot11.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_mcu.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/br_ftph.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/cs.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_type.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/spectrum.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_aes.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/action.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rt5592.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rt3290.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/mac_pci.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_mac.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/chip_id.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rt28xx.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rt30xx.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_txbf.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/ap_diversity.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/wsc.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/uapsd.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_drv.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux_cmm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_os.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/vrut_ubm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_hmac.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/drs_extr.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/cfg80211.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/ap.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_os_net.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/mlme.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_arc4.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/wpa_cmm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/cfg80211extr.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/firmware.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/radar.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/oid.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_cmd.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/dfs.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/wpa.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_led.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/iface/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/iface/iface_util.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/iface/rtmp_pci.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/dot11i_wpa.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/vr_ikans.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_md5.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_os_util.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_osabl.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/misc.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/misc_cmm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/client_wds_cmm.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/client_wds.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/ags.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/link_list.h
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/auth_rsp.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/auth.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/sta_cfg.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/assoc.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/sync.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/wpa.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/sanity.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/rtmp_ckipmic.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/connect.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/rtmp_data.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/sta/dls.c
DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/README_STA_pci
thugkitty@thugkitty-MS-7721:~/Desktop/Linux$ d DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
d: command not found
thugkitty@thugkitty-MS-7721:~/Desktop/Linux$ cd DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ wget http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch
--2015-12-05 00:02:29--  http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch
Resolving gridlox.net (gridlox.net)... 70.114.175.247
Connecting to gridlox.net (gridlox.net)|70.114.175.247|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12300 (12K) [text/x-diff]
Saving to: ‘rt5592sta_fix_64bit_3.15.patch’

rt5592sta_fix_64bit 100%[=====================>]  12.01K  --.-KB/s   in 0.005s 

2015-12-05 00:02:29 (2.22 MB/s) - ‘rt5592sta_fix_64bit_3.15.patch’ saved [12300/12300]

thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ patch -p1 < rt5592sta_fix_64bit_3.15.patch
patching file Makefile
patching file include/os/rt_linux.h
patching file os/linux/Makefile.4
patching file os/linux/Makefile.4.netif
patching file os/linux/Makefile.4.util
patching file os/linux/Makefile.6
patching file os/linux/Makefile.6.netif
patching file os/linux/Makefile.6.util
patching file os/linux/pci_main_dev.c
patching file os/linux/rt_linux.c
patching file sta/sta_cfg.c
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ make
make -C tools
make[1]: Entering directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
cp -f os/linux/Makefile.6 /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile
make -C /lib/modules/4.2.0-19-generic/build SUBDIRS=/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-19-generic'
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_md5.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.o
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/crypt_aes.h:31,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1459:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1459:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1554:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_aes.c:1554:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.o
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:527:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:477:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:528:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:477:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/mac_pci.h:33:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_chip.h:37,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:38,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c: In function ‘RTMPAdjustFrequencyOffset’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:583:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘FreqOffset’ will never be NULL [-Waddress]
  if (_pVal1 != NULL)        \
             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘HighCurrentBit’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wep.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/action.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_init.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_aes.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_sync.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/eeprom.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_info.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_radar.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.o
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:1972:29: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rt_channel.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_profile.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c: In function ‘AsicGetAutoAgcOffsetForTemperatureSensor’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_T
                            ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_T
                            ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/ps.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/uapsd.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_profile.o
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_profile.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_profile.c:411:35: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
                                   ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_profile.c:411:9: note: in expansion of macro ‘DBGPRINT’
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
         ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/assoc.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/auth.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sync.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sanity.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/connect.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/wpa.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:29:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3954:30: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.c:3954:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rt_os_util.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/ba_action.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/dls.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rt_led.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data_pci.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPFreeTXDUponTxDmaDone’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPHandleMgmtRingDmaDoneInterrupt’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_data_pci.c:735:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function ‘RTMPInitPCIeDevice’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_rbus_pci_drv.c:1382:23: warning: unused variable ‘Index’ [-Wunused-variable]
   UINT32 MacCsr0 = 0, Index= 0;
                       ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/ee_prom.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.o
In file included from include/linux/list.h:8:0,
                 from include/linux/module.h:9,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:31,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibrationMode’:
include/linux/kernel.h:722:17: warning: comparison of distinct pointer types lacks a cast
  (void) (&_min1 == &_min2);  \
                 ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.c:128:13: note: in expansion of macro ‘min’
   RFValue = min(RFValue, 0x5F);
             ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/mac_pci.h:33:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_chip.h:37,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:38,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘RfReg’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:592:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/frq_cal.c:141:3: note: in expansion of macro ‘RF_M_WRITE8’
   RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);  
   ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/ee_efuse.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:558:72: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Wincompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:41:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:887:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:578:72: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Wincompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:41:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:887:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rt_rf.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt30xx.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt30xx.c: In function ‘RT30xxLoadRFSleepModeSetup’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt30xx.c:477:9: warning: unused variable ‘MACValue’ [-Wunused-variable]
  UINT32 MACValue;
         ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt30xx.c: In function ‘RT30xxReverseRFSleepModeSetup’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt30xx.c:515:9: warning: unused variable ‘MACValue’ [-Wunused-variable]
  UINT32 MACValue;
         ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:120:26: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR *RF5592Reg_5G = RF5592Reg_5G_Default;
                          ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:179:42: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR_CHANNEL *RF5592Reg_Channel_5G = RF5592Reg_Channel_5G_Default;
                                          ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/mac_pci.h:33:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_chip.h:37,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:38,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c: In function ‘RT5592_ChipSwitchChannel’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘RfReg’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/chip/rtmp_phy.h:592:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:1985:4: note: in expansion of macro ‘RF_M_WRITE8’
    RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c: At top level:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:2223:17: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  .pRFRegTable = RF5592Reg_2G_5G,
                 ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../chips/rt5592.c:857:13: warning: ‘RT5592FilterCalibration’ defined but not used [-Wunused-function]
 static VOID RT5592FilterCalibration(IN PRTMP_ADAPTER pAd)
             ^
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/pci_main_dev.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/pci_main_dev.c:334:13: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  print_name = pci_name(pci_dev);
             ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/pci_main_dev.c: At top level:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/pci_main_dev.c:481:13: warning: ‘rt2860_remove_one’ defined but not used [-Wunused-function]
 static VOID rt2860_remove_one(
             ^
  LD [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.o
see include/linux/module.h for more information
  CC      /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.mod.o
  LD [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-19-generic'
cp -f /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.ko /tftpboot
cp: cannot create regular file ‘/tftpboot’: Permission denied
Makefile:384: recipe for target 'LINUX' failed
make: *** [LINUX] Error 1
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ make install
make -C /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: Permission denied
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
mkdir: cannot create directory ‘/etc/Wireless/RT2860STA’: No such file or directory
Makefile.6:297: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
Makefile:477: recipe for target 'install' failed
make: *** [install] Error 2
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ modprobe rt5592sta
modprobe: FATAL: Module rt5592sta not found.
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ sudo make
make -C tools
make[1]: Entering directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
cp -f os/linux/Makefile.6 /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile
make -C /lib/modules/4.2.0-19-generic/build SUBDIRS=/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-19-generic'
  CC [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.o
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:558:72: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Wincompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:41:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:887:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:578:72: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Wincompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:41:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:887:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rt_config.h:33,
                 from /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:28:
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
  LD [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.o
see include/linux/module.h for more information
  LD [M]  /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-19-generic'
cp -f /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/rt5592sta.ko /tftpboot
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ sudo make install
make -C /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.2.0-19-generic
make[1]: Leaving directory '/home/thugkitty/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ modprobe rt5592sta
modprobe: ERROR: could not insert 'rt5592sta': Operation not permitted
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ sudo modprobe rt5592sta
thugkitty@thugkitty-MS-7721:~/Desktop/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326$ 


```

Going to restart my computer will let you know if works or not.

---

### Post by Thugkitty on 2015-12-05
It worked!

---

