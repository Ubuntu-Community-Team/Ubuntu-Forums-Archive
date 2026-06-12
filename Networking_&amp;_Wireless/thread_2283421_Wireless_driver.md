---
title: "Wireless driver"
date: 2015-06-21
forum: Networking &amp; Wireless
---

### Post by M_Harley on 2015-06-21
I am fairly new to Ubuntu and I am having a problem with my wireless USB stick and installing its driver 

Parameters:
[LIST]
[*]I have Ubuntu 14.04.1
[*]The wireless stick is a Net DYN and can be found: [http://www.amazon.com/Adapter-NET-DYN%C2%AE-Perfect-Desktop-Laptop/dp/B00LWE14TO](http://www.amazon.com/Adapter-NET-DYN%C2%AE-Perfect-Desktop-Laptop/dp/B00LWE14TO)
[*]My laptop has no other means to connect to internet(no Ethernet cord)
[*]I have the initial install cd for the wireless stick, but when I open up the Linux folder, There is no run file, just a bunch of .c files
[*]my laptop is a dell Inspiron 15, 3000 series
[/LIST]
Therefore, how do I install the driver? Thank you for your time and patience.

---

### Post by chili555 on 2015-06-21
Please insert the device and open a terminal Ctrl+Alt+t and run and then post:```
lsusb
```Thanks.

---

### Post by M_Harley on 2015-06-22
The output is: 

Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 04f3:034e Elan Microelectronics Corp. 
Bus 001 Device 016: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 064e:c233 Suyin Corp. 
Bus 001 Device 012: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2015-06-22
Here is a thread that explains how to install the driver: [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation) As you can see, it involves getting the files and prerequisites from the internet. While it is possible, albeit lengthy and tedious, to download all these things on some other computer and transfer them on a USB key or similar, it is a copy and paste two minute job with a temporary ethernet connection. 

If your laptop has no ethernet port at all, I will write the alternative instructions for you. If there is any possibility that you can beg or borrow a temporary ethernet connection, you will save us both a great deal of work and possibly headache.

Which do you prefer?

---

### Post by M_Harley on 2015-06-22
I have temporary internet connection. I follow the steps all the way to the end but it says, "modprobe: FATAL: Module mt7601Usta not found."

---

### Post by M_Harley on 2015-06-22
Here is the code from the terminal:



```
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-52-generic_3.13.0-52.85_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-52-generic_3.13.0-52.85_amd64.deb)  404  Not Found [IP: 91.189.91.24 80]


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.52.59_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.52.59_amd64.deb)  404  Not Found [IP: 91.189.91.24 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
m@TheWorldofM:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
git set to manually installed.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 429 not upgraded.
m@TheWorldofM:~$ git clone [https://github.com/porjo/mt7601.git](https://github.com/porjo/mt7601.git) 
Cloning into 'mt7601'...
remote: Counting objects: 446, done.
remote: Total 446 (delta 0), reused 0 (delta 0), pack-reused 446
Receiving objects: 100% (446/446), 1.58 MiB | 0 bytes/s, done.
Resolving deltas: 100% (173/173), done.
Checking connectivity... done.
m@TheWorldofM:~$ cd mt7601/src
m@TheWorldofM:~/mt7601/src$ make
make -C tools
make[1]: Entering directory `/home/m/mt7601/src/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/m/mt7601/src/tools'
/home/m/mt7601/src/tools/bin2h
cp -f os/linux/Makefile.6 /home/m/mt7601/src/os/linux/Makefile
make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/m/mt7601/src/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/assoc.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/auth.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/sync.o
/home/m/mt7601/src/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/m/mt7601/src/os/linux/../../sta/sync.c:2183:12: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type [enabled by default]
            ie_list->CapabilityInfo) == FALSE)
            ^
