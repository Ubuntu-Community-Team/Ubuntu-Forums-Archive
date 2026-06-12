---
title: "ralink 3070"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by zeuse on 2015-02-23
Hi all.
I've a very hard problem. My ralink 3070 doesn't work on Ubuntu 14.04LTS 64 bit.
I've downloaded the newest official driver, but:

```

lsusb
Bus 002 Device 004: ID 1770:ff00  
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 005: ID 1267:0212 Logic3 / SpectraVideo plc 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

make -C tools
make[1]: ingresso nella directory "/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools"
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.13.0-45-generic/build SUBDIRS=/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.13.0-45-generic"
  CC [M]  /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8:  warning: unused variable ‘i’ [-Wunused-variable]
  ULONG i;
        ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:497:3:  warning: passing argument 1 of ‘memmove’ makes pointer from integer  without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string_64.h:58:7:  note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:499:3:  warning: passing argument 1 of ‘memmove’ makes pointer from integer  without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:31,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/usr/src/linux-headers-3.13.0-45-generic/arch/x86/include/asm/string_64.h:58:7:  note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:650:20:  warning: assignment makes integer from pointer without a cast [enabled  by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_os.h:44:0,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp_comm.h:75,
                 from /home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:32:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/os/rt_linux.h:886:34:  warning: assignment makes integer from pointer without a cast [enabled  by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:669:2:  note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:695:15:  warning: assignment makes integer from pointer without a cast [enabled  by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20:  error: incompatible types when assigning to type ‘int’ from type  ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20:  error: incompatible types when assigning to type ‘int’ from type  ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4:  warning: passing argument 2 of ‘file_w->f_op->write’ from  incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4:  note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22:  warning: unused variable ‘macValue’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9:  warning: unused variable ‘macAddr’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21:  warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Errore 1
make[1]: *** [_module_/home/zeuse/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.13.0-45-generic"
make: *** [LINUX] Errore 2


```

Thanks in avance!

---

### Post by chili555 on 2015-02-23
Your device is not an MT7601U device. Even if we could successfully compile the driver you downloaded, it won't drive your device.

The driver for your device, rt2800usb, is present in Ubuntu 14.04 by default.```
chili@T410:~$ modinfo rt2800usb | grep 3070
alias:          usb:v[COLOR="#FF0000"]148F[/COLOR]p[COLOR="#FF0000"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
```If it isn't working as expected, something else is wrong. Please tell old Uncle Chili what's not working. As well, please run and post:```
rfkill list all
lsmod | grep rt2
dmesg | grep rt2
```Thanks.

---

### Post by zeuse on 2015-02-25
Hi Old Uncle Chili ):P

My USB device works for a second, doesn't work for a second, works again for a second and so on.



rfkill list all
```

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
34: phy33: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lsmod | grep rt2
```

rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630669  4 rt2x00lib,rt2x00usb,rt2800lib,iwlmvm
crc_ccitt              12707  1 rt2800lib
cfg80211              484040  4 iwlwifi,mac80211,rt2x00lib,iwlmvm
```

dmesg | grep rt2
```

