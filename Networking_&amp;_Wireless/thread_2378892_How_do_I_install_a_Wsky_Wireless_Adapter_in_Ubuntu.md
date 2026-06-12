---
title: "How do I install a Wsky Wireless Adapter in Ubuntu 17.10"
date: 2017-11-28
forum: Networking &amp; Wireless
---

### Post by rranger2 on 2017-11-28
I've just purchased [this wifi adapter]("https://www.amazon.com/gp/product/B0779VHS6S/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1") which, as you can see, is supposed to be Linux capable. In fact, it comes with a CD that has Linux (kernel 2.67.18 ~ 4.1).zip and .rar files. But, of course, there are absolutely ZERO instructions on how to install the adapter. Can someone help me with instructions on how I'd go about installing the software for the adapter? This is a Realtek-based device, which might help. 

Thanks!

---

### Post by wildmanne39 on 2017-11-28
*Thread moved to **Networking & Wireless to a more appropriate forum**.*

I have never seen a driver from a disc work in Ubuntu or linux.

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 

Make sure the adapter is plugged in before running the wireless script.

Thanks

---

### Post by rranger2 on 2017-11-28
Thanks for the quick reply. The problem is, I'm running this from Windows 10 at the moment because I can't get it to connect in Ubuntu. If I switch to Ubuntu, do I navigate to this page using my old adapter and then run your script without internet access (because I've plugged in the new one)? Kind of a Catch 22. Please elaborate on how this will work without internet access.

I think I just answered my own question. I thought you had created a self-executing file, but I see that I'll need to do it in terminal. I'll report back.

---

### Post by wildmanne39 on 2017-11-28
If you have ethernet connection or can tether your cell phone that will work, there is a link on the page with the script commands that tells you how to run it without an internet connection.

If you still have issues with running the script please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by rranger2 on 2017-11-28
Hi:

Thanks for helping me with this. Here's the output for the commmands above:

```
For: cat /etc/lsb-release; uname -a
Response: 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
Linux don-Inspiron-518 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


For: lspci -nnk | grep -iA2 net
Response:
03:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
	Subsystem: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:027d]
	Kernel driver in use: r8169
	Kernel modules: r8169

For:lsusb
Response:
Bus 002 Device 007: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 003: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:0a23 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



For:iwconfig
Response:
wlx00026fae7662  IEEE 802.11  ESSID:"xfinityroxnetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 20:F1:9E:DF:DA:8B   
          Bit Rate=39 Mb/s   Tx-Power=30 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:172  Invalid misc:204   Missed beacon:0


lo        no wireless extensions.


enp4s0    no wireless extensions.


For: rfkill list all
Response: 
3: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no


For:lsmod
Response:
Module                  Size  Used by
ccm                    20480  6
arc4                   16384  2
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib             114688  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              778240  3 rt2800lib,rt2x00lib,rt2x00usb
cfg80211              610304  2 rt2x00lib,mac80211
nls_utf8               16384  1
isofs                  45056  1
binfmt_misc            20480  1
nls_iso8859_1          16384  1
dcdbas                 16384  0
dell_smm_hwmon         16384  0
joydev                 20480  0
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  5
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
input_leds             16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_usb_audio         196608  1
snd_usbmidi_lib        32768  1 snd_usb_audio
coretemp               16384  0
snd_hwdep              20480  2 snd_hda_codec,snd_usb_audio
snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
kvm                   581632  0
irqbypass              16384  1 kvm
serio_raw              16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                24576  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  25 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
amdgpu               2007040  0
uas                    24576  0
usb_storage            69632  4 uas
hid_generic            16384  0
amdkfd                188416  1
usbhid                 49152  0
amd_iommu_v2           20480  1 amdkfd
hid                   118784  2 hid_generic,usbhid
radeon               1470464  19
firewire_ohci          40960  0
psmouse               147456  0
r8169                  81920  0
firewire_core          65536  1 firewire_ohci
i2c_algo_bit           16384  2 amdgpu,radeon
pata_acpi              16384  0
crc_itu_t              16384  1 firewire_core
mii                    16384  1 r8169
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        167936  2 amdgpu,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   356352  10 amdgpu,radeon,ttm,drm_kms_helper
```

The only concern I have is that I suspect the Ralink wireless adapter that you see here is the Rosewill adapter I'm currently using (since the system refuses to identify the Realtek-based adapter I'm trying to use (much faster, 5 GHZ, etc.). Any help you can give will be greatly appreciated.

---

### Post by wildmanne39 on 2017-11-28
Follow the directions in post 14 here:

[https://ubuntuforums.org/showthread.php?t=2362577&page=2](https://ubuntuforums.org/showthread.php?t=2362577&page=2)

after you do the following:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Please note that the driver will not build or work with kernels newer then what comes in 16.04 or 16.04.2. 

You will need an internet connection to download the driver.

---

### Post by Yellow Pasque on 2017-11-29
> **wildmanne39 said:**
> Please note that the driver will not build or work with kernels newer then what comes in 16.04 or 16.04.2

I just added a patch in that thread you linked to. Feel free to test it. I'm guessing the OP may also need to add the USB ID in os_dep/linux/usb_intf.c file. It looks to me like only the Bluetooth version (0bda:b82c) is there.

```
#ifdef CONFIG_RTL8822B
	/*=== Realtek demoboard ===*/
	{USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
	{USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
	{USB_DEVICE(0x0b05, 0x184c), .driver_info = RTL8822B}, /* ASUS USB AC53 */

//Add this?     {USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},

	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```

---

### Post by rranger2 on 2017-11-29
Thank you both wildmanne39 and Temujin for the quick responses. This morning I realized that the CD supplied with the dongle includes an install.sh script in the Linux zipped and rar files. I extracted the zip file to my desktop and ran the install.sh file. It did something, but I'm not sure what, since the dongle still doesn't work. 

I'm at work at the moment, but I'll try what you suggest when I get home this evening. In the interim, is there something I'm not getting about the install.sh script? Do all the files need to be extracted to a particular location before I can run the install script? Again, I appreciate your help! And, BTW, I'm keeping in mind your point, wildemanne39, that you've never seen a driver from a disk work (but I still think it may be worth a shot, provided I can figure out how to do it correctly).

---

### Post by Yellow Pasque on 2017-11-29
> ran the install.sh file. It did something

Maybe you could give us the terminal output so we know what "something" is.

---

### Post by rranger2 on 2017-11-29
> **Temüjin said:**
> Maybe you could give us the terminal output so we know what "something" is.

LOL, and touche! I'll look into that when I get home from work.

---

### Post by jeremy31 on 2017-11-29
> **Temüjin said:**
> I just added a patch in that thread you linked to. Feel free to test it. I'm guessing the OP may also need to add the USB ID in os_dep/linux/usb_intf.c file. It looks to me like only the Bluetooth version (0bda:b82c) is there.

```
#ifdef CONFIG_RTL8822B
	/*=== Realtek demoboard ===*/
	{USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
	{USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
	{USB_DEVICE(0x0b05, 0x184c), .driver_info = RTL8822B}, /* ASUS USB AC53 */

//Add this?     {USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},

	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```

I will see about adding the patch when I get home

---

### Post by wildmanne39 on 2017-11-29
Thanks Temüjin!

---

### Post by rranger2 on 2017-11-29
> **Temüjin said:**
> Maybe you could give us the terminal output so we know what "something" is.

Hi:

I ran the install.sh file and this was the output:

```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58.tar.gz
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_mp.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_ioctl_query.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_wapi_sms4.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_ioctl_rtl.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_wapi.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/efuse/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/efuse/rtw_efuse.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_mlme_ext.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_sta_mgt.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_io.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_rf.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_xmit.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_vht.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_ioctl_set.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_iol.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_odm.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_cmd.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_ap.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_pwrctrl.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_tdls.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_bt_mp.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_eeprom.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_debug.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_beamforming.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_wlan_util.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_mlme.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_p2p.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_sreset.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_btcoex.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_mp_ioctl.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_ieee80211.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_recv.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_br_ext.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_mem.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/core/rtw_security.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_service_xp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_br_ext.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_pci.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/mp_custom_oid.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_vht.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8703BPhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_iol.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8723BPhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/usb_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_gspi.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_service_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/usb_ops_linux.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/swabb.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/little_endian.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/big_endian.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/swab.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/byteorder/generic.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8723BPwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_io.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/ieee80211.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8821APwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_conf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/ip.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_service_linux.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_wifi_regd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_gspi.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_ops_xp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/usb_vendor_req.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_efuse.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8821a_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_xp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_com_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mlme_ext.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8821a_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_android.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/xmit_osdep.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_osintf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188EPhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8814PhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8812PhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_com_reg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/autoconf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/pci_osintf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_com.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_ops_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8192EPwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ioctl_query.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_wapi.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ioctl.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/wifi.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_version.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8192EPhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/if_ether.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mlme.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8703BPwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_debug.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/gspi_ops_linux.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_sdio.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/mlme_osdep.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_beamforming.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_data.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/pci_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/circ_buf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/HalPwrSeqCmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_byteorder.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/nic_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_btcoex.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8192EPhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/wlan_bssdef.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_p2p.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8723BPhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/custom_gpio.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/ethernet.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ioctl_rtl.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/gspi_ops.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_event.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_ops_linux.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/linux/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/linux/wireless.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188FPwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_service.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_sdio.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8192e_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_qos.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_com_phycfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/ieee80211_ext.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ap.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_phy.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/recv_osdep.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_cmd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_pwrctrl.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_ops.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/gspi_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_odm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/usb_ops.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_com_h2c.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/usb_osintf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_led.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8812PhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sdio_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_pg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_phy_reg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mem.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8703BPhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mp_ioctl.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_tdls.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8812PwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8814PwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ioctl_set.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188FPhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/basic_types.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_ic_cfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_bt_mp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188EPhyCfg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/drv_types_linux.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_eeprom.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8814a_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_xmit.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8723PwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/h2clbk.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8723b_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188EPwrSeq.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/pci_ops.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_ht.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8814PhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_intf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/Hal8188FPhyReg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mp_phy_regdef.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/cmd_osdep.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_mp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_security.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_recv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8703b_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188f_hal.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/osdep_service_bsd.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_btcoex.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8188e_spec.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/HalVerDef.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtl8812a_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/gspi_osintf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/sta_info.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/rtw_sreset.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/include/hal_intf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/runwpa
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/clean
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/Kconfig
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/ifcfg-wlan0
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/Makefile
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/wlan0dhcp
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_dm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_hci/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_hci/hal_usb.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/efuse/efuse_mask.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_dm.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/led/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/led/hal_usb_led.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_xmit.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_hal_init.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/Hal8821APwrSeq.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_rf6052.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/Hal8812PwrSeq.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_cmd.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_dm.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_sreset.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/rtl8812a_phycfg.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/usb_halinit.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/rtl8812au_led.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/rtl8812a/usb/usb_ops_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_mp.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_win.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_noisemonitor.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_pathdiv.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_hwconfig.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_ce.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_rainfo.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halhwimg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_cfotracking.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dynamictxpower.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_interface.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_win.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_bb.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_fw.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_win.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_ap.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/phydm_regconfig8812a.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/phydm_rtl8812a.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_ce.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/phydm_rtl8812a.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_mac.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_rf.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_mac.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halphyrf_8812a_ap.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/mp_precomp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_bb.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/phydm_regconfig8812a.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8812a/halhwimg8812a_fw.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_antdect.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_edcaturbocheck.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_precomp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_ap.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_regdefine11ac.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_adaptivity.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_debug.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_win.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_cfotracking.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_beamforming.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_acs.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_types.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dig.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_adaptivity.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dynamicbbpowersaving.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_ap.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_hwconfig.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_pre_define.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_win.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halphyrf_8821a_ce.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_regconfig8821a.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_rf.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_mac.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_rtl8821a.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halphyrf_8821a_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_bb.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halphyrf_8821a_win.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_bb.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/version_rtl8821a.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_ap.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_fw.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_ce.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_win.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_rtl8821a.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_mac.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halphyrf_8821a_win.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_ap.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_regconfig8821a.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_rf.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/mp_precomp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/phydm_iqk_8821a_win.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtl8821a/halhwimg8821a_fw.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_regdefine11n.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_reg.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dynamicbbpowersaving.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_rxhp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dynamictxpower.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_ce.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_noisemonitor.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_ce.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_debug.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_acs.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtchnlplan.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_dig.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_win.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_powertracking_ap.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_edcaturbocheck.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_rainfo.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_interface.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/mp_precomp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/halphyrf_ap.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_rxhp.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_beamforming.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_antdect.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_antdiv.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/rtchnlplan.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_pathdiv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/phydm/phydm_antdiv.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/HalPwrSeqCmd.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_btcoex.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_com_phycfg.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821a1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192e1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8703b2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192e1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192d2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723b1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/Mp_Precomp.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8703b2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821a2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8812a2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8703b1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8188c2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821a2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtcOutSrc.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8812a1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192d2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723a2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8703b1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723a2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723a1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821a1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723b2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723b1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8812a1Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8188c2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723b2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8812a2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192e2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821aCsr2Ant.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8723a1Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8821aCsr2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/btc/HalBtc8192e2Ant.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_com.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_intf.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/hal/hal_phy.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/wifi_regd.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/custom_gpio_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/ioctl_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/xmit_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/mlme_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/ioctl_mp.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/rtw_proc.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/os_intfs.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/ioctl_cfg80211.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/rtw_cfgvendor.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/recv_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/usb_ops_linux.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/rtw_cfgvendor.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/rtw_android.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/rtw_proc.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/ioctl_cfg80211.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/linux/usb_intf.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/os_dep/osdep_service.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ARM_SUNxI_sdio.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ARM_WMT_sdio.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_arm_act_sdio.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ARM_SUNnI_sdio.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_sprd_sdio.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ops.h
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ARM_SUNxI_usb.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_RTK_DMP_usb.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58/platform/platform_ops.c
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58
Authentication requested [root] for make clean:
Password: 
su: Authentication failure
Authentication requested [root] for make driver:
Password: 
su: Authentication failure
##################################################
Compile make driver error: 1
Please check error Mesg
##################################################
```

Any ideas where I go from here?

> **Temüjin said:**
> I just added a patch in that thread you linked to. Feel free to test it. I'm guessing the OP may also need to add the USB ID in os_dep/linux/usb_intf.c file. It looks to me like only the Bluetooth version (0bda:b82c) is there.

```
#ifdef CONFIG_RTL8822B
    /*=== Realtek demoboard ===*/
    {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
    {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
    {USB_DEVICE(0x0b05, 0x184c), .driver_info = RTL8822B}, /* ASUS USB AC53 */

//Add this?     {USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},

    {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```

I trust I'm not going to try your patience ... but what thread are you referring to? and where should I paste this? If I understand correctly, I also need to paste this code into the shown file in the "os_dep" directory. Is that correct?

Sorry for any neophyte questions. I'm new to compiling drivers.

---

### Post by jeremy31 on 2017-11-29
Please post the contents of install.sh and Makefile, please use code tags

I might want to try ```
sudo install.sh
```

I looked at a driver file from Amazon comments/reviews and that file has no mention of your device.  I would add a bad review on the amazon product page and see if the seller or someone else answers.  Be sure to include that it has an ID of ID 0bda:b812 Realtek Semiconductor Corp.

---

### Post by Yellow Pasque on 2017-11-29
> what thread are you referring to? 
I am talking about thread wildmanne39 linked to: [https://ubuntuforums.org/showthread.php?t=2362577&p=13655637#post13655637](https://ubuntuforums.org/showthread.php?t=2362577&p=13655637#post13655637)

> and where should I paste this? 
Into a blank text file. Like this:
```
cd ~/
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu/
gedit whatever.patch     #Opens up blank text file. Paste, save and exit
patch -p1 < whatever.patch
make clean
make
sudo make install
```

> If I understand correctly, I also need to paste this code into the shown file in the "os_dep" directory. Is that correct?

I don't know. Realtek's naming scheme is confusing me. Your device's USB ID suggests the chipset is 8822BU, but the CD is building a driver named 8821AU. Maybe it works for both? *shrug*
[https://wikidevi.com/wiki/Realtek_RTL8812BU_USB_Module](https://wikidevi.com/wiki/Realtek_RTL8812BU_USB_Module)
[https://wikidevi.com/wiki/Realtek#ac](https://wikidevi.com/wiki/Realtek#ac)

EDIT: Just saw that jeremy is also confused with naming, so I feel less dumb.

---

### Post by wildmanne39 on 2017-11-29
Something is wrong they included the wrong disc or ubuntu is recognizing it incorrectly, not exactly sure.

---

### Post by jeremy31 on 2017-11-29
I would really like to see if the linux driver rranger2 has has the b812 listed in the os_dep/linux/usb_intf.c file and there is something else going on if the install.sh is asking for the su password

---

### Post by rranger2 on 2017-11-30
> **jeremy31 said:**
> I would really like to see if the linux driver rranger2 has has the b812 listed in the os_dep/linux/usb_intf.c file and there is something else going on if the install.sh is asking for the su password

Again, thanks for the continued help. I went a different route last night (after sending the response to you) with similarly dismal success. I was able to locate what I thought would be Debian installable drivers on Github for [this ]("https://github.com/gnab/rtl8812au")(whatever the chipset is) and for an older [Netgear A6210]("https://www.newegg.com/Product/Product.aspx?Item=9SIA2F83373778&cm_re=netgear_ac1200-_-33-122-618-_-Product") adapter that I've used on a Windows machine for a few years. I had no luck with the Realtek device and I was unsuccessful at installing the Netgear drivers. 

I'll look into this tonight when I get home (I'm in the Eastern US) and get back to you both. 

I do have one question: If the drivers originally referred to by [COLOR=#000000]wildmanne39 would work on Ubuntu 16.04, why wouldn't they also carry over to later versions - like the 17.10 version I'm running? Or, is it simply that the later Linux kernel doesn't support the earlier drivers?[/COLOR]

---

### Post by Yellow Pasque on 2017-11-30
> If the drivers originally referred to by wildmanne39 would work on Ubuntu 16.04, why wouldn't they also carry over to later versions - like the 17.10 version I'm running? 

Why don't Windows XP drivers work on Windows 7? Because the API changes. It's no different with the Linux kernel. That's what the patch takes care of.

---

### Post by rranger2 on 2017-11-30
Good point, thanks.

---

### Post by praseodym on 2017-11-30
Errr, what about the internal Ralink 5592 card?

[https://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](https://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

---

### Post by Yellow Pasque on 2017-11-30
> Errr, what about the internal Ralink 5592 card?

The OP seems focused on getting an AC1200 adapter to work. The internal adapter would probably be better than the Rosewill one, but if the Rosewill adapter works without driver wrangling, it's probably better for OP as a stopgap solution.

---

### Post by rranger2 on 2017-11-30
> **Temüjin said:**
> The OP seems focused on getting an AC1200 adapter to work. The internal adapter would probably be better than the Rosewill one, but if the Rosewill adapter works without driver wrangling, it's probably better for OP as a stopgap solution.

Sorry to have introduced the AC1200 into the discussion (is that an Ralink 5592 card? And, BTW, I get a 404 error when I try to execute the commands in that thread); the AC1200 is simply an old 5 GHZ adapter I have that I thought I might be able to get to work if the Realtek one doesn't pan out. I'm still very much interested in solving the issue with Realtek device. When you say you: "[COLOR=#000000]*would really like to see if the linux driver rranger2 has has the b812 listed in the os_dep/linux/usb_intf.c file and there is something else going on if the install.sh is asking for the su password",* what are you asking me to post?[/COLOR]

---

### Post by rranger2 on 2017-11-30
Oh, I see. The internal Ralink 5592 card doesn't work at all, which is why I'm trying to install the USB devices. I have a Rosewill USB device that does work, but it's 2.4 GHZ only.

---

### Post by jeremy31 on 2017-11-30
Netgear A6210 might work with
```
sudo apt-get install git build-essential dkms
```
```
git clone https://github.com/jurobystricky/Netgear-A6210
```
```
sudo dkms add ./Netgear-A6210
```
```
sudo dkms install netgear-a6210/2.5.0
```
Reboot

---

### Post by rranger2 on 2017-11-30
> **jeremy31 said:**
> Netgear A6210 might work with
```
sudo apt-get install git build-essential dkms
```
```
git clone https://github.com/jurobystricky/Netgear-A6210
```
```
sudo dkms add ./Netgear-A6210
```
```
sudo dkms install netgear-a6210/2.5.0
```
Reboot

Well, I did what you suggested wrt AC1200 and this is what I got when I tried to execute the git clone step:

```
fatal: destination path 'Netgear-A6210' already exists and is not an empty directory.
``` 

That must have been from an earlier attempt. Do I need to remove what's already there and, if so, how do I go about doing that? Again, you're dealing with a neophyte, so sorry for the very basic questions.

```
don@don-Inspiron-518:~$ sudo dkms install netgear-a6210/2.5.0

Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j4 KERNELRELEASE=4.13.0-17-generic.....(bad exit status: 2)
ERROR (dkms apport): binary package for netgear-a6210: 2.5.0 not found
Error! Bad return status for module build on kernel: 4.13.0-17-generic (x86_64)
Consult /var/lib/dkms/netgear-a6210/2.5.0/build/make.log for more information.

```

When I printed out the log file, this is what it said:

```
DKMS make.log for netgear-a6210-2.5.0 for kernel 4.13.0-17-generic (x86_64)
Thu Nov 30 17:35:50 EST 2017
export DBGFLAGS


*** Building driver with debug messages ***


cp -f os/linux/Makefile.6 /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/Makefile
make -C /lib/modules/4.13.0-17-generic/build DBGFLAGS=-DDBG SUBDIRS=/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-17-generic'
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/rtmp_data.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sta_cfg.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sta.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../mgmt/mgmt_vht.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../common/vht.o
In file included from ./include/linux/bitmap.h:8:0,
                 from ./include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/cpufeature.h:4,
                 from ./arch/x86/include/asm/thread_info.h:52,
                 from ./include/linux/thread_info.h:37,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from ./include/linux/preempt.h:80,
                 from ./include/linux/spinlock.h:50,
                 from ./include/linux/seqlock.h:35,
                 from ./include/linux/time.h:5,
                 from ./include/linux/stat.h:18,
                 from ./include/linux/module.h:10,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/os/rt_linux.h:14,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/rtmp_os.h:30,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/rtmp_comm.h:64,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.c:33:
In function &#8216;memcpy&#8217;,
    inlined from &#8216;rt_ioctl_iwaplist&#8217; at /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.c:549:2:
./include/linux/string.h:305:4: error: call to &#8216;__read_overflow2&#8217; declared with attribute error: detected read beyond size of object passed as 2nd parameter
    __read_overflow2();
    ^~~~~~~~~~~~~~~~~~
scripts/Makefile.build:302: recipe for target '/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Makefile:1546: recipe for target '_module_/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux' failed
make[1]: *** [_module_/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-17-generic'
Makefile:59: recipe for target 'debug' failed
make: *** [debug] Error 2

```

---

### Post by jeremy31 on 2017-11-30
So that isn't updated enough to work with the 4.13 kernel in 17.10
Any reason you want to use a short term release like 17.10 rather than the 16.04 LTS?

---

### Post by rranger2 on 2017-11-30
I like Gnome and the better tools it gives. That's all. It also seems to be markedly faster. No worries, I can return the dongle I got and look for something else. Do you have any suggestions for a quality dual-band card or USB device? I'm not picky; I'm happy to put in a new PCI card if necessary. I find the Wifi recommendation list to be a little ambiguous.

---

### Post by jeremy31 on 2017-11-30
PCI cards, I would pick a dual band Intel as Intel provides very good support in Linux

---

### Post by rranger2 on 2017-11-30
> **jeremy31 said:**
> PCI cards, I would pick a dual band Intel as Intel provides very good support in Linux

Thank you very much. I really appreciate the help.

---

### Post by Yellow Pasque on 2017-11-30
Did you even try what I suggested? Here's the patch again with the ID line added.

```
cd ~/
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu/
gedit whatever.patch     #Opens up blank text file. Paste patch contents, save and exit
patch -p1 < whatever.patch
make
sudo make install
```

```
diff -Naur -x '.*' rtl8822bu/include/osdep_service_linux.h rtl8822bu.patched/include/osdep_service_linux.h
--- rtl8822bu/include/osdep_service_linux.h	2017-11-30 18:26:31.986587900 -0500
+++ rtl8822bu.patched/include/osdep_service_linux.h	2017-11-30 18:17:20.577256289 -0500
@@ -45,7 +45,12 @@
 #include <linux/semaphore.h>
 #endif
 #include <linux/sem.h>
+
 #include <linux/sched.h>
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4, 11, 0))
+	#include <linux/sched/signal.h>
+#endif
+
 #include <linux/etherdevice.h>
 #include <linux/wireless.h>
 #include <net/iw_handler.h>
diff -Naur -x '.*' rtl8822bu/os_dep/linux/ioctl_cfg80211.c rtl8822bu.patched/os_dep/linux/ioctl_cfg80211.c
--- rtl8822bu/os_dep/linux/ioctl_cfg80211.c	2017-11-30 18:26:31.998588969 -0500
+++ rtl8822bu.patched/os_dep/linux/ioctl_cfg80211.c	2017-11-30 18:17:20.581256598 -0500
@@ -742,12 +742,30 @@
 		struct ieee80211_channel *notify_channel;
 		u32 freq;
 		u16 channel = cur_network->network.Configuration.DSConfig;
+		
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,12,0))
+		struct cfg80211_roam_info roam_info = {};
+#endif
 
 		freq = rtw_ch2freq(channel);
 		notify_channel = ieee80211_get_channel(wiphy, freq);
 #endif
 
 		RTW_INFO(FUNC_ADPT_FMT" call cfg80211_roamed\n", FUNC_ADPT_ARG(padapter));
+		
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,12,0))
+		roam_info.channel = notify_channel;
+		roam_info.bssid = cur_network->network.MacAddress;
+		roam_info.req_ie =
+			pmlmepriv->assoc_req+sizeof(struct rtw_ieee80211_hdr_3addr)+2;
+		roam_info.req_ie_len =
+			pmlmepriv->assoc_req_len-sizeof(struct rtw_ieee80211_hdr_3addr)-2;
+		roam_info.resp_ie =
+			pmlmepriv->assoc_rsp+sizeof(struct rtw_ieee80211_hdr_3addr)+6;
+		roam_info.resp_ie_len =
+			pmlmepriv->assoc_rsp_len-sizeof(struct rtw_ieee80211_hdr_3addr)-6;
+		cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
+#else		
 		cfg80211_roamed(padapter->pnetdev
 #if LINUX_VERSION_CODE > KERNEL_VERSION(2, 6, 39) || defined(COMPAT_KERNEL_RELEASE)
 		                , notify_channel
@@ -758,6 +776,7 @@
 		                , pmlmepriv->assoc_rsp + sizeof(struct rtw_ieee80211_hdr_3addr) + 6
 		                , pmlmepriv->assoc_rsp_len - sizeof(struct rtw_ieee80211_hdr_3addr) - 6
 		                , GFP_ATOMIC);
+#endif
 	} else {
 #if LINUX_VERSION_CODE < KERNEL_VERSION(3, 11, 0) || defined(COMPAT_KERNEL_RELEASE)
 		RTW_INFO("pwdev->sme_state(b)=%d\n", pwdev->sme_state);
@@ -1721,7 +1740,7 @@
 #endif
 static int cfg80211_rtw_change_iface(struct wiphy *wiphy,
                                      struct net_device *ndev,
-                                     enum nl80211_iftype type, u32 *flags,
+                                     enum nl80211_iftype type,
                                      struct vif_params *params) {
 	enum nl80211_iftype old_type;
 	NDIS_802_11_NETWORK_INFRASTRUCTURE networkType;
@@ -3595,7 +3614,13 @@
 	mon_ndev->type = ARPHRD_IEEE80211_RADIOTAP;
 	strncpy(mon_ndev->name, name, IFNAMSIZ);
 	mon_ndev->name[IFNAMSIZ - 1] = 0;
+	
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,11,9))
+	mon_ndev->needs_free_netdev = false;
+	mon_ndev->priv_destructor = rtw_ndev_destructor;
+#else
 	mon_ndev->destructor = rtw_ndev_destructor;
+#endif
 
 #if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 29))
 	mon_ndev->netdev_ops = &rtw_cfg80211_monitor_if_ops;
@@ -3661,7 +3686,7 @@
 #if (LINUX_VERSION_CODE >= KERNEL_VERSION(4, 1, 0))
     unsigned char name_assign_type,
 #endif
-    enum nl80211_iftype type, u32 *flags, struct vif_params *params) {
+    enum nl80211_iftype type, struct vif_params *params) {
 	int ret = 0;
 	struct net_device *ndev = NULL;
 	_adapter *padapter = wiphy_to_adapter(wiphy);
@@ -6094,7 +6119,13 @@
 #endif
 
 #if defined(CONFIG_PM) && (LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
-	wiphy->flags |= WIPHY_FLAG_SUPPORTS_SCHED_SCAN;
+
+#if (LINUX_VERSION_CODE < KERNEL_VERSION(4,12,0))
+ 	wiphy->flags |= WIPHY_FLAG_SUPPORTS_SCHED_SCAN;
+#else // kernel >= 4.12
+	wiphy->max_sched_scan_reqs = 1;
+#endif
+
 #ifdef CONFIG_PNO_SUPPORT
 	wiphy->max_sched_scan_ssids = MAX_PNO_LIST_COUNT;
 #endif
diff -Naur -x '.*' rtl8822bu/os_dep/linux/usb_intf.c rtl8822bu.patched/os_dep/linux/usb_intf.c
--- rtl8822bu/os_dep/linux/usb_intf.c	2017-11-30 18:26:32.006589681 -0500
+++ rtl8822bu.patched/os_dep/linux/usb_intf.c	2017-11-30 18:25:42.670143032 -0500
@@ -223,6 +223,7 @@
 	{USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
 	{USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
 	{USB_DEVICE(0x0b05, 0x184c), .driver_info = RTL8822B}, /* ASUS USB AC53 */
+	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812), .driver_info = RTL8822B},
 	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
 #endif /* CONFIG_RTL8822B */
 

```

---

### Post by rranger2 on 2017-12-01
Thank you Temujin, I have now. This is what happened when I issued the "make" command:

```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-17-generic/build M=/home/don/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-17-generic'
  CC [M]  /home/don/rtl8822bu/core/rtw_cmd.o
  CC [M]  /home/don/rtl8822bu/core/rtw_security.o
  CC [M]  /home/don/rtl8822bu/core/rtw_debug.o
  CC [M]  /home/don/rtl8822bu/core/rtw_io.o
  CC [M]  /home/don/rtl8822bu/core/rtw_ioctl_query.o
  CC [M]  /home/don/rtl8822bu/core/rtw_ioctl_set.o
  CC [M]  /home/don/rtl8822bu/core/rtw_ieee80211.o
  CC [M]  /home/don/rtl8822bu/core/rtw_mlme.o
  CC [M]  /home/don/rtl8822bu/core/rtw_mlme_ext.o
  CC [M]  /home/don/rtl8822bu/core/rtw_mi.o
  CC [M]  /home/don/rtl8822bu/core/rtw_wlan_util.o
  CC [M]  /home/don/rtl8822bu/core/rtw_vht.o
  CC [M]  /home/don/rtl8822bu/core/rtw_pwrctrl.o
  CC [M]  /home/don/rtl8822bu/core/rtw_rf.o
  CC [M]  /home/don/rtl8822bu/core/rtw_recv.o
  CC [M]  /home/don/rtl8822bu/core/rtw_sta_mgt.o
  CC [M]  /home/don/rtl8822bu/core/rtw_ap.o
  CC [M]  /home/don/rtl8822bu/core/rtw_xmit.o
  CC [M]  /home/don/rtl8822bu/core/rtw_p2p.o
  CC [M]  /home/don/rtl8822bu/core/rtw_tdls.o
  CC [M]  /home/don/rtl8822bu/core/rtw_br_ext.o
  CC [M]  /home/don/rtl8822bu/core/rtw_iol.o
  CC [M]  /home/don/rtl8822bu/core/rtw_sreset.o
  CC [M]  /home/don/rtl8822bu/core/rtw_btcoex.o
  CC [M]  /home/don/rtl8822bu/core/rtw_beamforming.o
  CC [M]  /home/don/rtl8822bu/core/rtw_odm.o
  CC [M]  /home/don/rtl8822bu/core/efuse/rtw_efuse.o
  CC [M]  /home/don/rtl8822bu/os_dep/osdep_service.o
  CC [M]  /home/don/rtl8822bu/os_dep/linux/os_intfs.o
  CC [M]  /home/don/rtl8822bu/os_dep/linux/usb_intf.o
/home/don/rtl8822bu/os_dep/linux/usb_intf.c:1616:0: error: unterminated argument list invoking macro "USB_DEVICE"
 #endif /* CONFIG_INTEL_PROXIM */
 
/home/don/rtl8822bu/os_dep/linux/usb_intf.c:226:3: error: &#8216;USB_DEVICE&#8217; undeclared here (not in a function); did you mean &#8216;ZONE_DEVICE&#8217;?
  {USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},
   ^~~~~~~~~~
   ZONE_DEVICE
/home/don/rtl8822bu/os_dep/linux/usb_intf.c:226:2: error: expected &#8216;}&#8217; at end of input
  {USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},
  ^
scripts/Makefile.build:302: recipe for target '/home/don/rtl8822bu/os_dep/linux/usb_intf.o' failed
make[2]: *** [/home/don/rtl8822bu/os_dep/linux/usb_intf.o] Error 1
Makefile:1546: recipe for target '_module_/home/don/rtl8822bu' failed
make[1]: *** [_module_/home/don/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-17-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2


```

---

### Post by Yellow Pasque on 2017-12-01
My apologies. I missed a ' ) ' after "0xB812"

```
{USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812, .driver_info = RTL8822B},
```
should be:
```
{USB_DEVICE(USB_VENDER_ID_REALTEK, 0xB812), .driver_info = RTL8822B},
```

To fix:
```
cd ~/rtl8822bu
gedit os_dep/linux/usb_intf.c
```
Scroll down to line 225 or so and add the ' ) '. Save, exit, and run make.

If that's too difficult for you, I also edited my post/patch, so you could just trash it and start over.
```
cd ~/
rm -rf rtl8822bu/
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu/
gedit whatever.patch     #Opens up blank text file. Paste patch contents, save and exit
patch -p1 < whatever.patch
make
sudo make install
```

---

### Post by rranger2 on 2017-12-01
Temujin, my friend, you are a certifiable genius! I made the incredibly small edit, re-"made" the driver, installed it, and it works like a charm with a WPA2 connection and a link speed of 867 Mb/s. Very nice indeed! Thank you all for the help and have a great set of holidays!

How do I mark this as solved, or do you do that?

---

### Post by Yellow Pasque on 2017-12-01
You're welcome. There's a 'thread tools' menu above the first post to mark your thread as solved.
(If I was a genius, I would have written the code, rather than just playing patch monkey.)

---

### Post by rranger2 on 2017-12-01
Modesty, however unnecessary, is a very valuable commodity these days :p

---

### Post by wildmanne39 on 2017-12-01
Thanks Temüjin, well done!

---

### Post by vidman on 2018-01-24
Hello, 

I have a USB wifi produced by Newterk. The linux driver they provided on the disc would error out during installation but I found that this thread solved my problem as it uses the same 0bda:b812 chipset. 

Everything was working great for the past couple of weeks. Then it just stopped working. I didn't update or install anything. Just used Libreoffice and played a bit of civ 5 and shutdown the computer. This morning, boot up and the system says there is no wifi adapter installed. 

And it is just like before: lsusb shows it's there but for whatever the reason settings reports no wifi adapter found. 

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04b8:1114 Seiko Epson Corp. 
Bus 001 Device 006: ID 04d9:fa58 Holtek Semiconductor, Inc. 
Bus 001 Device 004: ID 1038:1202 SteelSeries ApS 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 005: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```
I see you there, you naughty little 0bda:b812. 

Also, the changes to the files I made from this thread remain intact so I'm at a loss of where to look next. 

Could steam/civ5 killed it? I'd be tempted to blame it if I hadn't also been using it regularly over the last couple of weeks. 

That's always been my biggest gripe with ubuntu... how you can just turn it off and not make any changes or updates and then stuff is broken on the next boot. At least my desktop environment is still showing...

[https://paste.ubuntu.com/26451882/](https://paste.ubuntu.com/26451882/)
Edit: Well... redoing the steps here and then rebooting twice and suddenly it's working again. What has the power to undo the patch install? 

Btw, special thanks to Temüjin for getting me up and running in the first place!

---

### Post by Yellow Pasque on 2018-01-24
It's probably a kernel update that did it. You'll either need to run 'sudo make install' again when you boot into a new kernel or rig it up to do so automatically upon installation of new kernel (dkms).

> how you can just turn it off and not make any changes or updates and then stuff is broken on the next boot.

I'm still wrestling with multiple AMD machines with Windows 10 that won't apply the latest mitigation update(s) correctly, so this is not exclusively a Linux issue.

---

### Post by vidman on 2018-01-24
I get that. I am on ubuntu because a windows update completely destroyed my machine. But the difference is... at least it was an update that I could blame. I've never experienced iOS or windows just randomly not work after a single reboot that didn't have an update or something I did wrong to blame. It's never just broke after minor normal use. That is something I can attribute to ubuntu. I've been using it off and on since 8.10. Through out the life I can remember the majority of issues happened not during an update or new package installation. Weird problems like shutting down but the next day grub is borked, or the desktop is missing, or the network suddenly disappears. The difference is, with windows, it's anybody's guess on how to fix an issue when I've never been able to NOT figure out how to fix a Linux issue (barring massive user mistakes with xorg back in the day). 

 But back on topic. How do I figure out what is undoing the patching of these drivers so that I don't have to go through the patching process over again? I didn't update the kernel personally.  Is that an automated function now?

---

### Post by jeremy31 on 2018-01-24
You could try my patched dkms version, using a dkms.conf I made with Temujin's patch from above
```
cd Desktop
sudo apt install dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```
I can understand why you would have to compile again after a  kernel update but not sure why you would have to apply the patch again unless you deleted the directory and did the git clone command again

---

### Post by chili555 on 2018-01-24
> You'll either need to run 'sudo make install' again It should be:```
cd rtl8822bu/
make clean
make
sudo make install
```The install procedure compiles and installs the driver for the currently running kernel version only. When Update Manager offers a newer kernel version, also known as linux-image, after the requested reboot, you must recompile. 

If, after an update, the system asks for a reboot, you can bet that the wireless will not work. Recompile.

---

### Post by vidman on 2018-01-24
Thanks everyone!  On to the real problem that I think that caused the debacle.  I'm turning off autoupdates but after a reboot the boxes are rechecked.   So I think a kernel update is what did it.   That problem will have to be a different thread.  For now, I'll just be prepared to recompile as necessary.  Thanks for the help everyone.

---

### Post by jeremy31 on 2018-01-25
Or you could copy my dkms.conf to your directory and add it as dkms, so it compiles automatically when the kernel is updated
```
cd rtl8822bu
wget https://raw.githubusercontent.com/jeremyb31/rtl8822bu/master/dkms.conf
cd ~
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```

---

### Post by Yellow Pasque on 2018-01-25
> I'm turning off autoupdates but after a reboot the boxes are rechecked.

The best solution is jeremy31's (dkms). unattended-upgrades package may be causing that behavior. If you're not good about regularly updating your system, I would recommend you leave it installed though.

> **chili555 said:**
> It should be:```
cd rtl8822bu/
make clean
```

Good catch on make clean. Thanks.

---

### Post by jerome1232 on 2018-02-01
I also got this adapter and was about to leave a scathing review on amazon about how it's advertised to work with Linux Kernel 4.1x yet here I am, having to follow a forum because the included driver doesn't want to compile when I noticed a link to an updated driver on the amazon page.

Well it (their updated driver) won't compile on 4.13 either, so I guess I'm back to leaving a scathing review. Thanks for guide to get this working.   *internal grumbles about drivers*

---

### Post by Yellow Pasque on 2018-02-01
^I'd bet money they meant 2.6.x - 4.1.x

---

### Post by R%&amp;92GH&amp; on 2018-04-30
Sorry to resurrect this thread, but I have exactly the same device, and I've been unable to make it work on Ubuntu 18.04. First of all because the computer does not have network access (so I can't use git or wget), but even if download the packages from another computer and save them in a usb stick, I get several errors when compiling them.

Are there any pre-compiled binaries for 64bit machines?

---

### Post by jasoncanon on 2018-05-09
> **marcpalaus said:**
> Sorry to resurrect this thread, but I have exactly the same device, and I've been unable to make it work on Ubuntu 18.04. First of all because the computer does not have network access (so I can't use git or wget), but even if download the packages from another computer and save them in a usb stick, I get several errors when compiling them.

Are there any pre-compiled binaries for 64bit machines?

I'm in the same boat. A good chance for me to learn how to compile my first driver. Thanks for all the help in this thread already.

-Jason

---

### Post by famewolf on 2018-06-15
> **jeremy31 said:**
> You could try my patched dkms version, using a dkms.conf I made with Temujin's patch from above
```
cd Desktop
sudo apt install dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```
I can understand why you would have to compile again after a  kernel update but not sure why you would have to apply the patch again unless you deleted the directory and did the git clone command again


Thank you VERY MUCH for this information (and thanks to the others who provided parts of it to get to this point).   I was able to use this to successfully get a wifi dongle working on a ubuntu variant.  It should work on just about any distro.  If you try this on a usb 2.0 port I wouldn't expect much more than the AC600 of previous models.

---

### Post by famewolf on 2018-06-17
> **jeremy31 said:**
> You could try my patched dkms version, using a dkms.conf I made with Temujin's patch from above
```
cd Desktop
sudo apt install dkms
git clone https://github.com/jeremyb31/rtl8822bu.git
sudo dkms add ./rtl8822bu
sudo dkms install 8822bu/1.1
```
I can understand why you would have to compile again after a  kernel update but not sure why you would have to apply the patch again unless you deleted the directory and did the git clone command again


I tried this on a Manjaro linux laptop and all I get is a message in dmesg which says "[  593.868203] 8822bu: Unknown symbol __vfs_read (err 0)"

The 8812AU driver also apparently had this issue and it's discussed here:  [https://github.com/zebulon2/rtl8812au-driver-5.2.9/issues/2](https://github.com/zebulon2/rtl8812au-driver-5.2.9/issues/2)

It was fixed with this patch:  [https://github.com/zebulon2/rtl8812au-driver-5.2.9/commit/08e0472fbc60be09f6207b21819ed141cb81d579](https://github.com/zebulon2/rtl8812au-driver-5.2.9/commit/08e0472fbc60be09f6207b21819ed141cb81d579)

Does this provide enough info to get it working on the 8812BU driver?

---

### Post by jeremy31 on 2018-06-17
Try [https://github.com/MeissnerEffect/rtl8822bu](https://github.com/MeissnerEffect/rtl8822bu)

---

### Post by famewolf on 2018-06-17
> **jeremy31 said:**
> Try [https://github.com/MeissnerEffect/rtl8822bu](https://github.com/MeissnerEffect/rtl8822bu)



Thank you!  That one worked perfectly.  Now I just need to figure out how to undo the earlier dkms lines I ran so I can redo with new.   I did a manual install for now.


*update* thought I had it but didn't...kept giving me build errors on the add.  Finally just gave up and can do manual install.


Although the make and the make install work just fine attempting to do the dkms install results in:

[FONT=monospace][COLOR=#54FF54]**[famewolf@PC**[/COLOR][COLOR=#FFFFFF]** work2**[/COLOR][COLOR=#54FF54]**]$**[/COLOR][COLOR=#000000] sudo dkms install 8822bu/1.1[/COLOR]

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' all KVER=4.14.48-2-MANJARO..........................................................................................................
Error!  Build of 8822bu.ko failed for: 4.14.48-2-MANJARO (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/8822bu/1.1/build/ for more information.


The make.log is attached but looks the same as the manual "make" with no additional error's...it appears to complete but the secondary part doesn't occur.

[/FONT]

---

