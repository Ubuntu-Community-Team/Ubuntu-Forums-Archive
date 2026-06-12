---
title: "ASUS X550L Atheros Bluetooth scanning fails after 20sec"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by doylefermi on 2014-10-31
I dont know if am posting in the right place... But please do help me

I have an ASUS X550L pc running Ubuntu 14.04

[FONT=arial]The bluetooth doesnt work and stops scanning after about 20secs with no devices found. And the device is not found too even though its set to discoverable.

_**OUTPUT:-**_[/FONT]
[LIST]
[*][FONT=lucida console]lsusb[/FONT]
[/LIST]
[FONT=lucida console]Bus 001 Device 002: ID 8087:8000 Intel Corp. [/FONT]
[FONT=lucida console]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=lucida console]Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=lucida console]Bus 002 Device 004: ID 13d3:3408 IMC Networks [/FONT]
[FONT=lucida console]Bus 002 Device 002: ID 04f2:b40a Chicony Electronics Co., Ltd [/FONT]
[FONT=lucida console]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[FONT=arial][U]IMC Networks is the bluetooth device. The bluetooth works fine in windows 7. However i am using only linux at present.
[FONT=lucida console]
[/FONT][/U][/FONT][/FONT]
[LIST]
[*][FONT=lucida console]rfkill list[/FONT]
[/LIST]
[FONT=lucida console]1: phy0: Wireless LAN[/FONT]
[FONT=lucida console]    Soft blocked: no[/FONT]
[FONT=lucida console]    Hard blocked: no[/FONT]
[FONT=lucida console]2: asus-wlan: Wireless LAN[/FONT]
[FONT=lucida console]    Soft blocked: no[/FONT]
[FONT=lucida console]    Hard blocked: no[/FONT]
[FONT=lucida console]3: asus-bluetooth: Bluetooth[/FONT]
[FONT=lucida console]    Soft blocked: no[/FONT]
[FONT=lucida console]    Hard blocked: no[/FONT]
[FONT=lucida console]4: hci0: Bluetooth[/FONT]
[FONT=lucida console]    Soft blocked: no[/FONT]
[FONT=lucida console]    Hard blocked: no

[/FONT]
[LIST]
[*][FONT=lucida console]hciconfig[/FONT]
[/LIST]
[FONT=lucida console]hci0:    Type: BR/EDR  Bus: USB[/FONT]
[FONT=lucida console]    BD Address: 54:27:1E:58:4A:36  ACL MTU: 1022:8  SCO MTU: 183:5[/FONT]
[FONT=lucida console]    UP RUNNING PSCAN ISCAN [/FONT]
[FONT=lucida console]    RX bytes:732 acl:0 sco:0 events:59 errors:0[/FONT]
[FONT=lucida console]    TX bytes:1071 acl:0 sco:0 commands:55 errors:0

[/FONT]
[LIST]
[*][FONT=lucida console]sudo hcitool dev[/FONT]
[/LIST]
[FONT=lucida console]Devices:[/FONT]
[FONT=lucida console]    hci0    54:27:1E:58:4A:36[/FONT]
[FONT=lucida console]
[/FONT]

[LIST]
[*][FONT=lucida console]sudo hcitool scan[/FONT]
[/LIST]
[FONT=lucida console]Scanning ...

[/FONT]
[LIST]
[*][FONT=lucida console] hciconfig --all[/FONT]
[/LIST]
[FONT=lucida console]hci0:    Type: BR/EDR  Bus: USB[/FONT]
[FONT=lucida console]    BD Address: 54:27:1E:58:4A:36  ACL MTU: 1022:8  SCO MTU: 183:5[/FONT]
[FONT=lucida console]    UP RUNNING PSCAN ISCAN [/FONT]
[FONT=lucida console]    RX bytes:741 acl:0 sco:0 events:61 errors:0[/FONT]
[FONT=lucida console]    TX bytes:1079 acl:0 sco:0 commands:56 errors:0[/FONT]
[FONT=lucida console]    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x8f[/FONT]
[FONT=lucida console]    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 [/FONT]
[FONT=lucida console]    Link policy: RSWITCH HOLD SNIFF [/FONT]
[FONT=lucida console]    Link mode: SLAVE ACCEPT [/FONT]
[FONT=lucida console]    Name: 'mint-0'[/FONT]
[FONT=lucida console]    Class: 0x6c0100[/FONT]
[FONT=lucida console]    Service Classes: Rendering, Capturing, Audio, Telephony[/FONT]
[FONT=lucida console]    Device Class: Computer, Uncategorized[/FONT]
[FONT=lucida console]    HCI Version:  (0x7)  Revision: 0x3101[/FONT]
[FONT=lucida console]    LMP Version:  (0x7)  Subversion: 0x1[/FONT]
[FONT=lucida console]    Manufacturer: Atheros Communications, Inc. (69)[/FONT]







Please do help me. Am ready to send any other output necessary. Thanking you for helping me.



[FONT=lucida console][FONT=arial]

[/FONT][/FONT]

---

### Post by praseodym on 2014-11-01
Please show:
```

usb-devices
lsmod
```

```
modprobe -c | grep -i "13d3.*3408"
```
does not give an output here, so obviously there is no driver available. Maybe its connected to the WLAN device somehow?!

```
lspci -nnk
```
please.

---

### Post by doylefermi on 2014-11-01
[LIST]
[*][SIZE=4]_**usb-devices**_[/SIZE]
[/LIST]


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0538 Rev=01.00
S:  Product= USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b40a Rev=69.64
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=USB2.0 HD UVC WebCam
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3408 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