[   81.249465] ieee80211 phy11: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   81.249469] ieee80211 phy11: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   82.867180] ieee80211 phy11: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   83.383671] ieee80211 phy12: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   83.395095] ieee80211 phy12: rt2x00_set_rf: Info - RF chipset 0005 detected
[   83.438308] ieee80211 phy12: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   83.438343] ieee80211 phy12: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   83.976510] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   83.976517] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   85.594280] ieee80211 phy12: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   86.118381] ieee80211 phy13: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   86.128525] ieee80211 phy13: rt2x00_set_rf: Info - RF chipset 0005 detected
[   86.153746] ieee80211 phy13: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   86.153798] ieee80211 phy13: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   86.675458] ieee80211 phy13: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   86.675462] ieee80211 phy13: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   88.293242] ieee80211 phy13: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   88.801399] ieee80211 phy14: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   88.811485] ieee80211 phy14: rt2x00_set_rf: Info - RF chipset 0005 detected
[   88.838966] ieee80211 phy14: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   88.838985] ieee80211 phy14: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   89.386423] ieee80211 phy14: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   89.386427] ieee80211 phy14: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   91.004179] ieee80211 phy14: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   91.512625] ieee80211 phy15: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   91.523965] ieee80211 phy15: rt2x00_set_rf: Info - RF chipset 0005 detected
[   91.566848] ieee80211 phy15: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   91.566876] ieee80211 phy15: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   92.113413] ieee80211 phy15: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   92.113418] ieee80211 phy15: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   93.731173] ieee80211 phy15: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   94.299473] ieee80211 phy16: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   94.310018] ieee80211 phy16: rt2x00_set_rf: Info - RF chipset 0005 detected
[   94.341817] ieee80211 phy16: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   94.341851] ieee80211 phy16: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   94.872440] ieee80211 phy16: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   94.872443] ieee80211 phy16: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   96.962257] ieee80211 phy17: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   96.972139] ieee80211 phy17: rt2x00_set_rf: Info - RF chipset 0005 detected
[   96.999878] ieee80211 phy17: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   96.999900] ieee80211 phy17: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   97.535366] ieee80211 phy17: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   97.535370] ieee80211 phy17: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   99.153132] ieee80211 phy17: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   99.725266] ieee80211 phy18: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   99.735108] ieee80211 phy18: rt2x00_set_rf: Info - RF chipset 0005 detected
[   99.763509] ieee80211 phy18: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   99.763524] ieee80211 phy18: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  100.298390] ieee80211 phy18: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  100.298395] ieee80211 phy18: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  101.920135] ieee80211 phy18: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  102.516251] ieee80211 phy19: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  102.526124] ieee80211 phy19: rt2x00_set_rf: Info - RF chipset 0005 detected
[  102.553866] ieee80211 phy19: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  102.553890] ieee80211 phy19: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  103.081450] ieee80211 phy19: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  103.081453] ieee80211 phy19: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  104.699219] ieee80211 phy19: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  105.283242] ieee80211 phy20: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  105.293055] ieee80211 phy20: rt2x00_set_rf: Info - RF chipset 0005 detected
[  105.320895] ieee80211 phy20: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  105.320914] ieee80211 phy20: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  105.856441] ieee80211 phy20: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  105.856446] ieee80211 phy20: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  107.478214] ieee80211 phy20: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  108.034381] ieee80211 phy21: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  108.044485] ieee80211 phy21: rt2x00_set_rf: Info - RF chipset 0005 detected
[  108.072213] ieee80211 phy21: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  108.072236] ieee80211 phy21: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  108.603470] ieee80211 phy21: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  108.603473] ieee80211 phy21: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  110.225239] ieee80211 phy21: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  110.797342] ieee80211 phy22: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  110.807167] ieee80211 phy22: rt2x00_set_rf: Info - RF chipset 0005 detected
[  110.830975] ieee80211 phy22: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  110.830997] ieee80211 phy22: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  111.358504] ieee80211 phy22: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  111.358508] ieee80211 phy22: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  112.980280] ieee80211 phy22: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  113.548228] ieee80211 phy23: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  113.558095] ieee80211 phy23: rt2x00_set_rf: Info - RF chipset 0005 detected
[  113.582103] ieee80211 phy23: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  113.582122] ieee80211 phy23: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  114.117528] ieee80211 phy23: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  114.117532] ieee80211 phy23: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  115.739348] ieee80211 phy23: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  116.243597] ieee80211 phy24: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  116.253703] ieee80211 phy24: rt2x00_set_rf: Info - RF chipset 0005 detected
[  116.289406] ieee80211 phy24: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  116.289438] ieee80211 phy24: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  116.816495] ieee80211 phy24: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  116.816498] ieee80211 phy24: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  118.446264] ieee80211 phy24: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  119.010678] ieee80211 phy25: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  119.020789] ieee80211 phy25: rt2x00_set_rf: Info - RF chipset 0005 detected
[  119.052948] ieee80211 phy25: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  119.052963] ieee80211 phy25: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  119.587557] ieee80211 phy25: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  119.587563] ieee80211 phy25: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  121.205354] ieee80211 phy25: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  121.777541] ieee80211 phy26: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  121.787427] ieee80211 phy26: rt2x00_set_rf: Info - RF chipset 0005 detected
[  121.818969] ieee80211 phy26: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  121.818992] ieee80211 phy26: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  122.346604] ieee80211 phy26: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  122.346609] ieee80211 phy26: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  123.964387] ieee80211 phy26: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  124.536547] ieee80211 phy27: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  124.546444] ieee80211 phy27: rt2x00_set_rf: Info - RF chipset 0005 detected
[  124.578967] ieee80211 phy27: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  124.578996] ieee80211 phy27: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  125.121652] ieee80211 phy27: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  125.121656] ieee80211 phy27: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  126.739422] ieee80211 phy27: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  132.124962] ieee80211 phy28: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  132.134805] ieee80211 phy28: rt2x00_set_rf: Info - RF chipset 0005 detected
[  132.158220] ieee80211 phy28: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  132.158249] ieee80211 phy28: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  163.944346] ieee80211 phy28: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  168.036681] ieee80211 phy29: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  168.048072] ieee80211 phy29: rt2x00_set_rf: Info - RF chipset 0005 detected
[  168.086817] ieee80211 phy29: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  168.086844] ieee80211 phy29: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  168.633464] ieee80211 phy29: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  168.633474] ieee80211 phy29: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  170.255161] ieee80211 phy29: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  170.875375] ieee80211 phy30: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  170.886879] ieee80211 phy30: rt2x00_set_rf: Info - RF chipset 0005 detected
[  170.917258] ieee80211 phy30: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  170.917285] ieee80211 phy30: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  171.452564] ieee80211 phy30: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  171.452570] ieee80211 phy30: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  173.070302] ieee80211 phy30: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  173.642430] ieee80211 phy31: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  173.652302] ieee80211 phy31: rt2x00_set_rf: Info - RF chipset 0005 detected
[  173.676860] ieee80211 phy31: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  173.676893] ieee80211 phy31: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  174.211658] ieee80211 phy31: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  174.211669] ieee80211 phy31: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  175.829402] ieee80211 phy31: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  176.333642] ieee80211 phy32: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  176.344869] ieee80211 phy32: rt2x00_set_rf: Info - RF chipset 0005 detected
[  176.388373] ieee80211 phy32: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  176.388396] ieee80211 phy32: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  176.938567] ieee80211 phy32: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  176.938571] ieee80211 phy32: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  178.556396] ieee80211 phy32: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  179.076773] ieee80211 phy33: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  179.088131] ieee80211 phy33: rt2x00_set_rf: Info - RF chipset 0005 detected
[  179.122066] ieee80211 phy33: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  179.122088] ieee80211 phy33: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  179.649590] ieee80211 phy33: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  179.649600] ieee80211 phy33: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  181.267373] ieee80211 phy33: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  181.771599] ieee80211 phy34: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  181.781702] ieee80211 phy34: rt2x00_set_rf: Info - RF chipset 0005 detected
[  181.814460] ieee80211 phy34: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  181.814497] ieee80211 phy34: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  182.360532] ieee80211 phy34: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  182.360539] ieee80211 phy34: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  183.978336] ieee80211 phy34: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  184.494532] ieee80211 phy35: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  184.504879] ieee80211 phy35: rt2x00_set_rf: Info - RF chipset 0005 detected
[  184.541379] ieee80211 phy35: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  184.541401] ieee80211 phy35: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  185.067547] ieee80211 phy35: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  185.067557] ieee80211 phy35: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  186.685306] ieee80211 phy35: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  187.249595] ieee80211 phy36: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  187.259399] ieee80211 phy36: rt2x00_set_rf: Info - RF chipset 0005 detected
[  187.297380] ieee80211 phy36: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  187.297438] ieee80211 phy36: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  187.830599] ieee80211 phy36: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  187.830607] ieee80211 phy36: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  189.448304] ieee80211 phy36: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  189.960774] ieee80211 phy37: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  189.972046] ieee80211 phy37: rt2x00_set_rf: Info - RF chipset 0005 detected
[  190.018381] ieee80211 phy37: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  190.018409] ieee80211 phy37: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  190.565556] ieee80211 phy37: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  190.565560] ieee80211 phy37: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  192.183309] ieee80211 phy37: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  192.699568] ieee80211 phy38: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  192.709426] ieee80211 phy38: rt2x00_set_rf: Info - RF chipset 0005 detected
[  192.745102] ieee80211 phy38: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  192.745122] ieee80211 phy38: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  193.280533] ieee80211 phy38: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  193.280547] ieee80211 phy38: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  194.898314] ieee80211 phy38: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  195.410645] ieee80211 phy39: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  195.421105] ieee80211 phy39: rt2x00_set_rf: Info - RF chipset 0005 detected
[  195.461570] ieee80211 phy39: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  195.461600] ieee80211 phy39: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  195.995546] ieee80211 phy39: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  195.995553] ieee80211 phy39: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  197.613329] ieee80211 phy39: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  198.137634] ieee80211 phy40: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  198.148207] ieee80211 phy40: rt2x00_set_rf: Info - RF chipset 0005 detected
[  198.191014] ieee80211 phy40: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  198.191036] ieee80211 phy40: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  198.734548] ieee80211 phy40: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  198.734558] ieee80211 phy40: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  200.356294] ieee80211 phy40: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  200.880563] ieee80211 phy41: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  200.890702] ieee80211 phy41: rt2x00_set_rf: Info - RF chipset 0005 detected
[  200.926153] ieee80211 phy41: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  200.926176] ieee80211 phy41: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  201.453541] ieee80211 phy41: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  201.453545] ieee80211 phy41: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  203.075265] ieee80211 phy41: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  203.643669] ieee80211 phy42: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  203.654084] ieee80211 phy42: rt2x00_set_rf: Info - RF chipset 0005 detected
[  203.701482] ieee80211 phy42: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  203.701506] ieee80211 phy42: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  204.236595] ieee80211 phy42: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  204.236605] ieee80211 phy42: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  205.854355] ieee80211 phy42: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  206.374208] ieee80211 phy43: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  206.384028] ieee80211 phy43: rt2x00_set_rf: Info - RF chipset 0005 detected
[  206.407981] ieee80211 phy43: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  206.408004] ieee80211 phy43: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  206.935541] ieee80211 phy43: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  206.935546] ieee80211 phy43: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  208.557310] ieee80211 phy43: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  209.073735] ieee80211 phy44: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  209.084788] ieee80211 phy44: rt2x00_set_rf: Info - RF chipset 0005 detected
[  209.127565] ieee80211 phy44: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  209.127597] ieee80211 phy44: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  209.662565] ieee80211 phy44: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  209.662575] ieee80211 phy44: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  211.280279] ieee80211 phy44: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  211.812355] ieee80211 phy45: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  211.822185] ieee80211 phy45: rt2x00_set_rf: Info - RF chipset 0005 detected
[  211.850000] ieee80211 phy45: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  211.850025] ieee80211 phy45: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  212.381485] ieee80211 phy45: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  212.381490] ieee80211 phy45: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  213.999265] ieee80211 phy45: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  214.503611] ieee80211 phy46: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  214.514197] ieee80211 phy46: rt2x00_set_rf: Info - RF chipset 0005 detected
[  214.553318] ieee80211 phy46: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  214.553346] ieee80211 phy46: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  215.092552] ieee80211 phy46: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  215.092563] ieee80211 phy46: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  216.710308] ieee80211 phy46: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  217.238713] ieee80211 phy47: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  217.250061] ieee80211 phy47: rt2x00_set_rf: Info - RF chipset 0005 detected
[  217.302170] ieee80211 phy47: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  217.302232] ieee80211 phy47: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  217.835568] ieee80211 phy47: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  217.835578] ieee80211 phy47: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  219.453319] ieee80211 phy47: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  219.977703] ieee80211 phy48: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  219.989029] ieee80211 phy48: rt2x00_set_rf: Info - RF chipset 0005 detected
[  220.027075] ieee80211 phy48: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  220.027100] ieee80211 phy48: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  220.550530] ieee80211 phy48: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  220.550537] ieee80211 phy48: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  222.168260] ieee80211 phy48: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  222.700518] ieee80211 phy49: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  222.710356] ieee80211 phy49: rt2x00_set_rf: Info - RF chipset 0005 detected
[  222.746584] ieee80211 phy49: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  222.746613] ieee80211 phy49: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  223.285505] ieee80211 phy49: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  223.285509] ieee80211 phy49: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  224.903244] ieee80211 phy49: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  225.439537] ieee80211 phy50: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  225.449600] ieee80211 phy50: rt2x00_set_rf: Info - RF chipset 0005 detected
[  225.489735] ieee80211 phy50: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  225.489764] ieee80211 phy50: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  226.028534] ieee80211 phy50: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  226.028540] ieee80211 phy50: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  227.646278] ieee80211 phy50: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  228.154694] ieee80211 phy51: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  228.166041] ieee80211 phy51: rt2x00_set_rf: Info - RF chipset 0005 detected
[  228.213729] ieee80211 phy51: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  228.213761] ieee80211 phy51: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  228.755451] ieee80211 phy51: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  228.755456] ieee80211 phy51: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  230.373214] ieee80211 phy51: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  230.885604] ieee80211 phy52: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  230.896021] ieee80211 phy52: rt2x00_set_rf: Info - RF chipset 0005 detected
[  230.928395] ieee80211 phy52: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  230.928415] ieee80211 phy52: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  231.466498] ieee80211 phy52: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  231.466505] ieee80211 phy52: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  233.084294] ieee80211 phy52: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  233.648553] ieee80211 phy53: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  233.658369] ieee80211 phy53: rt2x00_set_rf: Info - RF chipset 0005 detected
[  233.682815] ieee80211 phy53: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  233.682855] ieee80211 phy53: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  234.225491] ieee80211 phy53: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  234.225497] ieee80211 phy53: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  235.843278] ieee80211 phy53: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  236.351345] ieee80211 phy54: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  236.361380] ieee80211 phy54: rt2x00_set_rf: Info - RF chipset 0005 detected
[  236.393529] ieee80211 phy54: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  236.393560] ieee80211 phy54: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  236.924538] ieee80211 phy54: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  236.924549] ieee80211 phy54: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  238.542291] ieee80211 phy54: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  239.126519] ieee80211 phy55: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  239.137742] ieee80211 phy55: rt2x00_set_rf: Info - RF chipset 0005 detected
[  239.184556] ieee80211 phy55: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  239.184585] ieee80211 phy55: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  239.723518] ieee80211 phy55: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  239.723522] ieee80211 phy55: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  241.341365] ieee80211 phy55: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  241.849568] ieee80211 phy56: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  241.859425] ieee80211 phy56: rt2x00_set_rf: Info - RF chipset 0005 detected
[  241.883503] ieee80211 phy56: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  241.883533] ieee80211 phy56: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  242.402556] ieee80211 phy56: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  242.402567] ieee80211 phy56: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  244.020264] ieee80211 phy56: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  244.580719] ieee80211 phy57: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  244.592010] ieee80211 phy57: rt2x00_set_rf: Info - RF chipset 0005 detected
[  244.642424] ieee80211 phy57: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  244.642461] ieee80211 phy57: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  245.181554] ieee80211 phy57: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  245.181558] ieee80211 phy57: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  246.799256] ieee80211 phy57: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  247.311442] ieee80211 phy58: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  247.322802] ieee80211 phy58: rt2x00_set_rf: Info - RF chipset 0005 detected
[  247.370153] ieee80211 phy58: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  247.370195] ieee80211 phy58: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  247.904561] ieee80211 phy58: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  247.904572] ieee80211 phy58: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  249.522349] ieee80211 phy58: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  250.086686] ieee80211 phy59: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  250.098251] ieee80211 phy59: rt2x00_set_rf: Info - RF chipset 0005 detected
[  250.132273] ieee80211 phy59: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  250.132302] ieee80211 phy59: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  250.663528] ieee80211 phy59: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  250.663532] ieee80211 phy59: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  252.289346] ieee80211 phy59: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  252.861451] ieee80211 phy60: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  252.871320] ieee80211 phy60: rt2x00_set_rf: Info - RF chipset 0005 detected
[  252.908564] ieee80211 phy60: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  252.908602] ieee80211 phy60: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  253.430632] ieee80211 phy60: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  253.430637] ieee80211 phy60: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  255.048422] ieee80211 phy60: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  255.668737] ieee80211 phy61: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  255.678587] ieee80211 phy61: rt2x00_set_rf: Info - RF chipset 0005 detected
[  255.707263] ieee80211 phy61: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  255.707306] ieee80211 phy61: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  256.233709] ieee80211 phy61: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  256.233718] ieee80211 phy61: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  257.851455] ieee80211 phy61: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  258.371902] ieee80211 phy62: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  258.383271] ieee80211 phy62: rt2x00_set_rf: Info - RF chipset 0005 detected
[  258.433479] ieee80211 phy62: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  258.433501] ieee80211 phy62: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  258.976728] ieee80211 phy62: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  258.976741] ieee80211 phy62: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  260.594516] ieee80211 phy62: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  261.110732] ieee80211 phy63: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  261.121495] ieee80211 phy63: rt2x00_set_rf: Info - RF chipset 0005 detected
[  261.168637] ieee80211 phy63: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  261.168660] ieee80211 phy63: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  261.691691] ieee80211 phy63: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  261.691696] ieee80211 phy63: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  263.309498] ieee80211 phy63: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  263.885883] ieee80211 phy64: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  263.897110] ieee80211 phy64: rt2x00_set_rf: Info - RF chipset 0005 detected
[  263.939949] ieee80211 phy64: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  263.939980] ieee80211 phy64: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  264.466799] ieee80211 phy64: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  264.466813] ieee80211 phy64: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  266.084546] ieee80211 phy64: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  266.620815] ieee80211 phy65: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  266.630925] ieee80211 phy65: rt2x00_set_rf: Info - RF chipset 0005 detected
[  266.670415] ieee80211 phy65: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  266.670453] ieee80211 phy65: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  267.201741] ieee80211 phy65: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  267.201745] ieee80211 phy65: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  268.819548] ieee80211 phy65: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  269.343967] ieee80211 phy66: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  269.355342] ieee80211 phy66: rt2x00_set_rf: Info - RF chipset 0005 detected
[  269.398710] ieee80211 phy66: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  269.398757] ieee80211 phy66: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  269.932796] ieee80211 phy66: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  269.932806] ieee80211 phy66: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  271.550553] ieee80211 phy66: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  272.062690] ieee80211 phy67: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  272.073054] ieee80211 phy67: rt2x00_set_rf: Info - RF chipset 0005 detected
[  272.112751] ieee80211 phy67: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  272.112781] ieee80211 phy67: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  272.647783] ieee80211 phy67: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  272.647797] ieee80211 phy67: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  274.265529] ieee80211 phy67: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  274.817775] ieee80211 phy68: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  274.827574] ieee80211 phy68: rt2x00_set_rf: Info - RF chipset 0005 detected
[  274.847348] ieee80211 phy68: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  274.847371] ieee80211 phy68: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  275.378721] ieee80211 phy68: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  275.378725] ieee80211 phy68: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  276.996533] ieee80211 phy68: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  277.564984] ieee80211 phy69: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  277.576059] ieee80211 phy69: rt2x00_set_rf: Info - RF chipset 0005 detected
[  277.614586] ieee80211 phy69: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  277.614608] ieee80211 phy69: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  278.153777] ieee80211 phy69: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  278.153782] ieee80211 phy69: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  279.771539] ieee80211 phy69: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  280.283779] ieee80211 phy70: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  280.293594] ieee80211 phy70: rt2x00_set_rf: Info - RF chipset 0005 detected
[  280.313108] ieee80211 phy70: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  280.313127] ieee80211 phy70: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  280.848742] ieee80211 phy70: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  280.848747] ieee80211 phy70: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  282.466474] ieee80211 phy70: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  282.974583] ieee80211 phy71: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  282.984589] ieee80211 phy71: rt2x00_set_rf: Info - RF chipset 0005 detected
[  283.018074] ieee80211 phy71: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  283.018127] ieee80211 phy71: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  283.567759] ieee80211 phy71: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  283.567767] ieee80211 phy71: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  285.185466] ieee80211 phy71: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  285.777845] ieee80211 phy72: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  285.787665] ieee80211 phy72: rt2x00_set_rf: Info - RF chipset 0005 detected
[  285.817407] ieee80211 phy72: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  285.817457] ieee80211 phy72: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  286.354747] ieee80211 phy72: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  286.354755] ieee80211 phy72: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  287.972560] ieee80211 phy72: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  288.492747] ieee80211 phy73: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  288.503918] ieee80211 phy73: rt2x00_set_rf: Info - RF chipset 0005 detected
[  288.552584] ieee80211 phy73: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  288.552647] ieee80211 phy73: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  289.081802] ieee80211 phy73: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  289.081811] ieee80211 phy73: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  290.699550] ieee80211 phy73: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  291.288030] ieee80211 phy74: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  291.299349] ieee80211 phy74: rt2x00_set_rf: Info - RF chipset 0005 detected
[  291.346623] ieee80211 phy74: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  291.346660] ieee80211 phy74: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  291.888889] ieee80211 phy74: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  291.888902] ieee80211 phy74: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  293.506646] ieee80211 phy74: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  294.066965] ieee80211 phy75: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  294.076785] ieee80211 phy75: rt2x00_set_rf: Info - RF chipset 0005 detected
[  294.096609] ieee80211 phy75: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  294.096634] ieee80211 phy75: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  294.631889] ieee80211 phy75: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  294.631899] ieee80211 phy75: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  296.249688] ieee80211 phy75: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  296.769718] ieee80211 phy76: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  296.779626] ieee80211 phy76: rt2x00_set_rf: Info - RF chipset 0005 detected
[  296.812420] ieee80211 phy76: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  296.812460] ieee80211 phy76: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  297.354896] ieee80211 phy76: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  297.354906] ieee80211 phy76: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  298.972672] ieee80211 phy76: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  299.485068] ieee80211 phy77: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  299.496420] ieee80211 phy77: rt2x00_set_rf: Info - RF chipset 0005 detected
[  299.530851] ieee80211 phy77: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  299.530877] ieee80211 phy77: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  300.069831] ieee80211 phy77: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  300.069835] ieee80211 phy77: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  301.687656] ieee80211 phy77: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  302.268010] ieee80211 phy78: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  302.278112] ieee80211 phy78: rt2x00_set_rf: Info - RF chipset 0005 detected
[  302.307712] ieee80211 phy78: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  302.307763] ieee80211 phy78: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  302.860962] ieee80211 phy78: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  302.860973] ieee80211 phy78: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  304.478678] ieee80211 phy78: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  305.023101] ieee80211 phy79: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  305.034468] ieee80211 phy79: rt2x00_set_rf: Info - RF chipset 0005 detected
[  305.068823] ieee80211 phy79: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  305.068849] ieee80211 phy79: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  305.599945] ieee80211 phy79: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  305.599961] ieee80211 phy79: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  307.217732] ieee80211 phy79: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  307.725939] ieee80211 phy80: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  307.736010] ieee80211 phy80: rt2x00_set_rf: Info - RF chipset 0005 detected
[  307.771553] ieee80211 phy80: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  307.771574] ieee80211 phy80: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  308.310898] ieee80211 phy80: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  308.310903] ieee80211 phy80: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  309.928707] ieee80211 phy80: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  310.441026] ieee80211 phy81: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  310.451310] ieee80211 phy81: rt2x00_set_rf: Info - RF chipset 0005 detected
[  310.490626] ieee80211 phy81: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  310.490653] ieee80211 phy81: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  311.029915] ieee80211 phy81: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  311.029920] ieee80211 phy81: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  312.647694] ieee80211 phy81: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  313.148084] ieee80211 phy82: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  313.159442] ieee80211 phy82: rt2x00_set_rf: Info - RF chipset 0005 detected
[  313.197179] ieee80211 phy82: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  313.197221] ieee80211 phy82: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  313.732862] ieee80211 phy82: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  313.732868] ieee80211 phy82: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  315.350621] ieee80211 phy82: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  315.862845] ieee80211 phy83: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  315.872661] ieee80211 phy83: rt2x00_set_rf: Info - RF chipset 0005 detected
[  315.906596] ieee80211 phy83: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  315.906652] ieee80211 phy83: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  316.447890] ieee80211 phy83: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  316.447901] ieee80211 phy83: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  318.065584] ieee80211 phy83: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  318.621883] ieee80211 phy84: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  318.631710] ieee80211 phy84: rt2x00_set_rf: Info - RF chipset 0005 detected
[  318.651949] ieee80211 phy84: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  318.651980] ieee80211 phy84: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  319.174851] ieee80211 phy84: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  319.174857] ieee80211 phy84: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  320.792642] ieee80211 phy84: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]

