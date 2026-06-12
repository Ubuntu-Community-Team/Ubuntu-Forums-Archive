---
title: "Wireless driver unfindable ( ubuntu 14.04 LTS )"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by xrobot on 2015-09-24
[COLOR=#111111][FONT=Ubuntu]My OS is ubuntu 14.04 LTS 64bit and my wifi card is RT3290. I followed some guide on the internet but my wifi doesn't work. I have tryed these guides:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://www.dailylinuxnews.com/blog/2014/09/install-ralink-rt3290-wifi-driver-in-ubuntu-linuxmint-elementaryos/](http://www.dailylinuxnews.com/blog/2014/09/install-ralink-rt3290-wifi-driver-in-ubuntu-linuxmint-elementaryos/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][Wireless driver - how to load manufacturer's STA file (Ralink 3290)]("http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The last one return me these errors

```
[COLOR=#222222][FONT=Verdana]# make[/FONT][/COLOR][/FONT][/COLOR]
make -C tools
make[1]: ingresso nella directory "/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/tools"
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/tools/bin2h
cp -f os/linux/Makefile.6 /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/Makefile
make -C /lib/modules/3.19.0-28-generic/build SUBDIRS=/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.19.0-28-generic"
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_md5.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1466:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));
      ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1561:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.o
In file included from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42:0,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rt_config.h:36,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:30:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:529:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:463:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:530:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:463:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wep.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/action.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_data.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c: In function ‘rt28xx_init’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:162:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat=]
   DBGPRINT(RT_DEBUG_OFF,("PllCtrl:0x%x\n",PllCtrl.word));
   ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:178:10: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
          AUTO_WAKEUP_STRUC AutoWakeupCfg;
          ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_aes.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sync.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/eeprom.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_info.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c:1032:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_radar.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_channel.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_profile.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_asic.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ps.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/uapsd.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c:409:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/assoc.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sync.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sanity.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:766:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
     UCHAR uRSSI2;
     ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/connect.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/wpa.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:3956:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), pAd->CommonCfg.Channel));
    ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_private_get_statistics’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:7220:1: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘EEPROM_NIC_CONFIG3_STRUC’ [-Wformat=]
 sprintf(extra+strlen(extra), "pAd->NicConfig3.field.CoexAnt == 0x%x\n\n",pAd->NicConfig3);
 ^
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_os_util.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:18,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:18,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42:0,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:992:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:681:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1136:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1137:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o] Errore 1
make[1]: *** [_module_/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.19.0-28-generic"
make: *** [LINUX] Errore 2
root@ciaoatutti:/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508# make install
make -C /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux -f Makefile.6 install
mkdir: impossibile creare la directory "/etc/Wireless": File già esistente
make[1]: ingresso nella directory "/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux"
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3290sta.ko /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/
install: impossibile eseguire stat di "rt3290sta.ko": File o directory non esistente
make[1]: *** [install] Errore 1
make[1]: uscita dalla directory "/home/ciaoatutti/Scaricati/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux"
[COLOR=#111111][FONT=Ubuntu][COLOR=#222222][FONT=Verdana]make: *** [install] Errore 2[/FONT][/COLOR]
```
[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-09-24
You just might need to ```
sudo apt-get install linux-firmware
```

Reboot, if it doesn't work see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the script results

Thanks

---

### Post by xrobot on 2015-09-25
> **jeremy31 said:**
> You just might need to ```
sudo apt-get install linux-firmware
```

Reboot, if it doesn't work see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the script results

Thanks

```
# sudo apt-get install linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 52 not upgraded.


```

```
# sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://it.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://it.archive.ubuntu.com trusty-updates InRelease                      
Hit http://dl.google.com stable Release.gpg                                    
Ign http://it.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release                                        
Hit http://it.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://it.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://it.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://it.archive.ubuntu.com trusty Release                                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://it.archive.ubuntu.com trusty-updates Release                        
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://it.archive.ubuntu.com trusty-backports Release                      
Hit http://it.archive.ubuntu.com trusty/main Sources                           
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://it.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://it.archive.ubuntu.com trusty/universe Sources                       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://it.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://it.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://it.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://it.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://it.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://it.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://it.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://it.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://it.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://it.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://it.archive.ubuntu.com trusty/main Translation-it                    
Hit http://it.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://it.archive.ubuntu.com trusty/multiverse Translation-it              
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://it.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://dl.google.com stable/main Translation-it                            
Hit http://it.archive.ubuntu.com trusty/restricted Translation-it              
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Hit http://it.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://it.archive.ubuntu.com trusty/universe Translation-it    
Get:1 http://security.ubuntu.com trusty-security/main amd64 Packages [344 kB]
Hit http://it.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://it.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://it.archive.ubuntu.com trusty-updates/universe Sources            
Hit http://it.archive.ubuntu.com trusty-updates/multiverse Sources          
Hit http://it.archive.ubuntu.com trusty-updates/main amd64 Packages         
Hit http://it.archive.ubuntu.com trusty-updates/restricted amd64 Packages   
Hit http://it.archive.ubuntu.com trusty-updates/universe amd64 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                     
Hit http://it.archive.ubuntu.com trusty-updates/multiverse amd64 Packages   
Hit http://ppa.launchpad.net trusty/main i386 Packages                      
Get:2 http://it.archive.ubuntu.com trusty-updates/main i386 Packages [603 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://it.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://it.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://it.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://it.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://it.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://it.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://it.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:3 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8875 B]
Hit http://it.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://it.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://it.archive.ubuntu.com trusty-backports/universe Sources          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                     
Hit http://it.archive.ubuntu.com trusty-backports/multiverse Sources        
Hit http://it.archive.ubuntu.com trusty-backports/main amd64 Packages       
Hit http://ppa.launchpad.net trusty/main i386 Packages                      
Hit http://it.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://it.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ppa.launchpad.net trusty/main Translation-en            
Hit http://it.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com trusty-backports/main i386 Packages
Get:4 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Hit http://it.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://it.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://it.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://it.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://it.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://it.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://it.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:5 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3691 B]
Get:6 http://security.ubuntu.com trusty-security/main i386 Packages [329 kB]   
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it   
Get:7 http://security.ubuntu.com trusty-security/restricted i386 Packages [8846 B]
Get:8 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:9 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3833 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Fetched 982 kB in 5s (184 kB/s)
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.



```



```
# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk binutils e2fslibs e2fsprogs firefox firefox-locale-en
  firefox-locale-it gir1.2-gudev-1.0 google-chrome-stable irqbalance libblkid1
  libcomerr2 libcomerr2:i386 libgail-common libgail18 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libmount1 libpam-systemd
  libpython3.4 libpython3.4-minimal libpython3.4-stdlib libss2
  libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1
  libudev1:i386 libufe-xidgetter0 libuuid1 libuuid1:i386 lshw mount
  python3-apport python3-gdbm python3-problem-report python3.4
  python3.4-minimal systemd-services thermald udev util-linux uuid-runtime
  webaccounts-extension-common xserver-xorg-core-lts-vivid xul-ext-ubufox
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
52 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 104 MB of archives.
After this operation, 1037 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main e2fslibs amd64 1.42.9-3ubuntu1.3 [182 kB]
Get:2 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 45.0.2454.101-1 [47.4 MB]
Get:3 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main e2fsprogs amd64 1.42.9-3ubuntu1.3 [667 kB]
Get:4 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main mount amd64 2.20.1-5.1ubuntu20.7 [114 kB]
Get:5 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main util-linux amd64 2.20.1-5.1ubuntu20.7 [458 kB]
Get:6 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.7 [11.4 kB]
Get:7 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 amd64 2.20.1-5.1ubuntu20.7 [10.9 kB]
Get:8 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libblkid1 amd64 2.20.1-5.1ubuntu20.7 [62.6 kB]
Get:9 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libcomerr2 i386 1.42.9-3ubuntu1.3 [62.8 kB]
Get:10 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libcomerr2 amd64 1.42.9-3ubuntu1.3 [62.9 kB]
Get:11 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libmount1 amd64 2.20.1-5.1ubuntu20.7 [60.2 kB]
Get:12 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libss2 amd64 1.42.9-3ubuntu1.3 [67.1 kB]
Get:13 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4 amd64 3.4.3-1ubuntu1~14.04.1 [1305 kB]
Get:14 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main python3.4 amd64 3.4.3-1ubuntu1~14.04.1 [178 kB]
Get:15 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4-stdlib amd64 3.4.3-1ubuntu1~14.04.1 [1982 kB]
Get:16 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main python3.4-minimal amd64 3.4.3-1ubuntu1~14.04.1 [1224 kB]
Get:17 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4-minimal amd64 3.4.3-1ubuntu1~14.04.1 [463 kB]
Get:18 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main udev amd64 204-5ubuntu20.14 [735 kB]
Get:19 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 i386 204-5ubuntu20.14 [34.1 kB]
Get:20 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 amd64 204-5ubuntu20.14 [33.2 kB]
Get:21 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.14 [25.5 kB]
Get:22 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.14 [197 kB]
Get:23 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.14 [9680 B]
Get:24 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.14 [26.7 kB]
Get:25 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-common all 2.24.23-0ubuntu1.3 [121 kB]
Get:26 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-bin amd64 2.24.23-0ubuntu1.3 [9804 B]
Get:27 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgail-common amd64 2.24.23-0ubuntu1.3 [110 kB]
Get:28 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgail18 amd64 2.24.23-0ubuntu1.3 [14.1 kB]
Get:29 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk2.0-0 amd64 2.24.23-0ubuntu1.3 [1738 kB]
Get:30 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libgudev-1.0-0 amd64 1:204-5ubuntu20.14 [14.1 kB]
Get:31 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 amd64 204-5ubuntu20.14 [49.5 kB]
Get:32 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main irqbalance amd64 1.0.6-2ubuntu0.14.04.4 [30.7 kB]
Get:33 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main lshw amd64 02.16-2ubuntu1.3 [224 kB]
Get:34 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-gdbm amd64 3.4.3-1~14.04.2 [12.1 kB]
Get:35 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main uuid-runtime amd64 2.20.1-5.1ubuntu20.7 [12.3 kB]
Get:36 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.15 [9940 B]
Get:37 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apport all 2.14.1-0ubuntu3.15 [75.2 kB]
Get:38 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main apport all 2.14.1-0ubuntu3.15 [180 kB]
Get:39 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main apport-gtk all 2.14.1-0ubuntu3.15 [9552 B]
Get:40 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main binutils amd64 2.24-5ubuntu14 [2076 kB]
Get:41 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main xul-ext-webaccounts amd64 0.5-0ubuntu2.14.04.1 [2282 B]
Get:42 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main webaccounts-extension-common amd64 0.5-0ubuntu2.14.04.1 [8178 B]
Get:43 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main libufe-xidgetter0 amd64 3.0.0+14.04.20140416-0ubuntu1.14.04.1 [2762 B]
Get:44 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main xul-ext-websites-integration all 2.3.6+13.10.20130920.1-0ubuntu1.2 [4238 B]
Get:45 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main xul-ext-unity all 3.0.0+14.04.20140416-0ubuntu1.14.04.1 [1738 B]
Get:46 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox amd64 41.0+build3-0ubuntu0.14.04.1 [41.6 MB]
Get:47 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox-locale-en amd64 41.0+build3-0ubuntu0.14.04.1 [668 kB]
Get:48 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox-locale-it amd64 41.0+build3-0ubuntu0.14.04.1 [339 kB]
Get:49 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gudev-1.0 amd64 1:204-5ubuntu20.14 [5496 B]
Get:50 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main thermald amd64 1.4.3-5~14.04.1 [199 kB]
Get:51 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-core-lts-vivid amd64 2:1.17.1-0ubuntu3.1~trusty1 [1291 kB]
Get:52 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main xul-ext-ubufox all 3.2-0ubuntu0.14.04.1 [35.0 kB]
Fetched 104 MB in 2min 32s (683 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../e2fslibs_1.42.9-3ubuntu1.3_amd64.deb ...
Unpacking e2fslibs:amd64 (1.42.9-3ubuntu1.3) over (1.42.9-3ubuntu1.2) ...
Setting up e2fslibs:amd64 (1.42.9-3ubuntu1.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../e2fsprogs_1.42.9-3ubuntu1.3_amd64.deb ...
Unpacking e2fsprogs (1.42.9-3ubuntu1.3) over (1.42.9-3ubuntu1.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up e2fsprogs (1.42.9-3ubuntu1.3) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../mount_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking mount (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up mount (2.20.1-5.1ubuntu20.7) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../util-linux_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking util-linux (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up util-linux (2.20.1-5.1ubuntu20.7) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.7_amd64.deb ...
De-configuring libuuid1:i386 (2.20.1-5.1ubuntu20.6) ...
Unpacking libuuid1:amd64 (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.7_i386.deb ...
Unpacking libuuid1:i386 (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Preparing to unpack .../libblkid1_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking libblkid1:amd64 (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Setting up libuuid1:amd64 (2.20.1-5.1ubuntu20.7) ...
Setting up libuuid1:i386 (2.20.1-5.1ubuntu20.7) ...
Setting up libblkid1:amd64 (2.20.1-5.1ubuntu20.7) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../libcomerr2_1.42.9-3ubuntu1.3_amd64.deb ...
De-configuring libcomerr2:i386 (1.42.9-3ubuntu1.2) ...
Unpacking libcomerr2:amd64 (1.42.9-3ubuntu1.3) over (1.42.9-3ubuntu1.2) ...
Preparing to unpack .../libcomerr2_1.42.9-3ubuntu1.3_i386.deb ...
Unpacking libcomerr2:i386 (1.42.9-3ubuntu1.3) over (1.42.9-3ubuntu1.2) ...
Preparing to unpack .../libmount1_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking libmount1:amd64 (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Setting up libmount1:amd64 (2.20.1-5.1ubuntu20.7) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../libss2_1.42.9-3ubuntu1.3_amd64.deb ...
Unpacking libss2:amd64 (1.42.9-3ubuntu1.3) over (1.42.9-3ubuntu1.2) ...
Setting up libcomerr2:amd64 (1.42.9-3ubuntu1.3) ...
Setting up libcomerr2:i386 (1.42.9-3ubuntu1.3) ...
Setting up libss2:amd64 (1.42.9-3ubuntu1.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 252157 files and directories currently installed.)
Preparing to unpack .../libpython3.4_3.4.3-1ubuntu1~14.04.1_amd64.deb ...
Unpacking libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.1) over (3.4.0-2ubuntu1.1) ...
Preparing to unpack .../python3.4_3.4.3-1ubuntu1~14.04.1_amd64.deb ...
Unpacking python3.4 (3.4.3-1ubuntu1~14.04.1) over (3.4.0-2ubuntu1.1) ...
Preparing to unpack .../libpython3.4-stdlib_3.4.3-1ubuntu1~14.04.1_amd64.deb ...
Unpacking libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.1) over (3.4.0-2ubuntu1.1) ...
Preparing to unpack .../python3.4-minimal_3.4.3-1ubuntu1~14.04.1_amd64.deb ...
Unpacking python3.4-minimal (3.4.3-1ubuntu1~14.04.1) over (3.4.0-2ubuntu1.1) ...
Preparing to unpack .../libpython3.4-minimal_3.4.3-1ubuntu1~14.04.1_amd64.deb ...
Unpacking libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.1) over (3.4.0-2ubuntu1.1) ...
Preparing to unpack .../udev_204-5ubuntu20.14_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libudev1_204-5ubuntu20.14_i386.deb ...
De-configuring libudev1:amd64 (204-5ubuntu20.13) ...
Unpacking libudev1:i386 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libudev1_204-5ubuntu20.14_amd64.deb ...
Unpacking libudev1:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.14_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.14_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.14_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.14_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../libgtk2.0-common_2.24.23-0ubuntu1.3_all.deb ...
Unpacking libgtk2.0-common (2.24.23-0ubuntu1.3) over (2.24.23-0ubuntu1.2) ...
Preparing to unpack .../libgtk2.0-bin_2.24.23-0ubuntu1.3_amd64.deb ...
Unpacking libgtk2.0-bin (2.24.23-0ubuntu1.3) over (2.24.23-0ubuntu1.2) ...
Preparing to unpack .../libgail-common_2.24.23-0ubuntu1.3_amd64.deb ...
Unpacking libgail-common:amd64 (2.24.23-0ubuntu1.3) over (2.24.23-0ubuntu1.2) ...
Preparing to unpack .../libgail18_2.24.23-0ubuntu1.3_amd64.deb ...
Unpacking libgail18:amd64 (2.24.23-0ubuntu1.3) over (2.24.23-0ubuntu1.2) ...
Preparing to unpack .../libgtk2.0-0_2.24.23-0ubuntu1.3_amd64.deb ...
Unpacking libgtk2.0-0:amd64 (2.24.23-0ubuntu1.3) over (2.24.23-0ubuntu1.2) ...
Preparing to unpack .../google-chrome-stable_45.0.2454.101-1_amd64.deb ...
Unpacking google-chrome-stable (45.0.2454.101-1) over (45.0.2454.93-1) ...
Preparing to unpack .../libgudev-1.0-0_1%3a204-5ubuntu20.14_amd64.deb ...
Unpacking libgudev-1.0-0:amd64 (1:204-5ubuntu20.14) over (1:204-5ubuntu20.13) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.14_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../irqbalance_1.0.6-2ubuntu0.14.04.4_amd64.deb ...
irqbalance stop/waiting
Unpacking irqbalance (1.0.6-2ubuntu0.14.04.4) over (1.0.6-2ubuntu0.14.04.3) ...
Preparing to unpack .../lshw_02.16-2ubuntu1.3_amd64.deb ...
Unpacking lshw (02.16-2ubuntu1.3) over (02.16-2ubuntu1.2) ...
Preparing to unpack .../python3-gdbm_3.4.3-1~14.04.2_amd64.deb ...
Unpacking python3-gdbm:amd64 (3.4.3-1~14.04.2) over (3.4.0-0ubuntu1) ...
Preparing to unpack .../uuid-runtime_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking uuid-runtime (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.15_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.13) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.15_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.13) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.15_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.13) ...
Preparing to unpack .../apport-gtk_2.14.1-0ubuntu3.15_all.deb ...
Unpacking apport-gtk (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.13) ...
Preparing to unpack .../binutils_2.24-5ubuntu14_amd64.deb ...
Unpacking binutils (2.24-5ubuntu14) over (2.24-5ubuntu13) ...
Preparing to unpack .../xul-ext-webaccounts_0.5-0ubuntu2.14.04.1_amd64.deb ...
Unpacking xul-ext-webaccounts (0.5-0ubuntu2.14.04.1) over (0.5-0ubuntu2) ...
Preparing to unpack .../webaccounts-extension-common_0.5-0ubuntu2.14.04.1_amd64.deb ...
Unpacking webaccounts-extension-common (0.5-0ubuntu2.14.04.1) over (0.5-0ubuntu2) ...
Preparing to unpack .../libufe-xidgetter0_3.0.0+14.04.20140416-0ubuntu1.14.04.1_amd64.deb ...
Unpacking libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1.14.04.1) over (3.0.0+14.04.20140416-0ubuntu1) ...
Preparing to unpack .../xul-ext-websites-integration_2.3.6+13.10.20130920.1-0ubuntu1.2_all.deb ...
Unpacking xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1.2) over (2.3.6+13.10.20130920.1-0ubuntu1.1) ...
Preparing to unpack .../xul-ext-unity_3.0.0+14.04.20140416-0ubuntu1.14.04.1_all.deb ...
Unpacking xul-ext-unity (3.0.0+14.04.20140416-0ubuntu1.14.04.1) over (3.0.0+14.04.20140416-0ubuntu1) ...
Preparing to unpack .../firefox_41.0+build3-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox (41.0+build3-0ubuntu0.14.04.1) over (40.0.3+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-en_41.0+build3-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox-locale-en (41.0+build3-0ubuntu0.14.04.1) over (40.0.3+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-it_41.0+build3-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox-locale-it (41.0+build3-0ubuntu0.14.04.1) over (40.0.3+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../gir1.2-gudev-1.0_1%3a204-5ubuntu20.14_amd64.deb ...
Unpacking gir1.2-gudev-1.0 (1:204-5ubuntu20.14) over (1:204-5ubuntu20.13) ...
Preparing to unpack .../thermald_1.4.3-5~14.04.1_amd64.deb ...
thermald stop/waiting
Unpacking thermald (1.4.3-5~14.04.1) over (1.4.3-3~14.04.1) ...
Preparing to unpack .../xserver-xorg-core-lts-vivid_2%3a1.17.1-0ubuntu3.1~trusty1_amd64.deb ...
Unpacking xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) over (2:1.17.1-0ubuntu3~trusty1) ...
Preparing to unpack .../xul-ext-ubufox_3.2-0ubuntu0.14.04.1_all.deb ...
Unpacking xul-ext-ubufox (3.2-0ubuntu0.14.04.1) over (3.1-0ubuntu0.14.04.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Setting up libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.1) ...
Setting up libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.1) ...
Setting up libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.1) ...
Setting up python3.4-minimal (3.4.3-1ubuntu1~14.04.1) ...
Setting up python3.4 (3.4.3-1ubuntu1~14.04.1) ...
Setting up libudev1:amd64 (204-5ubuntu20.14) ...
Setting up libudev1:i386 (204-5ubuntu20.14) ...
Setting up udev (204-5ubuntu20.14) ...
udev stop/waiting
udev start/running, process 7415
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.14) ...
Setting up systemd-services (204-5ubuntu20.14) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.14) ...
systemd-logind start/running, process 7487
Setting up libsystemd-login0:amd64 (204-5ubuntu20.14) ...
Setting up libgtk2.0-common (2.24.23-0ubuntu1.3) ...
Setting up libgtk2.0-0:amd64 (2.24.23-0ubuntu1.3) ...
Setting up libgtk2.0-bin (2.24.23-0ubuntu1.3) ...
Setting up libgail18:amd64 (2.24.23-0ubuntu1.3) ...
Setting up libgail-common:amd64 (2.24.23-0ubuntu1.3) ...
Setting up google-chrome-stable (45.0.2454.101-1) ...
Setting up libgudev-1.0-0:amd64 (1:204-5ubuntu20.14) ...
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.14) ...
Setting up irqbalance (1.0.6-2ubuntu0.14.04.4) ...
irqbalance start/running, process 7820
Setting up lshw (02.16-2ubuntu1.3) ...
Setting up python3-gdbm:amd64 (3.4.3-1~14.04.2) ...
Setting up uuid-runtime (2.20.1-5.1ubuntu20.7) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.15) ...
Setting up python3-apport (2.14.1-0ubuntu3.15) ...
Setting up apport (2.14.1-0ubuntu3.15) ...
apport start/running
Setting up apport-gtk (2.14.1-0ubuntu3.15) ...
Setting up binutils (2.24-5ubuntu14) ...
Setting up webaccounts-extension-common (0.5-0ubuntu2.14.04.1) ...
Setting up xul-ext-webaccounts (0.5-0ubuntu2.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1.14.04.1) ...
Setting up xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up xul-ext-unity (3.0.0+14.04.20140416-0ubuntu1.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox (41.0+build3-0ubuntu0.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (41.0+build3-0ubuntu0.14.04.1) ...
Setting up firefox-locale-it (41.0+build3-0ubuntu0.14.04.1) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.14) ...
Setting up thermald (1.4.3-5~14.04.1) ...
thermald start/running, process 7963
Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
Setting up xul-ext-ubufox (3.2-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-28-generic



```

Rebooted and doesn't work.
Now I am trying the wireless info script.

---

### Post by xrobot on 2015-10-27
Hello, This is the result of the script: [http://paste.ubuntu.com/12981432/](http://paste.ubuntu.com/12981432/)

---

### Post by jeremy31 on 2015-11-12
The kernel modules that should make it work are blacklisted
```
sudo rm /etc/modprobe.d/blacklist-ralink.conf
```

And lets blacklist the other module
```
echo "blacklist rt3290sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by xrobot on 2015-11-19
> **jeremy31 said:**
> The kernel modules that should make it work are blacklisted
```
sudo rm /etc/modprobe.d/blacklist-ralink.conf
```

And lets blacklist the other module
```
echo "blacklist rt3290sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot


I get an error:

```
# sudo rm /etc/modprobe.d/blacklist-ralink.conf
rm: [FONT=Consolas]cannot remove [/FONT]"/etc/modprobe.d/blacklist-ralink.conf":[FONT=Consolas] No such file or directory[/FONT]

```

---

### Post by jeremy31 on 2015-11-19
Run the wireless script again and post new results as your original script report showed
```
[COLOR=#000000][/etc/modprobe.d/blacklist-ralink.conf]
[/COLOR]blacklist rt2800pci
blacklist rt2x00pci

```

---

### Post by xrobot on 2015-11-23
> **jeremy31 said:**
> Run the wireless script again and post new results as your original script report showed
```
[COLOR=#000000][/etc/modprobe.d/blacklist-ralink.conf]
[/COLOR]blacklist rt2800pci
blacklist rt2x00pci

```

[http://paste.ubuntu.com/13476703/](http://paste.ubuntu.com/13476703/)

Thanks

---

### Post by xrobot on 2015-11-27
up

---

### Post by jeremy31 on 2015-11-27
See if changing to channel 13 helps, then go into Network Manager and set IPv6 to ignore.  Then we can set the country code with ```
sudo iw reg set IT
```

From the last script results it appears to be working and connected

---

### Post by xrobot on 2016-01-29
I have just done an update and now wifi doesn't work anymore.
This is the result of the script:
[http://paste.ubuntu.com/14702284/](http://paste.ubuntu.com/14702284/)

---

### Post by praseodym on 2016-01-29
> ```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR] 
```
The card is turned off. Any button, switch key or key combo?

---