[LIST]
[*]_**[SIZE=4]lsmod[/SIZE]**_
[/LIST]
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
btusb                  32412  0 
arc4                   12608  2 
bluetooth             395423  22 bnep,btusb,rfcomm
dm_multipath           22873  0 
scsi_dh                14882  1 dm_multipath
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
serio_raw              13462  0 
mac80211              626489  1 ath9k
snd_hda_intel          52355  5 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
lpc_ich                21080  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
cfg80211              484040  3 ath,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82274  1 mei_me
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
rtsx_pci_sdmmc         23274  0 
nouveau              1097199  1 
i915                  783485  6 
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
psmouse               102222  0 
ahci                   25819  4 
i2c_algo_bit           13413  2 i915,nouveau
libahci                32168  1 ahci
drm_kms_helper         52758  2 i915,nouveau
drm                   302817  8 ttm,i915,drm_kms_helper,nouveau
r8169                  67581  0 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
video                  19476  3 i915,nouveau,asus_wmi




[LIST]
[*][SIZE=4]_**modprobe -c | grep -i "13d3.*3408"**_[/SIZE]
[/LIST]
Like you told, no output :) . Yeah and its connected to wifi :P


[LIST]
[*]_**[SIZE=4]lspci -nnk[/SIZE]**_
[/LIST]
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:228a]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Kernel driver in use: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:11af]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
00:1f.6 Signal processing controller [1180]: Intel Corporation Lynx Point-LP Thermal [8086:9c24] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:202f]
    Kernel driver in use: rtsx_pci
02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: AzureWave Device [1a3b:2130]
    Kernel driver in use: ath9k
04:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
    Kernel driver in use: nouveau



Thanks for helping me out. Hope you can solve it . Thank you.

---

### Post by praseodym on 2014-11-01
The module "btusb" is loaded but maybe something is missing?!
```

dmesg | egrep 'bt|[B]lue|[F]irm'
```

---

### Post by jeremy31 on 2014-11-01
> **praseodym said:**
> The module "btusb" is loaded but maybe something is missing?!
```

dmesg | egrep 'bt|[B]lue|[F]irm'
```

A few generic entries in the btusb aliases
```
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*

```

---

### Post by doylefermi on 2014-11-01
```

[LIST]
[*][SIZE=4]_sudo dmesg | egrep 'bt|[B]lue|[F]irm'_[/SIZE]
[/LIST]

```

[    0.185460] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    3.286075] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   16.333209] Bluetooth: Core ver 2.17
[   16.333232] Bluetooth: HCI device and connection manager initialized
[   16.333240] Bluetooth: HCI socket layer initialized
[   16.333243] Bluetooth: L2CAP socket layer initialized
[   16.333247] Bluetooth: SCO socket layer initialized
[   16.335592] usbcore: registered new interface driver btusb
[   20.219886] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.219890] Bluetooth: BNEP filters: protocol multicast
[   20.219899] Bluetooth: BNEP socket layer initialized
[   20.221834] Bluetooth: RFCOMM TTY layer initialized
[   20.221845] Bluetooth: RFCOMM socket layer initialized
[   20.221849] Bluetooth: RFCOMM ver 1.11


Okay, so what should be done now?

---

### Post by jeremy31 on 2014-11-02
[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)
File a bug report as we might be able to patch the ath3k.c and btusb.c to include your device but it still might not work due to a bug with ath3k and xhci(USB)

Here are the changes I think would need to be make before compiling the patched modules in ath3k.c you need to add ```
{ USB_DEVICE(0x13d3, 0x3408) },
```
below ```
/* Atheros AR3012 with sflash firmware*/
```
So it looks somewhat like
```
	/* Atheros AR3012 with sflash firmware*/
	{ USB_DEVICE(0x0CF3, 0x0036) },
	{ USB_DEVICE(0x0CF3, 0x3004) },
	{ USB_DEVICE(0x0CF3, 0x3008) },
	{ USB_DEVICE(0x0CF3, 0x311D) },
	{ USB_DEVICE(0x0CF3, 0x817a) },
	{ USB_DEVICE(0x13d3, 0x3375) },
	{ USB_DEVICE(0x04CA, 0x3004) },
	{ USB_DEVICE(0x04CA, 0x3005) },
	{ USB_DEVICE(0x04CA, 0x3006) },
	{ USB_DEVICE(0x04CA, 0x3008) },
	{ USB_DEVICE(0x04CA, 0x300b) },
	{ USB_DEVICE(0x13d3, 0x3362) },
	{ USB_DEVICE(0x0CF3, 0xE004) },
	{ USB_DEVICE(0x0CF3, 0xE005) },
	{ USB_DEVICE(0x0930, 0x0219) },
	{ USB_DEVICE(0x0930, 0x0220) },
	{ USB_DEVICE(0x0489, 0xe057) },
	{ USB_DEVICE(0x13d3, 0x3393) },
	{ USB_DEVICE(0x0489, 0xe04e) },
	{ USB_DEVICE(0x0489, 0xe056) },
	{ USB_DEVICE(0x0489, 0xe04d) },
	{ USB_DEVICE(0x04c5, 0x1330) },
	{ USB_DEVICE(0x13d3, 0x3402) },
	{ USB_DEVICE(0x0cf3, 0x3121) },
	{ USB_DEVICE(0x0cf3, 0xe003) },
	{ USB_DEVICE(0x0489, 0xe05f) },
	{ USB_DEVICE(0x13d3, 0x3408) },

```




```
{ USB_DEVICE(0x13d3, 0x3408). .driver_info = BTUSB_ATH3012 },
``` below ```
static const struct usb_device_id ath3k_blist_tbl[] = {


	/* Atheros AR3012 with sflash firmware*/
```


Make sure the spacing and punctuation is the same and save and then to add to btusb.c where you add
```
{ USB_DEVICE(0x13d3, 0x3408), .driver_info = BTUSB_ATH3012 },
``` below this ```
/* Atheros 3012 with sflash firmware */
	{ USB_DEVICE(0x0cf3, 0x0036), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0x3004), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0x3008), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0x311d), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0x817a), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x13d3, 0x3375), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04ca, 0x3004), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04ca, 0x3005), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04ca, 0x3006), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04ca, 0x3008), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04ca, 0x300b), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x13d3, 0x3362), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0xe004), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0xe005), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0930, 0x0219), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0930, 0x0220), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0489, 0xe057), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x13d3, 0x3393), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0489, 0xe04e), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0489, 0xe056), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0489, 0xe04d), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x04c5, 0x1330), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x13d3, 0x3402), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0x3121), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0cf3, 0xe003), .driver_info = BTUSB_ATH3012 },
	{ USB_DEVICE(0x0489, 0xe05f), .driver_info = BTUSB_ATH3012 },
``` This will be approximately line 168, again check spacing and save

