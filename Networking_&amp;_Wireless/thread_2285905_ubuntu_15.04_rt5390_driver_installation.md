---
title: "ubuntu 15.04 rt5390 driver installation"
date: 2015-07-08
forum: Networking &amp; Wireless
---

### Post by joseph_greene on 2015-07-08
im running ubuntu 15.04 on a hp pavilion g6 1d98dx and am trying to install the driver for my wireless adapter (rt5390) by following the steps posted on this thread [http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716) but get theses errors ```
joseph@joseph-ubuntu:~/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ make
make -C tools
make[1]: Entering directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.19.0-22-generic/build SUBDIRS=/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-22-generic'
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlShow’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:5041:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                     ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:5041:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                               ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c: At top level:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:7555:1: fatal error: opening dependency file /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/.sta_cfg.o.d: Permission denied
 }
 ^
cc1: some warnings being treated as errors
compilation terminated.
The bug is not reproducible, so it is likely a hardware or OS problem.
scripts/Makefile.build:257: recipe for target '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1394: recipe for target '_module_/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux' failed
make[1]: *** [_module_/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-22-generic'
Makefile:372: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2 
```
 after doing step 7. run command "make" if anyone could help i greatly appreciate it. here is the output of lspci ```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

```

---

### Post by praseodym on 2015-07-09
The driver may be too old. Try this one (tested with 14.04 only! It is a patched one):

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/19/16/3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
tar xvf 3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
cd 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

Patch from here:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

---

### Post by joseph_greene on 2015-07-09
> **praseodym said:**
> The driver may be too old. Try this one (tested with 14.04 only! It is a patched one):

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/19/16/3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
tar xvf 3473742-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched.tar.gz
cd 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

Patch from here:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

when running "make" this was the output i got some error codes mainly towards the bottom ```
 joseph@joseph-ubuntu:~/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched$ make
make -C tools
make[1]: Entering directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/tools'
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/tools/bin2h
cp -f os/linux/Makefile.6 /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/Makefile
make -C /lib/modules/3.19.0-22-generic/build SUBDIRS=/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-22-generic'
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_md5.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_aes.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_aes.c:1459:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));
      ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_aes.c:1554:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.o
In file included from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rtmp_os.h:44:0,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rtmp_comm.h:60,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rt_config.h:33,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c:28:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c:1054:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c:1055:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c: In function ‘MlmePeriodicExec’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c:1292:8: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
        (UINT32)&pAd->RalinkCounters.OneSecEnd -
        ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/mlme.c:1293:8: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
        (UINT32)&pAd->RalinkCounters.OneSecStart);
        ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_wep.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/action.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_data.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/rtmp_init.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_aes.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_sync.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/eeprom.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_info.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_wpa.o
In file included from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rtmp_os.h:44:0,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rtmp_comm.h:60,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/rt_config.h:33,
                 from /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_wpa.c:28:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_wpa.c: In function ‘PeerWpaMessageSanity’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_wpa.c:456:32: warning: argument to ‘sizeof’ in ‘memset’ call is the same expression as the destination; did you mean to provide an explicit length? [-Wsizeof-pointer-memaccess]
  NdisZeroMemory(KEYDATA, sizeof(KEYDATA));
                                ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/include/os/rt_linux.h:473:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/dfs.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/spectrum.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/spectrum.c:1857:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/rt_channel.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_profile.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c: In function ‘AsicGetAutoAgcOffset’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:882:10: warning: unused variable ‘bTempSuccess’ [-Wunused-variable]
  BOOLEAN bTempSuccess = FALSE; 
          ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:881:6: warning: unused variable ‘LookupTableIndex’ [-Wunused-variable]
  INT LookupTableIndex = pAd->TxPowerCtrl.LookupTableIndex + TEMPERATURE_COMPENSATION_LOOKUP_TABLE_OFFSET;
      ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:880:6: warning: unused variable ‘CurrentTemp’ [-Wunused-variable]
  INT CurrentTemp = 0;
      ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:879:8: warning: unused variable ‘BbpValue’ [-Wunused-variable]
  UCHAR BbpValue = 0;
        ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:878:32: warning: unused variable ‘pTxPowerTuningEntry2’ [-Wunused-variable]
  PTX_POWER_TUNING_ENTRY_STRUCT pTxPowerTuningEntry2 = NULL;
                                ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:875:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
  UCHAR RFValue = 0;
        ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:874:32: warning: unused variable ‘pTxPowerTuningEntry’ [-Wunused-variable]
  PTX_POWER_TUNING_ENTRY_STRUCT pTxPowerTuningEntry = NULL;
                                ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c: In function ‘AsicAdjustTxPower’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:1575:16: warning: unused variable ‘flags’ [-Wunused-variable]
  unsigned long flags;
                ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:1562:20: warning: unused variable ‘pFinalTxPwr’ [-Wunused-variable]
  PTX_PWR_CFG_STRUC pFinalTxPwr = NULL;
                    ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_asic.c:1560:11: warning: unused variable ‘bAutoTxAgc’ [-Wunused-variable]
  BOOLEAN  bAutoTxAgc = FALSE;
           ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../os/linux/rt_profile.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../os/linux/rt_profile.c:411:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/assoc.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/auth.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sync.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sanity.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/connect.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/connect.c: In function ‘LinkUp’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/connect.c:1446:35: warning: unused variable ‘pCurrEntry’ [-Wunused-variable]
  MAC_TABLE_ENTRY *pEntry = NULL, *pCurrEntry = NULL;
                                   ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/connect.c:1445:28: warning: unused variable ‘HashIdx’ [-Wunused-variable]
  UCHAR Value = 0, idx = 0, HashIdx = 0;
                            ^
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/wpa.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/ags.o
  CC [M]  /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.o
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.c: In function ‘RTMPIoctlShow’:
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.c:4931:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                     ^
/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.c:4931:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                               ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1394: recipe for target '_module_/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux' failed
make[1]: *** [_module_/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-22-generic'
Makefile:356: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
joseph@joseph-ubuntu:~/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched$ sudo make install
make -C /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt5390sta.ko’: No such file or directory
Makefile.6:327: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/joseph/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_patched/os/linux'
Makefile:449: recipe for target 'install' failed
make: *** [install] Error 2 
```