In file included from /home/m/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/os/linux/../../sta/sync.c:28:
/home/m/mt7601/src/include/rtmp.h:7892:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST **’
 BOOLEAN StaAddMacTableEntry(
         ^
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/sanity.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/rtmp_data.o
/home/m/mt7601/src/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/m/mt7601/src/os/linux/../../sta/rtmp_data.c:523:4: warning: passing argument 2 of ‘MacTableLookup’ from incompatible pointer type [enabled by default]
    pEntry = MacTableLookup(pAd, &pHeader->Addr2);
    ^
In file included from /home/m/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/os/linux/../../sta/rtmp_data.c:28:
/home/m/mt7601/src/include/rtmp.h:8429:18: note: expected ‘UCHAR *’ but argument is of type ‘UCHAR (*)[6]’
 MAC_TABLE_ENTRY *MacTableLookup(RTMP_ADAPTER *pAd, UCHAR *pAddr);
                  ^
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/connect.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/wpa.o
  CC [M]  /home/m/mt7601/src/os/linux/../../sta/sta_cfg.o
/home/m/mt7601/src/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwgenie’:
/home/m/mt7601/src/os/linux/../../sta/sta_cfg.c:7618:13: warning: assignment from incompatible pointer type [enabled by default]
     eid_ptr = pAd->StaCfg.pWpaAssocIe;
             ^
  CC [M]  /home/m/mt7601/src/os/linux/../../common/crypt_md5.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/crypt_aes.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/mlme.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_wep.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/action.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_data.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtmp_init.o
/home/m/mt7601/src/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/m/mt7601/src/os/linux/../../common/rtmp_init.c:1656:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_aes.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_sync.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/eeprom.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_info.o
/home/m/mt7601/src/os/linux/../../common/cmm_info.c: In function ‘set_rf’:
/home/m/mt7601/src/os/linux/../../common/cmm_info.c:5730:3: warning: format ‘%x’ expects argument of type ‘unsigned int *’, but argument 5 has type ‘UCHAR *’ [-Wformat=]
   rv = sscanf(arg, "%d-%d-%x", &(bank_id), &(rf_id), &(rf_val));
   ^
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_radar.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/spectrum.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rt_channel.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_profile.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_asic.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/scan.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/uapsd.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/ps.o
  CC [M]  /home/m/mt7601/src/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/m/mt7601/src/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/m/mt7601/src/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/m/mt7601/src/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/txpower.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/m/mt7601/src/os/linux/../../phy/rtmp_phy.o
  CC [M]  /home/m/mt7601/src/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/m/mt7601/src/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/ba_action.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rt_os_util.o
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/m/mt7601/src/include/os/rt_linux.h:56:0,
                 from /home/m/mt7601/src/include/rtmp_os.h:44,
                 from /home/m/mt7601/src/include/rtmp_comm.h:75,
                 from /home/m/mt7601/src/os/linux/../../os/linux/sta_ioctl.c:30:
/home/m/mt7601/src/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
include/net/iw_handler.h:542:9: warning: array subscript is below array bounds [-Warray-bounds]
   memcpy(stream + point_len, extra, iwe->u.data.length);
         ^
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/rt_linux.o
/home/m/mt7601/src/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/m/mt7601/src/os/linux/../../os/linux/rt_linux.c:2054:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/m/mt7601/src/os/linux/../../os/linux/rt_linux.c:2054:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_mac_usb.o
/home/m/mt7601/src/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/m/mt7601/src/os/linux/../../common/cmm_mac_usb.c:562:31: warning: initialization from incompatible pointer type [enabled by default]
  PTX_CONTEXT pNullContext   = &(pAd->NullContext);
                               ^
  CC [M]  /home/m/mt7601/src/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtusb_io.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtusb_data.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtusb_bulk.o
/home/m/mt7601/src/os/linux/../../common/rtusb_bulk.c: In function ‘RTUSBCancelPendingBulkOutIRP’:
/home/m/mt7601/src/os/linux/../../common/rtusb_bulk.c:1680:15: warning: assignment from incompatible pointer type [enabled by default]
  pNullContext = &(pAd->NullContext);
               ^
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/rt_usb.o
/home/m/mt7601/src/os/linux/../../os/linux/rt_usb.c: In function ‘cmd_rsp_event_tasklet’:
/home/m/mt7601/src/os/linux/../../os/linux/rt_usb.c:537:22: warning: assignment from incompatible pointer type [enabled by default]
  pCmdRspEventContext = (PRX_CONTEXT)RTMP_USB_URB_DATA_GET(pUrb);
                      ^
  CC [M]  /home/m/mt7601/src/os/linux/../../common/ee_prom.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/ee_efuse.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mcu/rtmp_and.o
  CC [M]  /home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.o
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:32:2: warning: passing argument 3 of ‘RTUSBMultiWrite_nBytes’ from incompatible pointer type [enabled by default]
  RTUSBMultiWrite_nBytes(pAd, Offset, Data, Cnt * 4, 64); 
  ^
In file included from /home/m/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:28:
/home/m/mt7601/src/include/rtmp.h:7553:10: note: expected ‘PUCHAR’ but argument is of type ‘UINT32 *’
 NTSTATUS RTUSBMultiWrite_nBytes(
          ^
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘ChipOpsMCUHook’:
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:64:25: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->Calibration = AndesCalibrationOP;
                         ^
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:71:25: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->RandomWrite = AndesRandomWrite;
                         ^
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:72:27: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->RFRandomWrite = AndesRFRandomWrite;
                           ^
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:33:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCURandomWrite’:
/home/m/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:41:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
  CC [M]  /home/m/mt7601/src/os/linux/../../mcu/rtmp_M51.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rt_rf.o
  CC [M]  /home/m/mt7601/src/os/linux/../../chips/mt7601.o
/home/m/mt7601/src/os/linux/../../chips/mt7601.c: In function ‘MT7601DisableTxRx’:
/home/m/mt7601/src/os/linux/../../chips/mt7601.c:1491:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
   return;
   ^
/home/m/mt7601/src/os/linux/../../chips/mt7601.c: In function ‘MT7601_Init’:
/home/m/mt7601/src/os/linux/../../chips/mt7601.c:3387:24: warning: assignment from incompatible pointer type [enabled by default]
  pChipOps->DisableTxRx = MT7601DisableTxRx;
                        ^
  CC [M]  /home/m/mt7601/src/os/linux/../../mac/ral_omac.o
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/rt_usb_util.o
/home/m/mt7601/src/os/linux/../../os/linux/rt_usb_util.c: In function ‘rausb_autopm_get_interface’:
/home/m/mt7601/src/os/linux/../../os/linux/rt_usb_util.c:155:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
  CC [M]  /home/m/mt7601/src/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/m/mt7601/src/os/linux/../../common/frq_cal.o
  LD [M]  /home/m/mt7601/src/os/linux/mt7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/m/mt7601/src/os/linux/mt7601Usta.mod.o
  LD [M]  /home/m/mt7601/src/os/linux/mt7601Usta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
cp -f /home/m/mt7601/src/os/linux/mt7601Usta.ko /tftpboot 2>/dev/null || :
m@TheWorldofM:~/mt7601/src$ sudo mkdir -p /etc/Wireless/RT2870STA/
m@TheWorldofM:~/mt7601/src$ sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
m@TheWorldofM:~/mt7601/src$ sudo modprobe mt7601Usta
modprobe: FATAL: Module mt7601Usta not found.
m@TheWorldofM:~/mt7601/src$ cd mt7601/src
bash: cd: mt7601/src: No such file or directory
m@TheWorldofM:~/mt7601/src$ git clone [https://github.com/porjo/mt7601.git](https://github.com/porjo/mt7601.git) 
Cloning into 'mt7601'...
remote: Counting objects: 446, done.
remote: Total 446 (delta 0), reused 0 (delta 0), pack-reused 446
Receiving objects: 100% (446/446), 1.58 MiB | 0 bytes/s, done.
Resolving deltas: 100% (173/173), done.
Checking connectivity... done.
m@TheWorldofM:~/mt7601/src$ cd mt7601/src
m@TheWorldofM:~/mt7601/src/mt7601/src$ make
make -C tools
make[1]: Entering directory `/home/m/mt7601/src/mt7601/src/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/m/mt7601/src/mt7601/src/tools'
/home/m/mt7601/src/mt7601/src/tools/bin2h
cp -f os/linux/Makefile.6 /home/m/mt7601/src/mt7601/src/os/linux/Makefile
make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/m/mt7601/src/mt7601/src/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/assoc.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/auth.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/sync.o
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/sync.c:2183:12: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type [enabled by default]
            ie_list->CapabilityInfo) == FALSE)
            ^
In file included from /home/m/mt7601/src/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/mt7601/src/os/linux/../../sta/sync.c:28:
/home/m/mt7601/src/mt7601/src/include/rtmp.h:7892:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST **’
 BOOLEAN StaAddMacTableEntry(
         ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/sanity.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/rtmp_data.o
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/rtmp_data.c:523:4: warning: passing argument 2 of ‘MacTableLookup’ from incompatible pointer type [enabled by default]
    pEntry = MacTableLookup(pAd, &pHeader->Addr2);
    ^
In file included from /home/m/mt7601/src/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/mt7601/src/os/linux/../../sta/rtmp_data.c:28:
/home/m/mt7601/src/mt7601/src/include/rtmp.h:8429:18: note: expected ‘UCHAR *’ but argument is of type ‘UCHAR (*)[6]’
 MAC_TABLE_ENTRY *MacTableLookup(RTMP_ADAPTER *pAd, UCHAR *pAddr);
                  ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/connect.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/wpa.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../sta/sta_cfg.o
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwgenie’:
/home/m/mt7601/src/mt7601/src/os/linux/../../sta/sta_cfg.c:7618:13: warning: assignment from incompatible pointer type [enabled by default]
     eid_ptr = pAd->StaCfg.pWpaAssocIe;
             ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/crypt_md5.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/crypt_aes.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/mlme.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_wep.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/action.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_data.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtmp_init.o
/home/m/mt7601/src/mt7601/src/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/m/mt7601/src/mt7601/src/os/linux/../../common/rtmp_init.c:1656:1: warning: the frame size of 1032 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_aes.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_sync.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/eeprom.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_info.o
/home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_info.c: In function ‘set_rf’:
/home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_info.c:5730:3: warning: format ‘%x’ expects argument of type ‘unsigned int *’, but argument 5 has type ‘UCHAR *’ [-Wformat=]
   rv = sscanf(arg, "%d-%d-%x", &(bank_id), &(rf_id), &(rf_val));
   ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_radar.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/spectrum.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rt_channel.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_profile.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_asic.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/scan.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/uapsd.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/ps.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/txpower.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../phy/rtmp_phy.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/ba_action.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rt_os_util.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/m/mt7601/src/mt7601/src/include/os/rt_linux.h:56:0,
                 from /home/m/mt7601/src/mt7601/src/include/rtmp_os.h:44,
                 from /home/m/mt7601/src/mt7601/src/include/rtmp_comm.h:75,
                 from /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/sta_ioctl.c:30:
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
include/net/iw_handler.h:542:9: warning: array subscript is below array bounds [-Warray-bounds]
   memcpy(stream + point_len, extra, iwe->u.data.length);
         ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_linux.o
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_linux.c:2054:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_linux.c:2054:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_mac_usb.o
/home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_mac_usb.c:562:31: warning: initialization from incompatible pointer type [enabled by default]
  PTX_CONTEXT pNullContext   = &(pAd->NullContext);
                               ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_io.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_data.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_bulk.o
/home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_bulk.c: In function ‘RTUSBCancelPendingBulkOutIRP’:
/home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_bulk.c:1680:15: warning: assignment from incompatible pointer type [enabled by default]
  pNullContext = &(pAd->NullContext);
               ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb.o
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb.c: In function ‘cmd_rsp_event_tasklet’:
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb.c:537:22: warning: assignment from incompatible pointer type [enabled by default]
  pCmdRspEventContext = (PRX_CONTEXT)RTMP_USB_URB_DATA_GET(pUrb);
                      ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/ee_prom.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/ee_efuse.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_and.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.o
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:32:2: warning: passing argument 3 of ‘RTUSBMultiWrite_nBytes’ from incompatible pointer type [enabled by default]
  RTUSBMultiWrite_nBytes(pAd, Offset, Data, Cnt * 4, 64); 
  ^
In file included from /home/m/mt7601/src/mt7601/src/include/rt_config.h:59:0,
                 from /home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:28:
/home/m/mt7601/src/mt7601/src/include/rtmp.h:7553:10: note: expected ‘PUCHAR’ but argument is of type ‘UINT32 *’
 NTSTATUS RTUSBMultiWrite_nBytes(
          ^
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘ChipOpsMCUHook’:
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:64:25: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->Calibration = AndesCalibrationOP;
                         ^
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:71:25: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->RandomWrite = AndesRandomWrite;
                         ^
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:72:27: warning: assignment from incompatible pointer type [enabled by default]
   pChipOps->RFRandomWrite = AndesRFRandomWrite;
                           ^
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCUBurstWrite’:
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:33:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c: In function ‘MCURandomWrite’:
/home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_mcu.c:41:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mcu/rtmp_M51.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rt_rf.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../chips/mt7601.o
/home/m/mt7601/src/mt7601/src/os/linux/../../chips/mt7601.c: In function ‘MT7601DisableTxRx’:
/home/m/mt7601/src/mt7601/src/os/linux/../../chips/mt7601.c:1491:3: warning: ‘return’ with no value, in function returning non-void [-Wreturn-type]
   return;
   ^
/home/m/mt7601/src/mt7601/src/os/linux/../../chips/mt7601.c: In function ‘MT7601_Init’:
/home/m/mt7601/src/mt7601/src/os/linux/../../chips/mt7601.c:3387:24: warning: assignment from incompatible pointer type [enabled by default]
  pChipOps->DisableTxRx = MT7601DisableTxRx;
                        ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../mac/ral_omac.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb_util.o
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb_util.c: In function ‘rausb_autopm_get_interface’:
/home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/rt_usb_util.c:155:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/m/mt7601/src/mt7601/src/os/linux/../../common/frq_cal.o
  LD [M]  /home/m/mt7601/src/mt7601/src/os/linux/mt7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/m/mt7601/src/mt7601/src/os/linux/mt7601Usta.mod.o
  LD [M]  /home/m/mt7601/src/mt7601/src/os/linux/mt7601Usta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
cp -f /home/m/mt7601/src/mt7601/src/os/linux/mt7601Usta.ko /tftpboot 2>/dev/null || :
m@TheWorldofM:~/mt7601/src/mt7601/src$ cd mkdir -p /etc/Wireless/RT2870STA/
bash: cd: mkdir: No such file or directory
m@TheWorldofM:~/mt7601/src/mt7601/src$ sudo mkdir -p /etc/Wireless/RT2870STA/
m@TheWorldofM:~/mt7601/src/mt7601/src$ sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
m@TheWorldofM:~/mt7601/src/mt7601/src$ ls
ate               mac       phy                sta
chips             Makefile  rate_ctrl          sta_ate_iwpriv_usage.txt
common            mcu       README_STA_usb     tools
include           mgmt      RT2870STACard.dat
iwpriv_usage.txt  os        RT2870STA.dat
m@TheWorldofM:~/mt7601/src/mt7601/src$ sudo modprobe mt7601Usta
modprobe: FATAL: Module mt7601Usta not found.
m@TheWorldofM:~/mt7601/src/mt7601/src$
```

---

### Post by wildmanne39 on 2015-06-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2015-06-22
It looks like you missed this step:```
sudo apt-get install linux-headers-generic build-essential git
sudo apt-get install git
git clone https://github.com/porjo/mt7601.git 
cd mt7601/src
make
[COLOR="#FF0000"]sudo make install[/COLOR]
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta
```Please try again.

---

### Post by M_Harley on 2015-06-22
Thanks for the tip!

---

### Post by M_Harley on 2015-06-22
Mr. Chilli,

Thank you so much! Your help has been invaluable. I really appreciate it. On a side note, where would I go to continue learning more about Linux? Thanks for everything!

---

### Post by chili555 on 2015-06-22
> **M_Harley said:**
> Mr. Chilli,

Thank you so much! Your help has been invaluable. I really appreciate it. On a side note, where would I go to continue learning more about Linux? Thanks for everything!I'm sure there are better ways, but I got a book and experimented using a live DVD and I read the forums and Googled. There are dozens of sites similar to this to help: [http://howtoubuntu.org/](http://howtoubuntu.org/) I'd also check here: [http://askubuntu.com/questions](http://askubuntu.com/questions)

---

### Post by Matejko on 2015-06-24
I have strange situation. Have both installed windows & ubuntu. There is no problem to connect wifi on windows - immediately. But after switch to ubuntu, system tries to connect, I'm waiting for a long time but nothing happens.. Is this problem with drivers? How to fix it? Temporary I decide to connect my PC over router in client mode, but this is not the good way...

---

### Post by chili555 on 2015-06-24
> **Matejko said:**
> I have strange situation. Have both installed windows & ubuntu. There is no problem to connect wifi on windows - immediately. But after switch to ubuntu, system tries to connect, I'm waiting for a long time but nothing happens.. Is this problem with drivers? How to fix it? Temporary I decide to connect my PC over router in client mode, but this is not the good way...
Do you have the exact same device as the original post?> 148f:7601 Ralink Technology, Corp. If not, please start your own new thread. Help us by giving us details of your device and current settings as described here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Matejko on 2015-06-24
Thanks for answer. Excuse me for making little mess here.. For sure I have Ralink wifi, but not USB-stick - internal on PCI card. I'll check exact model today and I'll ask you later. Again thanks.

---

