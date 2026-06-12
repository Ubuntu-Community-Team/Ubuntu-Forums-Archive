---
title: "What do I need to install Nano USB Wifi Ralink 148f:7601?"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by Matty_r on 2014-09-30
I just received a Nano USB Wifi adapter (Ralink 148f:7601) and i'm not sure how to install it. I've tried search around but the drivers that a needed seem to vary and I have no idea how to troubleshoot what I need. I tried doing a *make* command on a driver that was on a cd that came with it but after I rebooted there was no change. 

Sorry I don't really know where to go from here.

```

lsusb
Bus 001 Device 006: ID 148f:7601 Ralink Technology, Corp.

```

---

### Post by Matty_r on 2014-09-30
I tried the following from [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation)

Do not connect the USB:

```
sudo apt-get install --reinstall linux-headers-generic build-essential  
tar xjf DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2  
cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/  
patch -p0 < ~/(ADD THE PATH)/rt2870-mt7601Usta-kuid_t-kgid_t.patch  
make  

```

Got an error during the make command 

make output:
```

matt@matt-linux:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ make
make -C tools
make[1]: Entering directory `/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.14.15-031415-generic/build SUBDIRS=/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.14.15-031415-generic'
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.o
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:331:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  RTMP_ADAPTER *pAd = (RTMP_ADAPTER *)pAdSrc;
                ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_profile.c:399:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/assoc.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.o
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:2173:10: warning: passing argument 8 of ‘StaAddMacTableEntry’ from incompatible pointer type
      if (StaAddMacTableEntry(pAd, 
          ^
In file included from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0,
                 from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sync.c:28:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:7892:9: note: expected ‘struct IE_LISTS *’ but argument is of type ‘struct BCN_IE_LIST *’
 BOOLEAN StaAddMacTableEntry(
         ^
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sanity.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.o
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:523:13: warning: passing argument 2 of ‘MacTableLookup’ from incompatible pointer type
    pEntry = MacTableLookup(pAd, &pHeader->Addr2);
             ^
In file included from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:59:0,
                 from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/rtmp_data.c:28:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:8429:18: note: expected ‘UCHAR *’ but argument is of type ‘UCHAR (*)[6]’
 MAC_TABLE_ENTRY *MacTableLookup(RTMP_ADAPTER *pAd, UCHAR *pAddr);
                  ^
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/connect.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/wpa.o
  CC [M]  /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.o
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlRF’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5306:7: warning: format ‘%X’ expects argument of type ‘unsigned int’, but argument 5 has type ‘LONG’ [-Wformat=]
       sprintf(msg+strlen(msg), "BANK%d_R%02d:%02X  ", bank_Id, rfId, rfValue);
       ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5359:3: warning: passing argument 2 of ‘RtmpDrvAllRFPrint’ from incompatible pointer type
   RtmpDrvAllRFPrint(NULL, msg, strlen(msg));
   ^
In file included from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_config.h:64:0,
                 from /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:28:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_os_util.h:668:6: note: expected ‘UINT32 *’ but argument is of type ‘PSTRING’
 VOID RtmpDrvAllRFPrint(
      ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5209:22: warning: unused variable ‘rf_bank’ [-Wunused-variable]
  UCHAR    regRF = 0, rf_bank = 0;
                      ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlShow’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5766:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                     ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5766:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                               ^
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwgenie’:
/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:7610:13: warning: assignment from incompatible pointer type
     eid_ptr = pAd->StaCfg.pWpaAssocIe;
             ^
cc1: some warnings being treated as errors
make[2]: *** [/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.o] Error 1
make[1]: *** [_module_/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.14.15-031415-generic'
make: *** [LINUX] Error 2

```

---

### Post by Hadaka on 2014-09-30
Hi, try a chilli555 special.
[URL="http://ubuntuforums.org/showthread.php?t=2210930"]http://ubuntuforums.org/showthread.php?t=2210930

post#6
[/URL]

---

### Post by Matty_r on 2014-09-30
Nothing seemed to work :(

```

uname -mr
3.14.15-031415-generic x86_64

```

sudo make install
```

matt@matt-linux:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo make install
make -C /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
make[1]: Entering directory `/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.14.15-031415-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Usta.ko /lib/modules/3.14.15-031415-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;mt7601Usta.ko&#8217;: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/matt/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
make: *** [install] Error 2
matt@matt-linux:~/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo modprobe mt7601Usta
modprobe: FATAL: Module mt7601Usta not found.

```

---

### Post by chili555 on 2014-09-30
I know of no way to get this device working in later Ubuntu versions. I suggest you research here fully supported USB wireless devices and save yourself, Hadaka and I a month of disappointment.

---

### Post by Matty_r on 2014-09-30
Well.. that's disappointing.

---

### Post by chili555 on 2014-11-22
Please see post #4 here: [http://ubuntuforums.org/showthread.php?t=2253718](http://ubuntuforums.org/showthread.php?t=2253718)

---