---

### Post by doylefermi on 2014-11-02
Thank you, but is there something else that can be done to fix it. Like you making a new patch and compiling. Since you have understood this issue well, and the code you have given me, Can it be put to use?Please do help me

---

### Post by praseodym on 2014-11-02
Please try this one liner first, it adds the device ID to the driver ath3k:
```

echo 'install ath3k modprobe --ignore-install ath3k ; /bin/echo "13d3 3408" > [COLOR="#FF0000"]/sys/bus/usb/drivers/ath3k[/COLOR]/new_id' | sudo tee /etc/modprobe.d/ath3k.conf
```
Please check the right path in red first. Now load the driver:
```

sudo modprobe -rfv btusb
sudo modprobe -v ath3k
dmesg | egrep 'ath3k|[B]lue'
```

---

### Post by doylefermi on 2014-11-02
Sorry, but I didnt get you.

I did the following:-
```
echo 'install ath3k modprobe --ignore-install ath3k ; /bin/echo "13d3 3408" > /sys/bus/usb/drivers/ath3k/new_id' | sudo tee /etc/modprobe.d/ath3k.conf
```
_OUTPUT:- _
install ath3k modprobe --ignore-install ath3k ; /bin/echo "13d3 3408" > /sys/bus/usb/drivers/ath3k/new_id

```
sudo modprobe -rfv btusb

```
```
sudo modprobe -v ath3k

```
```
dmesg | egrep 'ath3k|[B]lue'

```
_OUTPUT:-_
[   17.191776] Bluetooth: Core ver 2.17
[   17.191827] Bluetooth: HCI device and connection manager initialized
[   17.191837] Bluetooth: HCI socket layer initialized
[   17.191840] Bluetooth: L2CAP socket layer initialized
[   17.191846] Bluetooth: SCO socket layer initialized
[   20.745960] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.745964] Bluetooth: BNEP filters: protocol multicast
[   20.745971] Bluetooth: BNEP socket layer initialized
[   20.747976] Bluetooth: RFCOMM TTY layer initialized
[   20.747986] Bluetooth: RFCOMM socket layer initialized
[   20.747991] Bluetooth: RFCOMM ver 1.11
[12957.728867] Bluetooth: hci0 urb ffff8800b69440c0 failed to resubmit (2)
[12964.366310] usbcore: registered new interface driver ath3k
[12967.447020] Bluetooth: Error in firmware loading err = -110,len = 0, size = 4096
[12967.447078] ath3k: probe of 2-6:1.0 failed with error -110

---

### Post by jeremy31 on 2014-11-02
Any results from ```
ls /lib/firmware/ar3k
```
My laptop with Atheros BT has 14 files in that location

---

### Post by praseodym on 2014-11-02
```
[12967.447020] Bluetooth: Error in firmware loading err = -110,len = 0, size = 4096
[12967.447078] ath3k: probe of 2-6:1.0 failed with error -110 
```
Did you install the file "linux-firmware"? Normally, its default, but maybe it just doesn't work yet with this device.

---

### Post by doylefermi on 2014-11-02
```
ls /lib/firmware/ar3k
```

_**OUTPUT:-**_

AthrBT_0x01020001.dfu 
   ramps_0x01020200_26.dfu
AthrBT_0x01020200.dfu 
   ramps_0x01020200_40.dfu
AthrBT_0x01020201.dfu 
   ramps_0x01020201_26.dfu
AthrBT_0x11020000.dfu 
   ramps_0x01020201_40.dfu
AthrBT_0x31010000.dfu 
   ramps_0x11020000_40.dfu
AthrBT_0x41020000.dfu 
   ramps_0x31010000_40.dfu
ramps_0x01020001_26.dfu 
ramps_0x41020000_40.dfu

Me too. 14 files.

---

### Post by doylefermi on 2014-11-02
```
sudo apt-get install linux-firmware

```

_**OUTPUT:-**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I guess its already installed.

Btw I dont have ath3k directory
```
ls /sys/bus/usb/drivers

```
[U][B]OUTPUT:-
[/B][/U]btusb  hub  usb  usbfs  usbhid  usb-storage  uvcvideo

---

### Post by praseodym on 2014-11-02
Hm, try:
```

sudo mkdir -p /sys/bus/usb/drivers/ath3k
```and reboot.

---

### Post by doylefermi on 2014-11-02
```
 sudo mkdir -p /sys/bus/usb/drivers/ath3k

```

[sudo] password for haxorware: 
mkdir: cannot create directory ‘/sys/bus/usb/drivers/ath3k’: No such file or directory

What now?

---

### Post by jeremy31 on 2014-11-02
Any result from this ```
dmesg | grep SerialNumber
```
And post the result of this ```
 dmesg | grep usb
```

---

### Post by doylefermi on 2014-11-02
```
dmesg | grep SerialNumber

```[    1.446297] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.446303] usb usb1: SerialNumber: 0000:00:1d.0
[    1.449786] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.449792] usb usb2: SerialNumber: 0000:00:14.0
[    1.453420] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.453426] usb usb3: SerialNumber: 0000:00:14.0
[    1.890032] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.106915] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.106919] usb 2-5: SerialNumber: 0x0001
[    2.290924] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.457072] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0

