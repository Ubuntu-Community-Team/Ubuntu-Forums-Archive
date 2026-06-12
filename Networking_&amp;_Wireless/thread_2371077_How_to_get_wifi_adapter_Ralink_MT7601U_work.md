---
title: "How to get wifi adapter Ralink MT7601U work"
date: 2017-09-10
forum: Networking &amp; Wireless
---

### Post by chenzero on 2017-09-10
overall, the problem I encountered is: all three drivers I tried for MT7601U are not working on Ubuntu 16.04, 64bits box.

In the beginning, when the adapter is pluged in, it's mounted as a disk, and the lsusb shows:
Bus 003 Device 010: ID 148f:2878 Ralink Technology, Corp. 
the disk includes the driver files for Windows.

after eject the disk, the lsusb shows:
Bus 003 Device 011: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter

I tried following 3 drivers:
1) the default mt7601u included in the kernel: 4.4.0-91-generic
after eject the disk, 
$> lsmod|grep mt
mt7601u               102400  0
mac80211              737280  1 mt7601u
cfg80211              565248  2 mac80211,mt7601u
binfmt_misc            20480  1
$> modinfo mt7601u
filename:       /lib/modules/4.4.0-91-generic/kernel/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
srcversion:     E8B632D369E0C2A9F1CF7D8
alias:          usb:v7392p7710d*dc*dsc*dp*ic*isc*ip*in*
......
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-91-generic SMP mod_unload modversions 

$> dmesg
// begin----------------------------------------
[ 4581.094119] usb 3-4: USB disconnect, device number 6
[ 4584.872751] usb 3-4: new high-speed USB device number 7 using xhci_hcd
[ 4585.001408] usb 3-4: New USB device found, idVendor=148f, idProduct=2878
[ 4585.001413] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4585.001416] usb 3-4: Product: &#1033;
[ 4585.001418] usb 3-4: Manufacturer: &#1033;
[ 4585.001753] usb-storage 3-4:1.0: USB Mass Storage device detected
[ 4585.001873] scsi host6: usb-storage 3-4:1.0
[ 4586.001122] scsi 6:0:0:0: CD-ROM            MediaTek Flash autorun    0.01 PQ: 0 ANSI: 0 CCS
[ 4586.001978] sr 6:0:0:0: [sr0] scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[ 4586.002529] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 4586.002716] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 4619.658385] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4619.691737] ISOFS: changing to secondary root
[ 4691.563347] usb 3-4: USB disconnect, device number 7
[ 4693.638315] usb 3-4: new high-speed USB device number 8 using xhci_hcd
[ 4693.766896] usb 3-4: New USB device found, idVendor=148f, idProduct=2878
[ 4693.766901] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4693.766903] usb 3-4: Product: &#1033;
[ 4693.766905] usb 3-4: Manufacturer: &#1033;
[ 4693.767338] usb-storage 3-4:1.0: USB Mass Storage device detected
[ 4693.768063] scsi host7: usb-storage 3-4:1.0
[ 4694.766737] scsi 7:0:0:0: CD-ROM            MediaTek Flash autorun    0.01 PQ: 0 ANSI: 0 CCS
[ 4694.767423] sr 7:0:0:0: [sr0] scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[ 4694.767908] sr 7:0:0:0: Attached scsi CD-ROM sr0
[ 4694.768147] sr 7:0:0:0: Attached scsi generic sg1 type 5
[ 4728.418255] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4728.427856] ISOFS: changing to secondary root
[ 4733.824182] sr 7:0:0:0: [sr0] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4733.824190] sr 7:0:0:0: [sr0] tag#0 CDB: Start/Stop Unit 1b 00 00 00 02 00
[ 4733.824218] usb 3-4: USB disconnect, device number 8
[ 4733.824281] sr 7:0:0:0: [sr0] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4733.824291] sr 7:0:0:0: [sr0] tag#0 CDB: Prevent/Allow Medium Removal 1e 00 00 00 00 00
[ 4734.099901] usb 3-4: new high-speed USB device number 9 using xhci_hcd
[ 4734.238749] usb 3-4: New USB device found, idVendor=148f, idProduct=7601
[ 4734.238754] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4734.238757] usb 3-4: Product: 802.11 n WLAN
[ 4734.238772] usb 3-4: Manufacturer: MediaTek
[ 4734.238775] usb 3-4: SerialNumber: 1.0
[ 4735.432096] usb 3-4: reset high-speed USB device number 9 using xhci_hcd
[ 4735.562543] mt7601u 3-4:1.0: ASIC revision: 76010001 MAC revision: 76010500
[ 4735.563089] mt7601u 3-4:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[ 4739.011624] mt7601u 3-4:1.0: Vendor request req:07 off:09a8 failed:-110
[ 4742.131399] mt7601u 3-4:1.0: Vendor request req:02 off:09a8 failed:-110
[ 4745.251254] mt7601u 3-4:1.0: Vendor request req:07 off:0734 failed:-110
[ 4748.371056] mt7601u 3-4:1.0: Vendor request req:42 off:0230 failed:-110
[ 4751.490880] mt7601u 3-4:1.0: Vendor request req:07 off:0080 failed:-110
[ 4754.610694] mt7601u 3-4:1.0: Vendor request req:02 off:0080 failed:-110
[ 4757.730501] mt7601u 3-4:1.0: Vendor request req:02 off:0080 failed:-110
[ 4757.730548] mt7601u: probe of 3-4:1.0 failed with error -110
[ 4757.730870] usbcore: registered new interface driver mt7601u
// end ----------------------------------------

