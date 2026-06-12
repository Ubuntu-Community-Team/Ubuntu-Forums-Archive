---
title: "Can't install USB wifi adapter"
date: 2014-08-27
forum: Networking &amp; Wireless
---

### Post by bryan-com on 2014-08-27
I just installed Ubuntu on my pc for the first time. yippy! I have no ethernet drop nearby but I do have a USB wifi adapter and CD installation cdrom. The problem is that I can't make sense out of the installation files and my pc doesn't even see the adapter yet. Everyone seems to be talking about .deb fines for installations but I have no .deb file. 
Here's what I have.
I extracted an archive that I think is for the Linux driver. Now there is a directory named DPA_MT7601U_Linux_3.0.0.3_20130313
In that directory I have a whole slew of files and some more Dirs.
dirs...
MODULE
NETIF
UTIL

files...
config.mk
cp_module.sh
cp_util.sh
load
Makefile
Makefile.clean
Makefile.inc
RT2870STA.dat
SingleSKU.dat
unload

Is any of this what I'm looking for?

thanks.

---

### Post by varunendra on 2014-08-27
> **bryan-com said:**
> Now there is a directory named **DPA_MT7601U_Linux_3.0.0.3_2013[COLOR="#FF0000"]03[/COLOR]13**

First of all, Welcome to the forums bryan!

The directory name suggests that the driver is older than the one available at Ralink's official website.

We have instructions to download and compile the new one, but not having an alternative internet connection can make it a bit tricky.

Please open a terminal (Ctrl-Alt-T) and post back the output of -
```
apt-get install --print-uris linux-headers-generic build-essential
```
(If it asks you whether to proceed with y/n, answer with 'y')

If the output of above gives us the download URIs of the required packages, we can download and install them manually and proceed with driver installation.