```


Thank you very very very much!

---

### Post by chili555 on 2015-02-25
I am confident this is the problem:> [   83.976510] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   83.976517] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   85.594280] ieee80211 phy12: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]I am less confident that I know the solution. Googling the error suggests that a kernel version of 3.15 or later fixes the issue. You are running 3.13.0-45-generic. There are several ways to address this. You could download and try a live session of Ubuntu 14.10 which uses 3.16. If your wireless works as expected, install it.

You could simply install a 3.16 kernel and reboot. We could also install backports-3.16 which installs the wireless driver suite only.

Which do you prefer? I prefer, and use myself, Ubuntu 14.10.

Whichever you choose, I will be happy to assist.

---

### Post by zeuse on 2015-02-26
I could install backports, but by terminal? I didn't found it in Ubuntu Software Center.
If i'll install kernel? Is it a little bit "forced" in Ubuntu 14.04LTS?

I know Ubuntu 14.10 is better, but i installed LTS only one month ago, after a very long backup. Generally i prefer LTS, i think it is more stable, but in this case i was wrong, eh eh.

However i'll try Ubuntu 14.10 live.

Thanks.

---

### Post by Bucky Ball on 2015-02-26
Just jumping in here, and don't want to tread on your toes, old Uncle chili (;)), but 14.10 is only supported for a couple more months and then OP would need to upgrade to 15.04. A backport or installing the 3.16 kernel might be the better option. 14.04 will, I believe, will be moving to the 3.16 kernel sometime in the future. ;)

Good luck, however it swings.

---

### Post by coffeecat on 2015-02-26
Point of information - 14.10 is supported until July 2015, which is a tad more than a "couple more months".

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Although users of 14.10 (such as myself) need to be on their toes, there is a comfortable window of opportunity for upgrading to 15.04 after 15.04 is released in April.

---

### Post by Bucky Ball on 2015-02-26
> **coffeecat said:**
> Point of information - 14.10 is supported until July 2015.

Thanks for that. My mistake. Noted. ;)

---

### Post by chili555 on 2015-02-26
The primary reason I suggested the live session of 14.10 is to test if the 3.16 kernel fixed the wireless problem. Running a live session involves no changes to an existing system at all and can be shut down and ended easily. Once we know that it does or doesn't fix the rt2800usb issue, we can proceed in any of the ways I mentioned above.

We are hoping to *NOT* see this in dmesg:> [ 83.976510] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[ 83.976517] ieee80211 phy12: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[ 85.594280] ieee80211 phy12: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff] > I could install backports, but by terminal?Yes, exactly.> If i'll install kernel? Is it a little bit "forced" in Ubuntu 14.04LTS?
I haven't any idea what you mean by 'forced.' Aside from your wireless hopefully working, you probably will notice no difference at all! Of course, if you have an exotic video card setup for which you already struggled to compile an equally exotic video driver, it could be problematic. Again, running the live session will tell us a lot about not only your wireless drivers, but also video, sound, etc.

Compiling backports is the way to get just the driver suite and just for Ralink devices so seems the cleanest. However, it is built for your currently running kernel only, 3.13.0-45 in your case. When Update Manager installs 3.13.0-46, after the requested reboot, you must recompile. And then again for -47 a few weeks later, etc. It is easy to do but a minor inconvenience.

If you install the 3.16 kernel or else 14.10, no recompile is needed after updates.

Each method is a different level of interesting, shall we say?

---

### Post by zeuse on 2015-02-28
No way.

Ubuntu 14.10 live: dmesg | grep rt2
```

[  767.340131] ieee80211 phy33: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  767.340160] ieee80211 phy33: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  769.468847] ieee80211 phy33: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  770.397562] ieee80211 phy34: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  770.407451] ieee80211 phy34: rt2x00_set_rf: Info - RF chipset 0005 detected

```

Ubuntu 14.04.2LTS live: dmesg | grep rt2
```

[  507.165443] ieee80211 phy5: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  507.165464] ieee80211 phy5: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  509.312652] ieee80211 phy5: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  510.233328] ieee80211 phy6: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  510.243075] ieee80211 phy6: rt2x00_set_rf: Info - RF chipset 0005 detected

```

---

