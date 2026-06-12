---
title: "how to install RT2870 drivers in ubuntu 14.04"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by jose105 on 2016-03-30
hi, i bought one of these wireless  ralink rt2870  usb adapters from ebay.the driver provided in the CD showed errors so i downloaded a new one and followed the steps from one of the threats "Thread: [RT2870 drivers in Ubuntu 12.04LTS]("http://ubuntuforums.org/showthread.php?t=2210930")" answered by [chili555]("http://ubuntuforums.org/member.php?u=35909").Every thing went OK up to 

sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913

when i run 

make
sudo make install
 
it shows errors as one file is missing i cant understand it.None of the solutions on the forum works. 
Please help me out and really fast ,as if not working i like to claim my money back from ebay
i will post the entire terminal process here;


```
  	 	 	 	   ben@ben-H81M-S:~$ lsusb  

 Bus 002 Device 002: ID 8087:8000 Intel Corp.  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 002: ID 8087:8008 Intel Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
 Bus 003 Device 007: ID 14cd:1212 Super Top microSD card reader (SY-T18)  

 Bus 003 Device 006: ID 12d1:1436 Huawei Technologies Co., Ltd. Broadband stick  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 ben@ben-H81M-S:~$ uname -r  
 3.13.0-83-generic  
 ben@ben-H81M-S:~$ sudo apt-get install linux-headers-generic build-essential  
 [sudo] password for ben:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 build-essential is already the newest version.  
 linux-headers-generic is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.  
 ben@ben-H81M-S:~$ cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913  
 ben@ben-H81M-S:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ make  
 make -C tools  
 make[1]: Entering directory `/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'  
 gcc -g bin2h.c -o bin2h  
 make[1]: Leaving directory `/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h 
 cp -f os/linux/Makefile.6 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile 
 make -C /lib/modules/3.13.0-83-generic/build SUBDIRS=/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules  
 make[1]: Entering directory `/usr/src/linux-headers-3.13.0-83-generic'  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function &#8216;announce_802_3_packet&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:331:16: warning: unused variable &#8216;pAd&#8217; [-Wunused-variable]  
   RTMP_ADAPTER *pAd = (RTMP_ADAPTER *)pAdSrc;  
                 ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:399:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]  
          DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));  
          ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/assoc.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth_rsp.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:2181:12: warning: passing argument 8 of &#8216;StaAddMacTableEntry&#8217; from incompatible pointer type [enabled by default]  
             ie_list->CapabilityInfo) == FALSE)  
             ^  
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:28: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:7892:9: note: expected &#8216;struct IE_LISTS *&#8217; but argument is of type &#8216;struct BCN_IE_LIST *&#8217;  
  BOOLEAN StaAddMacTableEntry(  
          ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sanity.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:523:4: warning: passing argument 2 of &#8216;MacTableLookup&#8217; from incompatible pointer type [enabled by default]  
     pEntry = MacTableLookup(pAd, &pHeader->Addr2);  
     ^  
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:28: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:8429:18: note: expected &#8216;UCHAR *&#8217; but argument is of type &#8216;UCHAR (*)[6]&#8217; 
  MAC_TABLE_ENTRY *MacTableLookup(RTMP_ADAPTER *pAd, UCHAR *pAddr);  
                   ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/connect.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/wpa.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPIoctlRF&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5306:7: warning: format &#8216;%X&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 5 has type &#8216;LONG&#8217; [-Wformat=]  
        sprintf(msg+strlen(msg), "BANK%d_R%02d:%02X  ", bank_Id, rfId, rfValue);  
        ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5359:3: warning: passing argument 2 of &#8216;RtmpDrvAllRFPrint&#8217; from incompatible pointer type [enabled by default]  
    RtmpDrvAllRFPrint(NULL, msg, strlen(msg));  
    ^  
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:64:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:28: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_os_util.h:668:6: note: expected &#8216;UINT32 *&#8217; but argument is of type &#8216;PSTRING&#8217;  
  VOID RtmpDrvAllRFPrint(  
       ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5209:22: warning: unused variable &#8216;rf_bank&#8217; [-Wunused-variable]  
   UCHAR    regRF = 0, rf_bank = 0;  
                       ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function &#8216;RtmpIoctl_rt_ioctl_siwgenie&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:7610:13: warning: assignment from incompatible pointer type [enabled by default]  
      eid_ptr = pAd->StaCfg.pWpaAssocIe;  
              ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_md5.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_sha2.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_hmac.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1459:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]  
       DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));  
       ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1554:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]  
       DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));  
       ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_arc4.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.o 
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:33, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:28: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:544:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]  
        (UINT32)&pAd->RalinkCounters.OneSecEnd -  
        ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:473:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;  
  #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)  
                                                                             ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:545:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]  
        (UINT32)&pAd->RalinkCounters.OneSecStart);  
        ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:473:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;  
  #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)  
                                                                             ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function &#8216;AsicRxAntEvalTimeout&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:5201:45: warning: unused variable &#8216;rssi_diff&#8217; [-Wunused-variable]  
   CHAR   larger = -127, rssi0, rssi1, rssi2, rssi_diff;  
                                              ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wep.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/action.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function &#8216;CmdRspEventCallbackHandle&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2509:8: warning: unused variable &#8216;Ret&#8217; [-Wunused-variable]  
   INT32 Ret;  
         ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function &#8216;StopDmaTx&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2684:8: warning: unused variable &#8216;IdleNums&#8217; [-Wunused-variable]  
   UINT8 IdleNums = 0;  
         ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2682:20: warning: unused variable &#8216;UsbCfg&#8217; [-Wunused-variable]  
   USB_DMA_CFG_STRUC UsbCfg;  
                     ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitAsicFromEEPROM&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:981:9: warning: unused variable &#8216;i&#8217; [-Wunused-variable]  
   USHORT i;  
          ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAdapter&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1292:22: warning: unused variable &#8216;GloCfg&#8217; [-Wunused-variable]  
   WPDMA_GLO_CFG_STRUC GloCfg;  
                       ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAsic&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1367:11: warning: unused variable &#8216;KeyIdx&#8217; [-Wunused-variable]  
   USHORT   KeyIdx;  
            ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1656:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]  
  }  
  ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init_inf.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_tkip.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_aes.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sync.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c: In function &#8216;RtmpChipOpsEepromHook&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c:34:9: warning: unused variable &#8216;e2p_csr&#8217; [-Wunused-variable]  
   UINT32 e2p_csr;  
          ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sanity.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function &#8216;Set_DebugFunc_Proc&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;const char *&#8217; [-Wformat=]  
   DBGPRINT_S(RT_DEBUG_TRACE, ("Set RTDebugFunc = 0x%x\n",__FUNCTION__, RTDebugFunc));  
   ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: too many arguments for format [-Wformat-extra-args]  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function &#8216;set_rf&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:5730:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int *&#8217;, but argument 5 has type &#8216;UCHAR *&#8217; [-Wformat=]  
    rv = sscanf(arg, "%d-%d-%x", &(bank_id), &(rf_id), &(rf_val));  
    ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: In function &#8216;wmode_valid_and_correct&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:279:8: warning: unused variable &#8216;mode&#8217; [-Wunused-variable]  
   UCHAR mode = *wmode;  
         ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: At top level:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:264:16: warning: &#8216;wmode_valid&#8217; defined but not used [-Wunused-function]  
  static BOOLEAN wmode_valid(RTMP_ADAPTER *pAd, enum WIFI_MODE wmode)  
                 ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wpa.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_radar.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c:1972:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]  
    DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));  
    ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_timer.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_channel.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c: In function &#8216;rtmp_read_multest_from_file&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c:2671:23: warning: unused variable &#8216;pWdsEntry&#8217; [-Wunused-variable]  
   PRT_802_11_WDS_ENTRY pWdsEntry;  
                        ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_asic.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/scan.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cmd.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/uapsd.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ps.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/ra_ctrl.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_legacy.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_ags.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/rtmp_chip.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/txpower.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mac/rtmp_mac.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_hw.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_entrytb.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c: In function &#8216;NICInitBBP&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c:61:8: warning: unused variable &#8216;R0&#8217; [-Wunused-variable]  
   UCHAR R0 = 0xff;  
         ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_phy.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_rf.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.o 
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:33, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c:30: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]  
    ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))  
                                   ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:929:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;  
   SET_OS_PKT_DATATAIL(__pRxPkt, __pData, __DataSize);      \  
   ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c:1574:2: note: in expansion of macro &#8216;RTMP_OS_PKT_INIT&#8217;  
   RTMP_OS_PKT_INIT(pRxBlk->pRxPacket,  
   ^  
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_ht.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_os_util.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/sta_ioctl.o 
   CC [M]  /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsUsDelay&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable &#8216;i&#8217; [-Wunused-variable]  
   ULONG i;  
         ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:497:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]  
    NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);  
    ^  
 In file included from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/string.h:4:0, 
                  from include/linux/string.h:17,  
                  from include/linux/bitmap.h:8,  
                  from include/linux/cpumask.h:11,  
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/cpumask.h:4, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/msr.h:10, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/processor.h:20, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/thread_info.h:22, 
                  from include/linux/thread_info.h:54,  
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/preempt.h:6, 
                  from include/linux/preempt.h:18,  
                  from include/linux/spinlock.h:50,  
                  from include/linux/seqlock.h:35,  
                  from include/linux/time.h:5,  
                  from include/linux/stat.h:18,  
                  from include/linux/module.h:10,  
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32: 
 /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217; 
  void *memmove(void *dest, const void *src, size_t count);  
        ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:499:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]  
    NdisMoveMemory(skb->tail, pData, DataSize);  
    ^  
 In file included from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/string.h:4:0, 
                  from include/linux/string.h:17,  
                  from include/linux/bitmap.h:8,  
                  from include/linux/cpumask.h:11,  
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/cpumask.h:4, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/msr.h:10, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/processor.h:20, 
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/thread_info.h:22, 
                  from include/linux/thread_info.h:54,  
                  from /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/preempt.h:6, 
                  from include/linux/preempt.h:18,  
                  from include/linux/spinlock.h:50,  
                  from include/linux/seqlock.h:35,  
                  from include/linux/time.h:5,  
                  from include/linux/stat.h:18,  
                  from include/linux/module.h:10,  
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32: 
 /usr/src/linux-headers-3.13.0-83-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217; 
  void *memmove(void *dest, const void *src, size_t count);  
        ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:650:20: warning: assignment makes integer from pointer without a cast [enabled by default]  
    pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;  
                     ^  
 In file included from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75, 
                  from /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32: 
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]  
    ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))  
                                   ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:669:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;  
   SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);  
   ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:695:15: warning: assignment makes integer from pointer without a cast [enabled by default]  
   pOSPkt->tail = pOSPkt->data + pOSPkt->len;  
                ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;  
    pOSFSInfo->fsuid = current_fsuid();  
                     ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;  
    pOSFSInfo->fsgid = current_fsgid();  
                     ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpDrvAllRFPrint&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of &#8216;file_w->f_op->write&#8217; from incompatible pointer type [enabled by default]  
     file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos); 
     ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected &#8216;const char *&#8217; but argument is of type &#8216;UINT32 *&#8217;  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable &#8216;macValue&#8217; [-Wunused-variable]  
   UINT32 macAddr = 0, macValue = 0;  
                       ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable &#8216;macAddr&#8217; [-Wunused-variable]  
   UINT32 macAddr = 0, macValue = 0;  
          ^  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSIRQRelease&#8217;:  
 /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable &#8216;net_dev&#8217; [-Wunused-variable]  
   struct net_device *net_dev = (struct net_device *)pNetDev;  
                      ^  
 make[2]: *** [/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Error 1  
 make[1]: *** [_module_/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2  
 make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-83-generic'  
 make: *** [LINUX] Error 2  
 ben@ben-H81M-S:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo make install  
 make -C /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install  

 mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists  
 make[1]: Entering directory `/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'  
 rm -rf /etc/Wireless/RT2870STA  
 mkdir /etc/Wireless/RT2870STA  
 cp /home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.  
 install -d /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/  
 install -m 644 -c mt7601Usta.ko /lib/modules/3.13.0-83-generic/kernel/drivers/net/wireless/  
 install: cannot stat &#8216;mt7601Usta.ko&#8217;: No such file or directory  
 make[1]: *** [install] Error 1  
 make[1]: Leaving directory `/home/ben/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'  
 make: *** [install] Error 2  
 ben@ben-H81M-S:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$
```

---

### Post by howefield on 2016-03-30
Thread moved to the "*Networking & Wireless*" forum.

---