---

### Post by praseodym on 2015-07-09
Normally, this device should run with the native driver rt2800pci:
```

sudo modprobe -v rt2800pci
dmesg | grep rt2
rfkill list
iwconfig
```

---

### Post by joseph_greene on 2015-07-09
> **praseodym said:**
> Normally, this device should run with the native driver rt2800pci:
```

sudo modprobe -v rt2800pci
dmesg | grep rt2
rfkill list
iwconfig
```

output of running code ```
joseph@joseph-ubuntu:~$ sudo modprobe -v rt2800pci
[sudo] password for joseph: 
insmod /lib/modules/3.19.0-22-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko 
insmod /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko 
joseph@joseph-ubuntu:~$ dmesg | grep rt2
[ 6910.918066] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[ 6910.922237] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
joseph@joseph-ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
joseph@joseph-ubuntu:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


``` and now instead of the network dropdown menu only displaying ethernet network,wired connection1,disconnect,vpn connections,enable networking,connection information, and edit connections it shows these [https://www.dropbox.com/s/rgcujwrf2bpvdsa/Screenshot%20from%202015-07-09%2010%3A40%3A21.png?dl=0](https://www.dropbox.com/s/rgcujwrf2bpvdsa/Screenshot%20from%202015-07-09%2010%3A40%3A21.png?dl=0) also

---

### Post by praseodym on 2015-07-09
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: [COLOR="#FF0000"]yes[/COLOR]
joseph@joseph-ubuntu:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]off[/COLOR]   
          Retry short limit:7   RTS thr:off   Fragment thr:off
```
The card is "off". Any button, switch, key or key combination? Checked the BIOS?

---

### Post by joseph_greene on 2015-07-09
the key combo is just f12 but when i do that it toggles soft block. i enabled network adapter start on bootup in bios and now the network drop down menu shrunk again [https://www.dropbox.com/s/4v1miprcza977km/Screenshot%20from%202015-07-09%2011%3A11%3A55.png?dl=0](https://www.dropbox.com/s/4v1miprcza977km/Screenshot%20from%202015-07-09%2011%3A11%3A55.png?dl=0)

---

### Post by praseodym on 2015-07-09
BIOS reset?

---

### Post by joseph_greene on 2015-07-09
nothing changed except for instead of my ethernet connection being etho1 its now wired connection 1 and "rfkill list all" and "sudo rfkill list all" are not giving any output

---

### Post by monkeybrain20122 on 2015-07-09
I have the same card. The driver rt2800pci works just fine. Works out of the box.

---

### Post by joseph_greene on 2015-07-09
i think my problem is something to do with the hardblock no matter what i do it wont go off. i believe if i could somehow turn it off that might solve my problem. or it might be something else im sorta new to linux

---