```
dmesg | grep usb

```[    0.414406] usbcore: registered new interface driver usbfs
[    0.414416] usbcore: registered new interface driver hub
[    0.414454] usbcore: registered new device driver usb
[    1.446294] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.446297] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.446299] usb usb1: Product: EHCI Host Controller
[    1.446301] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.446303] usb usb1: SerialNumber: 0000:00:1d.0
[    1.449783] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.449786] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.449788] usb usb2: Product: xHCI Host Controller
[    1.449790] usb usb2: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.449792] usb usb2: SerialNumber: 0000:00:14.0
[    1.453418] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.453420] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.453422] usb usb3: Product: xHCI Host Controller
[    1.453424] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.453426] usb usb3: SerialNumber: 0000:00:14.0
[    1.757820] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.890030] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.890032] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.057661] usb 2-5: new high-speed USB device number 2 using xhci_hcd
[    2.106913] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a
[    2.106915] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.106917] usb 2-5: Product: USB2.0 HD UVC WebCam
[    2.106918] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.106919] usb 2-5: SerialNumber: 0x0001
[    2.273500] usb 2-6: new full-speed USB device number 3 using xhci_hcd
[    2.290922] usb 2-6: New USB device found, idVendor=13d3, idProduct=3408
[    2.290924] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.361474] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    2.457070] usb 1-1.3: New USB device found, idVendor=0000, idProduct=0538
[    2.457072] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.457073] usb 1-1.3: Product:  USB OPTICAL MOUSE
[    2.464157] usbcore: registered new interface driver usbhid
[    2.464158] usbhid: USB HID core driver
[    2.465858] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12
[    2.465960] hid-generic 0003:0000:0538.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.3/input0
[   13.970370] usbcore: registered new interface driver btusb
[   15.116137] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input21
[   15.116243] usbcore: registered new interface driver uvcvideo

---

### Post by jeremy31 on 2014-11-03
I sent an email to the kernel developers in charge of this asking for this to be supported, we will see what happens

---

### Post by doylefermi on 2014-11-05
Thank you so much. Incase someone needs it:-

_**sudo cat /sys/kernel/debug/usb/devices**_

```

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev= 3.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 9
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.13
S:  Manufacturer=Linux 3.13.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms


T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b40a Rev=69.64
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=USB2.0 HD UVC WebCam
S:  SerialNumber=0x0001
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=0e(video) Sub=03 Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 512 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1024 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1536 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2048 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2688 Ivl=125us
I:  If#= 1 Alt= 7 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3072 Ivl=125us


T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=12   MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3408 Rev= 0.01
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
A:  FirstIf#= 0 IfCount= 2 Cls=e0(wlcon) Sub=01 Prot=01
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 2
B:  Alloc=  0/800 us ( 0%), #Int=  2, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.13
S:  Manufacturer=Linux 3.13.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480  MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev= 0.04
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=1.5  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0538 Rev= 1.00
S:  Product= USB OPTICAL MOUSE
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms

```

[U][B]sudo lspci -vnn

[/B][/U]```

00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>


00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:228a]
    Flags: bus master, fast devsel, latency 0, IRQ 65
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, fast devsel, latency 0, IRQ 68
    Memory at f7a1c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel


00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:0a03] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7a10000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>


00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Flags: bus master, medium devsel, latency 0, IRQ 60
    Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, fast devsel, latency 0, IRQ 66
    Memory at f7a25000 (64-bit, non-prefetchable) [size=32]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me


00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:11af]
    Flags: bus master, fast devsel, latency 0, IRQ 67
    Memory at f7a18000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport


00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7900000-f79fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport


00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7800000-f78fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport


00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport


00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:201f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7a23000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 63
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a22000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci


00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: medium devsel, IRQ 3
    Memory at f7a21000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]


00:1f.6 Signal processing controller [1180]: Intel Corporation Lynx Point-LP Thermal [8086:9c24] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:131d]
    Flags: bus master, fast devsel, latency 0, IRQ 3
    Memory at f7a20000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-


02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:202f]
    Flags: bus master, fast devsel, latency 0, IRQ 61
    Memory at f7915000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at f7900000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable- Count=1 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: rtsx_pci


02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Flags: bus master, fast devsel, latency 0, IRQ 62
    I/O ports at e000 [size=256]
    Memory at f7914000 (64-bit, non-prefetchable) [size=4K]
    Memory at f7910000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [160] Device Serial Number 23-86-28-12-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: AzureWave Device [1a3b:2130]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f7800000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at f7880000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k


04:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau

```

---

### Post by doylefermi on 2014-11-08
This problem has been solved by JeremyB. Thanks for your effort.