If you can temporarily get an alternative internet connection (in a cyber cafe, a friend's USB modem/wifi-dongle etc.), then the full and exact installation instructions are given in this post : [http://ubuntuforums.org/showthread.php?t=2206873&p=12936176#post12936176](http://ubuntuforums.org/showthread.php?t=2206873&p=12936176#post12936176)

---

### Post by Irihapeti on 2014-08-27
*Thread moved to **Networking & Wireless**.*

---

### Post by 3rdalbum on 2014-08-27
Wait - if this device uses an RT2870 chip, you don't need that driver. It is preinstalled on Ubuntu 12.04 and later.

Unlike Windows, when you plug in a USB device Linux doesn't make any noises or display any notifications.

Just wait about 10 seconds after plugging in and click on the Network Manager icon at the top of the screen and your local WiFi networks should appear.

If it doesnt work and you are not sure what chip is in the WiFi device, plug it in and type this into the terminal:

lsusb

(It stands for "List USB")

The model number of the WiFi chip will appear along with the details of all USB devices you have plugged in.

---

### Post by varunendra on 2014-08-27
> **3rdalbum said:**
> Wait - if this device uses an RT2870 chip, you don't need that driver.

RT2860/70STA are just the names of the data (settings) files that perhaps All of the Ralink drivers use, regardless of the driver name. The folder name suggests the chip is one of their two latest releases (**MT7601**/7610U) which have no native Linux drivers so far.

---

### Post by bryan-com on 2014-08-27
Thanks for the help.  I have a laptop with wifi so I can pass stuff back and forth via flash drive. 
Here are the results of what you asked me to run.
brcjacks@brcjacks-Inspiron-530s:~$ apt-get install --print-uris linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
brcjacks@brcjacks-Inspiron-530s:~$

---

### Post by bryan-com on 2014-08-27
And the results of lsusb

brcjacks@brcjacks-Inspiron-530s:~$ lsusb
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 004: ID 148f:7601 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brcjacks@brcjacks-Inspiron-530s:~$

---

### Post by varunendra on 2014-08-27
Problem is, the package build-essential is just a list of packages that are needed to compile source codes. It has dependencies and those dependencies have further dependencies and so on..

Getting a temporary internet connection would have made it super easy. Earlier versions of Ubuntu used to have this package, along with all the dependencies on the CD iso itself, so one could simply add the CD as a software repository and install from it. But the current versions don't include build-essential on the ISO, so that method is no longer going to work.

If you can't get a temporary internet connection, then please try this (just cooked up this idea on my own, not sure if it is going to work) -

Boot from the live DVD/USB. In the live session, perform steps 1, 2 and 3 given in this post : [http://ubuntuforums.org/showpost.php?p=12936176](http://ubuntuforums.org/showpost.php?p=12936176)
You don't need to run 'sudo make install' command in step 3, just stop after 'make'.

A Live session has both the headers and build-essential installed, so you should be able to compile the driver there. We need these packages only to compile the driver. Since it is a fresh install, and you haven't updated since installation, the driver compiled on the Live session should work with the installed version.

IF the driver is compiled successfully (no errors in the 'make' step), archive the entire directory as a tar.bz2 package (to preserve permissions) -
```
cd ..
tar cjf driver.tar.bz2 DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
```

Copy this "driver.tar.bz2" archive that will be created with the last command above (in the "Downloads" directory, or wherever this "DPO..." directory is) onto your hard disk.

Reboot into installed Ubuntu > copy this "driver.tar.bz2" archive onto your Desktop > open a terminal > run the following commands to install it -
```
cd Desktop
tar xjf driver.tar.bz2
cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
sudo make install
```
If you see any errors in any of the steps, report back and we'll proceed as required.

---

### Post by bryan-com on 2014-08-27
Results from the Make:
```

brcjacks@brcjacks-Inspiron-530s:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ make
make -C tools
make[1]: Entering directory `/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:331:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  RTMP_ADAPTER *pAd = (RTMP_ADAPTER *)pAdSrc;
                ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:399:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/assoc.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:2181:12: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type [enabled by default]
            ie_list->CapabilityInfo) == FALSE)
            ^
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:28:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:7892:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST *’
 BOOLEAN StaAddMacTableEntry(
         ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sanity.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:523:4: warning: passing argument 2 of ‘MacTableLookup’ from incompatible pointer type [enabled by default]
    pEntry = MacTableLookup(pAd, &pHeader->Addr2);
    ^
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:28:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:8429:18: note: expected ‘UCHAR *’ but argument is of type ‘UCHAR (*)[6]’
 MAC_TABLE_ENTRY *MacTableLookup(RTMP_ADAPTER *pAd, UCHAR *pAddr);
                  ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/connect.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/wpa.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlRF’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5306:7: warning: format ‘%X’ expects argument of type ‘unsigned int’, but argument 5 has type ‘LONG’ [-Wformat=]
       sprintf(msg+strlen(msg), "BANK%d_R%02d:%02X  ", bank_Id, rfId, rfValue);
       ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5359:3: warning: passing argument 2 of ‘RtmpDrvAllRFPrint’ from incompatible pointer type [enabled by default]
   RtmpDrvAllRFPrint(NULL, msg, strlen(msg));
   ^
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:64:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:28:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_os_util.h:668:6: note: expected ‘UINT32 *’ but argument is of type ‘PSTRING’
 VOID RtmpDrvAllRFPrint(
      ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5209:22: warning: unused variable ‘rf_bank’ [-Wunused-variable]
  UCHAR    regRF = 0, rf_bank = 0;
                      ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwgenie’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:7610:13: warning: assignment from incompatible pointer type [enabled by default]
     eid_ptr = pAd->StaCfg.pWpaAssocIe;
             ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_md5.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1459:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));
      ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1554:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.o
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:33,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:28:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:544:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:545:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function ‘AsicRxAntEvalTimeout’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:5201:45: warning: unused variable ‘rssi_diff’ [-Wunused-variable]
  CHAR   larger = -127, rssi0, rssi1, rssi2, rssi_diff;
                                             ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wep.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/action.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function ‘CmdRspEventCallbackHandle’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2509:8: warning: unused variable ‘Ret’ [-Wunused-variable]
  INT32 Ret;
        ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function ‘StopDmaTx’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2684:8: warning: unused variable ‘IdleNums’ [-Wunused-variable]
  UINT8 IdleNums = 0;
        ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2682:20: warning: unused variable ‘UsbCfg’ [-Wunused-variable]
  USB_DMA_CFG_STRUC UsbCfg;
                    ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:981:9: warning: unused variable ‘i’ [-Wunused-variable]
  USHORT i;
         ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAdapter’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1292:22: warning: unused variable ‘GloCfg’ [-Wunused-variable]
  WPDMA_GLO_CFG_STRUC GloCfg;
                      ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1367:11: warning: unused variable ‘KeyIdx’ [-Wunused-variable]
  USHORT   KeyIdx;
           ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1656:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_aes.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sync.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c: In function ‘RtmpChipOpsEepromHook’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c:34:9: warning: unused variable ‘e2p_csr’ [-Wunused-variable]
  UINT32 e2p_csr;
         ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function ‘Set_DebugFunc_Proc’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘const char *’ [-Wformat=]
  DBGPRINT_S(RT_DEBUG_TRACE, ("Set RTDebugFunc = 0x%x\n",__FUNCTION__, RTDebugFunc));
  ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: too many arguments for format [-Wformat-extra-args]
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function ‘set_rf’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:5730:3: warning: format ‘%x’ expects argument of type ‘unsigned int *’, but argument 5 has type ‘UCHAR *’ [-Wformat=]
   rv = sscanf(arg, "%d-%d-%x", &(bank_id), &(rf_id), &(rf_val));
   ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: In function ‘wmode_valid_and_correct’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:279:8: warning: unused variable ‘mode’ [-Wunused-variable]
  UCHAR mode = *wmode;
        ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: At top level:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:264:16: warning: ‘wmode_valid’ defined but not used [-Wunused-function]
 static BOOLEAN wmode_valid(RTMP_ADAPTER *pAd, enum WIFI_MODE wmode)
                ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_radar.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_channel.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c: In function ‘rtmp_read_multest_from_file’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c:2671:23: warning: unused variable ‘pWdsEntry’ [-Wunused-variable]
  PRT_802_11_WDS_ENTRY pWdsEntry;
                       ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_asic.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/scan.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/uapsd.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ps.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/txpower.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c: In function ‘NICInitBBP’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c:61:8: warning: unused variable ‘R0’ [-Wunused-variable]
  UCHAR R0 = 0xff;
        ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.o
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:33,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c:30:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:929:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(__pRxPkt, __pData, __DataSize);      \
  ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c:1574:2: note: in expansion of macro ‘RTMP_OS_PKT_INIT’
  RTMP_OS_PKT_INIT(pRxBlk->pRxPacket,
  ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_os_util.o
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:56:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/sta_ioctl.c:30:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
include/net/iw_handler.h:542:9: warning: array subscript is below array bounds [-Warray-bounds]
   memcpy(stream + point_len, extra, iwe->u.data.length);
         ^
  CC [M]  /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable ‘i’ [-Wunused-variable]
  ULONG i;
        ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:497:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:499:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:650:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:669:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:695:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable ‘macValue’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [LINUX] Error 2
brcjacks@brcjacks-Inspiron-530s:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$

```

---

### Post by bryan-com on 2014-08-27
Results from the make install
```

brcjacks@brcjacks-Inspiron-530s:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo make install
[sudo] password for brcjacks: 
make -C /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Usta.ko /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;mt7601Usta.ko&#8217;: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/brcjacks/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
make: *** [install] Error 2
brcjacks@brcjacks-Inspiron-530s:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$

```

---

### Post by bryan-com on 2014-08-27
> **varunendra said:**
> RT2860/70STA are just the names of the data (settings) files that perhaps All of the Ralink drivers use, regardless of the driver name. The folder name suggests the chip is one of their two latest releases (**MT7601**/7610U) which have no native Linux drivers so far. 

Then I suppose my efforts are futile and I should be on ebay right now instead of bothering y'all.
Thanks for the help. 

btw, care to point me to a cheap USB wifi adapter that *does* have a native Linux driver?

---

### Post by varunendra on 2014-08-27
Not really futile. The driver they offer on their website works. Once it is built, you should have a working wifi until the next kernel upgrade, when you'll need to compile the driver again, easily this time since you will have the headers and build-essential on your system this time.

The only doubt I have is whether the driver will build on your kernel version or not. There was some problem in compilation between the backported packages and the kernel versions from 3.13.0-30 to 3.13.0-34.

Whatever it was, it seems to have been fixed in kernel version 3.13.0.34 and later. So if the Ralink driver fails to build on the Live session, we may try one of the latest kernel.

It is not really as difficult as it sounds. If you are compiling a driver for the first time, it may sound daunting, but once you have done it, it is just a matter of 3-4 commands in the terminal.

---

### Post by bryan-com on 2014-08-27
ok, so what do I do now? You seem to be saying that it should work but right now it does not. 
What should i try next?
and thanks for all the help so far. This is all new to me.

---

### Post by varunendra on 2014-08-27
Just realized that you posted the make/make-install results on the thread I linked to instead of yours here.

Let me first ask a mod to move them here so the progress of thread starts making some sense.

In the meanwhile, please post the output of -
```
uname -mr
```

And please understand that ALL posts related to a thread should stay on their own thread, not scattered on different threads all over the forum.

---

### Post by bryan-com on 2014-08-27
Sorry, Didn't realize I did that.

uname -mr
3.13.0-32-generic x86_64

---

### Post by sisco311 on 2014-08-27
> **varunendra said:**
> Just realized that you posted the make/make-install results on the thread I linked to instead of yours here.

Let me first ask a mod to move them here so the progress of thread starts making some sense.


Done.

> **bryan-com said:**
> Sorry, Didn't realize I did that.


No problem.

---

### Post by bryan-com on 2014-08-27
Sorry, Didn't realize I did that.

uname -mr
3.13.0-32-generic x86_64

---

### Post by bryan-com on 2014-08-27
Not to get off track here but I just ran a cat 5 cable across the house and plugged it in to the offending pc. I got blinky-blinky on the ethernet card and Linux tried to connect but failed. What's going on here? I'm running out of patients with Linux on my desktop.  This was a fresh install with the latest version from the Ubuntu site.

Oops, spoke too soon. I found some info about manually setting up the ethernet care and I got online.
Then, I got the brilliant idea of trying the OTHER usb wifi adapter in the house and wah-lah! I'm surfin' U.S.A.

Thanks again for your help.

---

### Post by varunendra on 2014-08-28
> **bryan-com said:**
> Oops, spoke too soon. I found some info about manually setting up the ethernet care and I got online.
Then, I got the brilliant idea of trying the OTHER usb wifi adapter in the house and wah-lah! I'm surfin' U.S.A.

Thanks again for your help.

You're welcome, but you just spoiled my opportunity of experimenting with the compilation :p

On a more serious note, glad you got it sorted. :)

---