$> iconfig -a // do not have new interface

2) DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2
this driver is downloaded from MediaTek:
[https://www.mediatek.com/products/broadbandWifi/mt7601u](https://www.mediatek.com/products/broadbandWifi/mt7601u)
to compile, need to patch some source code 

file: rt_linux.h
typedef struct _OS_FS_INFO_
{
	//int				fsuid;
	//int				fsgid;
	kuid_t fsuid; 
	kgid_t fsgid;
	mm_segment_t	fs;
} OS_FS_INFO;

config.mk
~~~~~~~~~~~~~
add following line after line:225
WFLAGS +=  -Wno-error=date-time

After compile, 
$> sudo insmod mt7601Usta.ko 
$> dmesg
// begin -------------------------------------------
[ 3534.318919] #
[ 3534.398911] #
[ 3534.478911] #
[ 3534.558903] #
[ 3534.563894] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Idx=0x1000,pAd->Flags=0x0
[ 3534.638897] #
[ 3534.718885] #
[ 3534.798891] #
[ 3534.878884] #
[ 3534.958882] #
[ 3535.038905] #
[ 3535.118870] #
[ 3535.198853] #
[ 3535.278861] #
[ 3535.358847] #
[ 3535.363822] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Idx=0x1000,pAd->Flags=0x0
[ 3535.438850] #
[ 3535.518846] #
[ 3535.598850] #
[ 3535.678839] #
[ 3535.758833] #
[ 3535.838830] #
[ 3535.918824] #
[ 3535.998824] #
[ 3536.078816] #
[ 3536.158809] #
[ 3536.163798] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Idx=0x1000,pAd->Flags=0x0
[ 3536.163811] WaitForAsicReady(0xffffffff):AsicNotReady!
[ 3536.238800] #
[ 3536.318800] #
[ 3536.398793] #
[ 3536.478791] #
[ 3536.558785] #
[ 3536.638771] #
[ 3536.718777] #
[ 3536.798772] #
[ 3536.878762] #
[ 3536.958764] #
[ 3536.963762] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Idx=0x24,pAd->Flags=0x0
[ 3536.963765] NVM is EFUSE
[ 3536.963767] Efuse Size=0x2d [Range:2d0-2fc] 
[ 3536.963769] Endpoint(8) is for In-band Command
[ 3536.963770] Endpoint(4) is for WMM0 AC0
[ 3536.963772] Endpoint(5) is for WMM0 AC1
[ 3536.963773] Endpoint(6) is for WMM0 AC2
[ 3536.963774] Endpoint(7) is for WMM0 AC3
[ 3536.963776] Endpoint(9) is for WMM1 AC0
[ 3536.963777] Endpoint(84) is for Data-In
[ 3536.963778] Endpoint(85) is for Command Rsp
[ 3536.963781] Allocate a net device with private data size=0!
[ 3536.963802] Allocate net device ops success!
[ 3536.963805] The name of the new ra interface is ra0...
[ 3536.963807] RtmpOSNetDevAttach()--->
[ 3536.964094] <---RtmpOSNetDevAttach(), ret=0
[ 3536.964097] <===rt2870_probe()!
[ 3536.964225] usbcore: registered new interface driver rt2870
[ 3536.964448] ===>rt_ioctl_giwrange
[ 3536.964457] INFO::Network is down!
[ 3536.964545] INFO::Network is down!
[ 3536.973329] ModemManager[6460]: segfault at 0 ip 0000000000431ab3 sp 00007ffd5bd86680 error 4 in ModemManager[400000+103000]
// end -------------------------------------------

3) the driver on [https://github.com/art567/mt7601usta.git](https://github.com/art567/mt7601usta.git)
the compile and installation steps for this driver are almost same with driver 2.
I also can not get it work.

Could you help on how to get Ralink MT7601 work?
Thank you very much!

---

### Post by chenzero on 2017-09-10
Attach the wireless script result here.
[ATTACH]276684[/ATTACH]
Thanks!

---

### Post by jeremy31 on 2017-09-10
I would file a bug report, see [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) against package linux

---

### Post by chenzero on 2017-09-10
I created a bug report on:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1716301](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1716301)
Thanks for your suggestion!

---