Refer: [http://forums.linuxmint.com/viewtopic.php?f=53&t=181629&p=942407#p942407](http://forums.linuxmint.com/viewtopic.php?f=53&t=181629&p=942407#p942407)

> [FONT=arial][COLOR=#333333]Can you use Mint Update Manager to update your kernel to 3.13.0-39? Just open update manager, refresh, then Click on View, then Linux Kernels, make the window bigger so you can see the install button[/COLOR]

[COLOR=#333333]Once it is finished, reboot Verify it is 3.13.0-39 with
[/COLOR]```
uname -a
```
```
sudo modprobe -r ath3k
```
[COLOR=#333333]
Then we rename existing ath3k module
[/COLOR]```
sudo mv /lib/modules/3.13.0-39-generic/kernel/drivers/bluetooth/ath3k.ko /lib/modules/3.13.0-39-generic/kernel/drivers/bluetooth/ath3k.ko.bak
```
[COLOR=#333333]
Download this file to your home directory [/COLOR][https://www.dropbox.com/s/njh9tl8l4kvci1u/ath3k.ko?dl=0](https://www.dropbox.com/s/njh9tl8l4kvci1u/ath3k.ko?dl=0)
[COLOR=#333333]
Then
[/COLOR]```
sudo cp ath3k.ko  /lib/modules/3.13.0-39-generic/kernel/drivers/bluetooth/
```
```
sudo modprobe -r btusb
```

```
sudo modprobe ath3k
```
[COLOR=#333333]

Then test to see if it works[/COLOR]
```
hcitool scan
```[/FONT]

---

### Post by jeremy31 on 2014-11-09
Too bad it will only work for the current 3.13.0-39 kernel until I figure out how to do a dkms install.  I figure the -40 kernel will be available soon. The ath9k devs are still working on a patch that they said they would send me and I would suspect it will get submitted to be included in newer kernels

---

### Post by Pilot6 on 2014-11-16
Where did you get this code? If you give me source, I will make a dkms package.

---

### Post by jeremy31 on 2014-11-17
> **Pilot6 said:**
> Where did you get this code? If you give me source, I will make a dkms package.

Here is a link to the patch file I did
[https://www.dropbox.com/s/3oakj695ixwolmk/ath3k.patch?dl=0](https://www.dropbox.com/s/3oakj695ixwolmk/ath3k.patch?dl=0)

---

### Post by Pilot6 on 2014-11-17
I applied this patch, but it seems that btusb needs to be patched too.

---

### Post by jeremy31 on 2014-11-17
> **Pilot6 said:**
> I applied this patch, but it seems that btusb needs to be patched too.

```
{ USB_DEVICE(0x13d3, 0x3408), .driver_info = BTUSB_ATH3012 },
```
needs to be added at about line 168

---

### Post by Pilot6 on 2014-11-17
I did that 10 minutes ago. Now I compile the kernel to test it. But if I blacklisted btusb, bluetooth worked.
Either way I make a custom kernel for ASUS laptops, since Focaltech touchpads are not supported yet.
First I apply this patch to that kernel, which is available for download. It is 3.16, which is used in 
Ubuntu 14.10 and soon will be optional for Ubuntu 14.04 and default in 14.04.2.

Then if I have time, I will make a dkms package. It will take some effort, since there are no ready code as a module.
But it will not be too hard.

---

### Post by Pilot6 on 2014-11-17
It does not work that way for some reason. I will look at it some time later. But it worked once.

---

### Post by Pilot6 on 2014-11-17
You know what is so funny? I unistalled that kernel with applied patch and now bt works perfectly.
Ths means that only id must be entered.

---

### Post by Pilot6 on 2014-11-17
Also notable is that it works without aht3k module. Only btusb.

---

### Post by jeremy31 on 2014-11-17
> **Pilot6 said:**
> Also notable is that it works without aht3k module. Only btusb.

But does it find any BT devices while scanning?  btusb might have been enough for it to work if there was another way to load the firmware

---

### Post by Pilot6 on 2014-11-17
It does find devices, pair with them and transfer data with no problem.

---

### Post by Pilot6 on 2014-11-17
I think

echo [COLOR=#000000][FONT=Ubuntu Mono]13d3 [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]3408 | sudo tee [/FONT][/COLOR][COLOR=#000000]/sys/bus/usb/drivers/btusb/new_id

can solve the issue. Maybe blacklisting if ath3k is needed. This device has IMC bluetooth, but not native Atheros.[/COLOR]

---

### Post by Pilot6 on 2014-11-17
I booted into 3.13.0-39 bt did not work there. Now booted back to 3.16 and it does not work here again. Mystery.

---

### Post by jeremy31 on 2014-11-17
> **Pilot6 said:**
> I booted into 3.13.0-39 bt did not work there. Now booted back to 3.16 and it does not work here again. Mystery.

Even on my laptop it doesn't work 100% because of what I think is an xhci problem.  I won't know for certain until I do a kernel with xhci as a module

---

### Post by Pilot6 on 2014-11-17
Now booted in 3.16 + patch -works,
Then in 3.16 without patch - works
Then in generic 3.13.0-39 works

I am trying to get the whole point of this. Now I use bt on generic kernel without any patches.

You can turn of xhci in uefi setup. It does not make any difference.

---

### Post by Pilot6 on 2014-11-17
I found the idea. You need to turn off the laptop, not restart after you install a kernel or a standalone driver. If bt chip is not powered off, the settings are kept and it works.

So here is the kernel image with both touchpad and bt patches.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

I use

options asus_nb_wmi wapf=4

for led working and no conflict with bt.

It seems to work.

And this is patched 3.16.0-25 Ubuntu kernel with all canonical patches.

---

### Post by jeremy31 on 2014-11-17
If it doesn't get powered down after ath3k loads the firmware you should be able to do almost anything other than unload both btusb and ath3k and expect it to work

I looked in my EUFI settings and haven't found the ability to disable xhci

I see a patch got submitted to lkml.org

---

### Post by Pilot6 on 2014-11-18
This is not the right patch. 13d3:3408 is an AR3011 device. So btusb must be blacklisted according to this.
[http://wireless.kernel.org/en/users/Drivers/ath3k](http://wireless.kernel.org/en/users/Drivers/ath3k)

```
diff --git a/drivers/bluetooth/ath3k.c b/drivers/bluetooth/ath3k.cindex d85ced2..ea14246 100644
--- a/drivers/bluetooth/ath3k.c
+++ b/drivers/bluetooth/ath3k.c
@@ -68,6 +68,7 @@ static const struct usb_device_id ath3k_table[] = {
 	{ USB_DEVICE(0x0930, 0x0215) },
 	{ USB_DEVICE(0x0CF3, 0x3002) },
 	{ USB_DEVICE(0x0CF3, 0xE019) },
+	{ USB_DEVICE(0x13d3, 0x3408) },
 	{ USB_DEVICE(0x13d3, 0x3304) },
 
 	/* Atheros AR9285 Malbec with sflash firmware */
diff --git a/drivers/bluetooth/btusb.c b/drivers/bluetooth/btusb.c
index edfc17b..3f935b1 100644
--- a/drivers/bluetooth/btusb.c
+++ b/drivers/bluetooth/btusb.c
@@ -145,6 +145,7 @@ static const struct usb_device_id blacklist_table[] = {
 	{ USB_DEVICE(0x0930, 0x0215), .driver_info = BTUSB_IGNORE },
 	{ USB_DEVICE(0x0cf3, 0x3002), .driver_info = BTUSB_IGNORE },
 	{ USB_DEVICE(0x0cf3, 0xe019), .driver_info = BTUSB_IGNORE },
+	{ USB_DEVICE(0x13d3, 0x3408), .driver_info = BTUSB_IGNORE },
 	{ USB_DEVICE(0x13d3, 0x3304), .driver_info = BTUSB_IGNORE },
 
 	/* Atheros AR9285 Malbec with sflash firmware */
```

---

### Post by jeremy31 on 2014-11-18
> **Pilot6 said:**
> This is not the right patch. 13d3:3408 is an AR3011 device. So btusb must be blacklisted according to this.
[http://wireless.kernel.org/en/users/Drivers/ath3k](http://wireless.kernel.org/en/users/Drivers/ath3k)

```
diff --git a/drivers/bluetooth/ath3k.c b/drivers/bluetooth/ath3k.cindex d85ced2..ea14246 100644
--- a/drivers/bluetooth/ath3k.c
+++ b/drivers/bluetooth/ath3k.c
@@ -68,6 +68,7 @@ static const struct usb_device_id ath3k_table[] = {
     { USB_DEVICE(0x0930, 0x0215) },
     { USB_DEVICE(0x0CF3, 0x3002) },
     { USB_DEVICE(0x0CF3, 0xE019) },
+    { USB_DEVICE(0x13d3, 0x3408) },
     { USB_DEVICE(0x13d3, 0x3304) },
 
     /* Atheros AR9285 Malbec with sflash firmware */
diff --git a/drivers/bluetooth/btusb.c b/drivers/bluetooth/btusb.c
index edfc17b..3f935b1 100644
--- a/drivers/bluetooth/btusb.c
+++ b/drivers/bluetooth/btusb.c
@@ -145,6 +145,7 @@ static const struct usb_device_id blacklist_table[] = {
     { USB_DEVICE(0x0930, 0x0215), .driver_info = BTUSB_IGNORE },
     { USB_DEVICE(0x0cf3, 0x3002), .driver_info = BTUSB_IGNORE },
     { USB_DEVICE(0x0cf3, 0xe019), .driver_info = BTUSB_IGNORE },
+    { USB_DEVICE(0x13d3, 0x3408), .driver_info = BTUSB_IGNORE },
     { USB_DEVICE(0x13d3, 0x3304), .driver_info = BTUSB_IGNORE },
 
     /* Atheros AR9285 Malbec with sflash firmware */
```

I looked the VID/PID up on a windows inf file and it showed it was an Atheros BT 4.0 device and IIRC the AR3011 is BT 3.0

---

### Post by Pilot6 on 2014-11-18
What is your iProduct in lsusb -v?

---

### Post by jeremy31 on 2014-11-18
> **Pilot6 said:**
> What is your iProduct in lsusb -v?
I don't have the device as the original poster, just someone trying to help, and someone willing to learn

---

### Post by doylefermi on 2014-11-19
The patch by Jeremy works fine. However each time the computer is restarted or logged out I need to run this code to get it working.

```
sudo modprobe -r btusb
sudo modprobe ath3k

```

Is there a permanent solution to it? Btusb should be removed permanantly?

---

### Post by Pilot6 on 2014-11-19
> **doylefermi said:**
> The patch by Jeremy works fine. However each time the computer is restarted or logged out I need to run this code to get it working.

```
sudo modprobe -r btusb
sudo modprobe ath3k

```

Is there a permanent solution to it? Btusb should be removed permanantly?

It is better to use kernel image with applied patch. I gave   a link. I submitted a patch and it will be applied to mainline kernel some time later.

This is the patched 3.16 kernel
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

---

### Post by Pilot6 on 2014-11-19
> **jeremy31 said:**
> I looked the VID/PID up on a windows inf file and it showed it was an Atheros BT 4.0 device and IIRC the AR3011 is BT 3.0

But it does not show AR3012 there. Either way, I tested the new patch and it looks like there are no issues with turning on/off this way.

---

### Post by doylefermi on 2014-11-19
How do we apply the patched kernel? There are 2 files right. What now?

---

### Post by Pilot6 on 2014-11-19
Place them in home derectory. Then do in terminal.

sudo dpkg -i linux*.deb

Then reboot

---

### Post by doylefermi on 2014-11-19
It doesn't work.

OUTPUT:-
```
sudo dpkg -i linux*.deb

```[sudo] password for haxorware: 
Selecting previously unselected package linux-backports-modules-cw-3.8-precise-generic.
(Reading database ... 219024 files and directories currently installed.)
Preparing to unpack linux-backports-modules-cw-3.8-precise-generic_3.2.0.70.84_amd64.deb ...
Unpacking linux-backports-modules-cw-3.8-precise-generic (3.2.0.70.84) ...
Selecting previously unselected package linux-headers-3.16.7-focaltech3+bt2+.
Preparing to unpack linux-headers-3.16.7-focaltech3+bt2+_3.16.7-focaltech3+bt2+-10.00.Custom_amd64.deb ...
Unpacking linux-headers-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
Selecting previously unselected package linux-image-3.16.7-focaltech3+bt2+.
Preparing to unpack linux-image-3.16.7-focaltech3+bt2+_3.16.7-focaltech3+bt2+-10.00.Custom_amd64.deb ...
Done.
Unpacking linux-image-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
dpkg: dependency problems prevent configuration of linux-backports-modules-cw-3.8-precise-generic:
 linux-backports-modules-cw-3.8-precise-generic depends on linux-backports-modules-cw-3.8-3.2.0-70-generic; however:
  Package linux-backports-modules-cw-3.8-3.2.0-70-generic is not installed.


dpkg: error processing package linux-backports-modules-cw-3.8-precise-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Error! Error! echo
Your kernel headers for kernel 3.16.7-focaltech3+bt2+ cannot be found at
/lib/modules/3.16.7-focaltech3+bt2+/build or /lib/modules/3.16.7-focaltech3+bt2+/source.
echo
Your kernel headers for kernel 3.16.7-focaltech3+bt2+ cannot be found at
/lib/modules/3.16.7-focaltech3+bt2+/build or /lib/modules/3.16.7-focaltech3+bt2+/source.
Setting up linux-image-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...


 Hmm. There is a symbolic link /lib/modules/3.16.7-focaltech3+bt2+/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.7-focaltech3+bt2+/build




 Hmm. The package shipped with a symbolic link /lib/modules/3.16.7-focaltech3+bt2+/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.7-focaltech3+bt2+/source


Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Error! Bad return status for module build on kernel: 3.16.7-focaltech3+bt2+ (x86_64)
Consult /var/lib/dkms/virtualbox-guest/4.3.10/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
update-initramfs: Generating /boot/initrd.img-3.16.7-focaltech3+bt2+
Warning: No support for locale: en_IN
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.7-focaltech3+bt2+
Found initrd image: /boot/initrd.img-3.16.7-focaltech3+bt2+
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done
Errors were encountered while processing:
 linux-backports-modules-cw-3.8-precise-generic



And bluetooth still doesnt work.

```
hcitool scan 

```Device is not available: No such device

---

### Post by Pilot6 on 2014-11-19
Do in terminal

sudo rfkill unblock all

If it does not work give outout of

lsusb

---

### Post by doylefermi on 2014-11-19
Doesn't work

```
lsusb
```


Bus 001 Device 003: ID 0000:0538  
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 13d3:3408 IMC Networks 
Bus 002 Device 003: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 03f0:e507 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```



[COLOR=#000000]hcitool scan[/COLOR]

```[COLOR=#000000]Device is not available: No such device[/COLOR]

---

### Post by Pilot6 on 2014-11-19
Hm. Looks OK.
Please give

dmesg | grep usb
rfkill list

---

### Post by Pilot6 on 2014-11-19
Please give

rfkill list
dmesg | egrep 'usb | btusb | ath3k'

---

### Post by doylefermi on 2014-11-19
```
 dmesg | grep usb

```[    0.258229] usbcore: registered new interface driver usbfs
[    0.258239] usbcore: registered new interface driver hub
[    0.258287] usbcore: registered new device driver usb
[    1.010083] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.010086] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.010089] usb usb1: Product: EHCI Host Controller
[    1.010091] usb usb1: Manufacturer: Linux 3.16.7-focaltech3+bt2+ ehci_hcd
[    1.010092] usb usb1: SerialNumber: 0000:00:1d.0
[    1.010896] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.010898] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.010900] usb usb2: Product: xHCI Host Controller
[    1.010902] usb usb2: Manufacturer: Linux 3.16.7-focaltech3+bt2+ xhci_hcd
[    1.010904] usb usb2: SerialNumber: 0000:00:14.0
[    1.014374] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.014376] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.014378] usb usb3: Product: xHCI Host Controller
[    1.014380] usb usb3: Manufacturer: Linux 3.16.7-focaltech3+bt2+ xhci_hcd
[    1.014382] usb usb3: SerialNumber: 0000:00:14.0
[    1.321864] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.454190] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.454195] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.981448] usb 2-2: new high-speed USB device number 2 using xhci_hcd
[    2.110989] usb 2-2: New USB device found, idVendor=03f0, idProduct=e507
[    2.110993] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.110994] usb 2-2: Product: v218g
[    2.110996] usb 2-2: Manufacturer: HP
[    2.110997] usb 2-2: SerialNumber: AA00000000000973
[    2.111126] usb 2-2: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[    2.111131] usb 2-2: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[    2.112373] usb-storage 2-2:1.0: USB Mass Storage device detected
[    2.112583] scsi4 : usb-storage 2-2:1.0
[    2.112662] usbcore: registered new interface driver usb-storage
[    2.277289] usb 2-5: new high-speed USB device number 3 using xhci_hcd
[    2.438059] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a
[    2.438063] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.438065] usb 2-5: Product: USB2.0 HD UVC WebCam
[    2.438066] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.438068] usb 2-5: SerialNumber: 0x0001
[    2.605128] usb 2-6: new full-speed USB device number 4 using xhci_hcd
[    2.734033] usb 2-6: New USB device found, idVendor=13d3, idProduct=3408
[    2.734036] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.932992] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    3.028653] usb 1-1.3: New USB device found, idVendor=0000, idProduct=0538
[    3.028657] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    3.028660] usb 1-1.3: Product:  USB OPTICAL MOUSE
[    3.032157] usbcore: registered new interface driver usbhid
[    3.032161] usbhid: USB HID core driver
[    3.032786] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:0000:0538.0001/input/input12
[    3.033031] hid-generic 0003:0000:0538.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.3/input0
[   16.063121] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input19
[   16.063215] usbcore: registered new interface driver uvcvideo
[   16.065116] usbcore: registered new interface driver btusb
[   19.531774] usbcore: registered new interface driver ath3k
[   43.231932] usb 2-6: USB disconnect, device number 4
[   51.701866] usb 2-6: new full-speed USB device number 5 using xhci_hcd
[   51.830934] usb 2-6: New USB device found, idVendor=13d3, idProduct=3408
[   51.830939] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
```


rfkill list 

```0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by doylefermi on 2014-11-19
```
dmesg | egrep 'usb | btusb | ath3k'

```[    1.010083] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.010086] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.010089] usb usb1: Product: EHCI Host Controller
[    1.010091] usb usb1: Manufacturer: Linux 3.16.7-focaltech3+bt2+ ehci_hcd
[    1.010092] usb usb1: SerialNumber: 0000:00:1d.0
[    1.010896] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.010898] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.010900] usb usb2: Product: xHCI Host Controller
[    1.010902] usb usb2: Manufacturer: Linux 3.16.7-focaltech3+bt2+ xhci_hcd
[    1.010904] usb usb2: SerialNumber: 0000:00:14.0
[    1.014374] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.014376] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.014378] usb usb3: Product: xHCI Host Controller
[    1.014380] usb usb3: Manufacturer: Linux 3.16.7-focaltech3+bt2+ xhci_hcd
[    1.014382] usb usb3: SerialNumber: 0000:00:14.0
[    1.321864] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.454190] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.454195] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.981448] usb 2-2: new high-speed USB device number 2 using xhci_hcd
[    2.110989] usb 2-2: New USB device found, idVendor=03f0, idProduct=e507
[    2.110993] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.110994] usb 2-2: Product: v218g
[    2.110996] usb 2-2: Manufacturer: HP
[    2.110997] usb 2-2: SerialNumber: AA00000000000973
[    2.111126] usb 2-2: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[    2.111131] usb 2-2: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[    2.277289] usb 2-5: new high-speed USB device number 3 using xhci_hcd
[    2.438059] usb 2-5: New USB device found, idVendor=04f2, idProduct=b40a
[    2.438063] usb 2-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.438065] usb 2-5: Product: USB2.0 HD UVC WebCam
[    2.438066] usb 2-5: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.438068] usb 2-5: SerialNumber: 0x0001
[    2.605128] usb 2-6: new full-speed USB device number 4 using xhci_hcd
[    2.734033] usb 2-6: New USB device found, idVendor=13d3, idProduct=3408
[    2.734036] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.932992] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    3.028653] usb 1-1.3: New USB device found, idVendor=0000, idProduct=0538
[    3.028657] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    3.028660] usb 1-1.3: Product:  USB OPTICAL MOUSE
[   19.531728] ath3k: probe of 2-6:1.0 failed with error -110
[   19.531774] usbcore: registered new interface driver ath3k
[   22.709980] ath3k: probe of 2-6:1.0 failed with error -110
[   25.764373] ath3k: probe of 2-6:1.0 failed with error -110
[   43.231932] usb 2-6: USB disconnect, device number 4
[   51.701866] usb 2-6: new full-speed USB device number 5 using xhci_hcd
[   51.830934] usb 2-6: New USB device found, idVendor=13d3, idProduct=3408
[   51.830939] usb 2-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   54.884098] ath3k: probe of 2-6:1.0 failed with error -110

---

### Post by Pilot6 on 2014-11-19
I hope you did not do wrong... I gave directions later.

---

### Post by Pilot6 on 2014-11-19
Oops sry. Do not do it!

---

### Post by Pilot6 on 2014-11-19
To enable the driver you need to turn off then on the laptop (not reboot). It should work with the previous kernel.
I was confused myself. You need to poweroff to let firmware be loaded after old kernel.

---

### Post by doylefermi on 2014-11-19
Tried like you told. Shutdown. Even removed the battery. And started. Still doesnt work.

---

### Post by Pilot6 on 2014-11-19
Hm. Then try the other image

sudo apt-get purge linux-headers-3.16.7-focaltech3+bt2+ linux-image-3.16.7-focaltech3+bt2+

Remove debs from your home folder and download new ones from here.

[https://www.dropbox.com/sh/un33oz6gh6us221/AABgynTRh8UQw4qlp5THXcbGa?dl=0](https://www.dropbox.com/sh/un33oz6gh6us221/AABgynTRh8UQw4qlp5THXcbGa?dl=0)

Install them, then poweroff and on.
After start

sudo rfkill unblock all
hcitool scan

---

### Post by doylefermi on 2014-11-19
Nope. Still doesnt work :(

---

### Post by Pilot6 on 2014-11-19
I saw you had and old wrong cw module. Do 

sudo apt-get purge [COLOR=#000000]linux-backports-modules-cw-3.8-precise-generic

But I do not think that can affect things.

No more ideas. Same module works for me with this kernel.[/COLOR]

---

### Post by doylefermi on 2014-11-19
How do i revert back to the old kernel 3.13.0-39 ??

---

### Post by Pilot6 on 2014-11-19
give output

dpkg -l  [COLOR=#000000] | grep linux-image-3.16.7*[/COLOR]

---

### Post by doylefermi on 2014-11-19
Hey I did what you told...

```
[COLOR=#000000]sudo apt-get purge [/COLOR][COLOR=#000000][COLOR=#000000]linux-backports-modules-cw-3.8-precise-generic[/COLOR][/COLOR]
```

And it worked. Now bluetooth's fine. However I had an overclocking app (that sets the frequency), that doesn't work and my mic(internal) too doesnt work(it didnt work on the previous one). Is there a fix for that?

---

### Post by Pilot6 on 2014-11-19
Did it work with 3.13.0-39? If not, then open another thread.

---

### Post by Pilot6 on 2014-11-19
And also I would suggest set back that bt2 kernel image. The last one may have issues with bt turn on or off. I just tried to test it too, when I was out of ideas.

---

### Post by doylefermi on 2014-11-19
I started a thread but noone has a solution yet. 

[http://ubuntuforums.org/showthread.php?t=2251129](http://ubuntuforums.org/showthread.php?t=2251129)

The CPU frequency worked on 39. I guess ur kernel doesnt support that.

And what do u mean by:
> [COLOR=#000000]And also I would suggest set back that bt2 kernel image. The last one may have issues with bt turn on or off. I just tried to test it too, when I was out of ideas.[/COLOR]

---

### Post by Pilot6 on 2014-11-19
Did you download another set of debs, which have bt in their names and not bt2? If you have installed them, then I suddest to change back to bt2.

Regarding the kernel. It is official 3.16.0-25 kernel, which is in 14.10 and soon will be in 14.04.2.
I just ported there a bt driver and focaltech touchpad driver. Nothing else.

I do not know why something may not work there.

---

### Post by doylefermi on 2014-11-19
But i tried bt2 1st : [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)
That one didn't work.

bt worked: [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

---

### Post by Pilot6 on 2014-11-19
I think it did not work because of that bad cw module, which you deleted later. They both should work.

Please test it. It is important for kernel development. Do

[COLOR=#000000]sudo apt-get purge linux-headers-3.16.7-focaltech3+bt+ linux-image-3.16.7-focaltech3+bt+[/COLOR]

Then remove from home folder all previous debs and leave only those with bt2 it the name.
Then install by

sudo dpkg -i linux*.deb

Poweroff and on. Try bt.

---

### Post by doylefermi on 2014-11-19
Tried like you told. BT works fine, BT2 doesnt.

---

### Post by Pilot6 on 2014-11-19
Please show 

dmesg | egrep 'btusb|ath3k'

---

### Post by Pilot6 on 2014-11-19
Did you do

sudo rfkill unblock all

---

