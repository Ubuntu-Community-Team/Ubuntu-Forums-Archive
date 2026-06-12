---
title: "Could not find Bluetooth driver for HP Notebook - 15-bs179tx for Ubuntu 16.04 LTS"
date: 2018-07-24
forum: Networking &amp; Wireless
---

### Post by aravind1994cs on 2018-07-24
A part of output produced by the command:
```
sudo lshw -html > mySpecs.html
```

[LIST]
[*]id: usb:1
[*]description: Bluetooth wireless interface
[*]product: 802.11n WLAN Adapter
[*]vendor: Realtek
[*]physical id: 4
[*]bus info: usb@1:4
[*]version: 2.00
[*]serial: 00e04c000001
[*]capabilities: bluetooth usb-1.10
[*]configuration:
[LIST]
[*]driver = btusb
[*]maxpower = 500mA
[*]speed = 12Mbit/s
[/LIST]
[/LIST]
[COLOR=#111111][FONT=Ubuntu][Here's a link for Laptop Specifications]("https://support.hp.com/in-en/document/c05835980")[/FONT][/COLOR]

---

### Post by chili555 on 2018-07-24
> driver = btusbEvidently, your system finds a driver. 

Is your bluetooth not working?

May we see the result of the terminal commands:```
dmesg | grep -i -e bt -e blue
rfkill list all
```

---

### Post by praseodym on 2018-07-24
Lets also see
```

lsusb
usb-devices
lsmod
```

---

### Post by aravind1994cs on 2018-07-27
[COLOR=#000000]Yes, it is not working. Please take a look at this snapshot.

[/COLOR] [ATTACH=CONFIG]280526[/ATTACH][COLOR=#000000]



The result of the terminal commands are as follows:[/COLOR]

```
$ dmesg | grep -i -e bt -e blue

```

[ 15.766015] acpi INT33D6:00: intel-vbtn: created platform device
[ 15.766238] intel-vbtn INT33D6:00: failed to read Intel Virtual Button driver
[ 15.799960] Bluetooth: Core ver 2.22
[ 15.799973] Bluetooth: HCI device and connection manager initialized
[ 15.799976] Bluetooth: HCI socket layer initialized
[ 15.799978] Bluetooth: L2CAP socket layer initialized
[ 15.799982] Bluetooth: SCO socket layer initialized
[ 15.816679] usbcore: registered new interface driver btusb
[ 15.817652] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[ 15.817653] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[ 15.876757] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[ 15.876759] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[ 15.888682] Bluetooth: hci0: rom_version status=0 version=2
[ 15.888692] Bluetooth: hci0: didn't find patch for chip id 2
[ 15.889903] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[ 15.889904] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[ 15.889911] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[ 15.889912] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[ 15.890892] Bluetooth: hci0: rom_version status=0 version=2
[ 15.890893] Bluetooth: hci0: didn't find patch for chip id 2
[ 16.178379] RTW: rtl8723de BT-Coex version = BTCOEX20170111-1414
[ 16.314058] RTW: Hal_EfuseParseBTCoexistInfo_8723D: Enable BT-coex, ant_num=1
[ 21.683260] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 21.683261] Bluetooth: BNEP filters: protocol multicast
[ 21.683266] Bluetooth: BNEP socket layer initialized
[ 48.346634] RTW: LocBTQosNull: 3
[ 48.346641] RTW: RsvdPageLoc: ProbeRsp=0 PsPoll=2 Null=4 QoSNull=5 BTNull=3

```
$ rfkill list all

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by aravind1994cs on 2018-07-27
[COLOR=#000000]Yes, it is not working. Please take a look at this snapshot.

[/COLOR][ATTACH=CONFIG]280526[/ATTACH][COLOR=#000000]



The result of the terminal commands are as follows:[/COLOR]

```
$ dmesg | grep -i -e bt -e blue

```

[ 15.766015] acpi INT33D6:00: intel-vbtn: created platform device
[ 15.766238] intel-vbtn INT33D6:00: failed to read Intel Virtual Button driver
[ 15.799960] Bluetooth: Core ver 2.22
[ 15.799973] Bluetooth: HCI device and connection manager initialized
[ 15.799976] Bluetooth: HCI socket layer initialized
[ 15.799978] Bluetooth: L2CAP socket layer initialized
[ 15.799982] Bluetooth: SCO socket layer initialized
[ 15.816679] usbcore: registered new interface driver btusb
[ 15.817652] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[ 15.817653] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[ 15.876757] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[ 15.876759] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[ 15.888682] Bluetooth: hci0: rom_version status=0 version=2
[ 15.888692] Bluetooth: hci0: didn't find patch for chip id 2
[ 15.889903] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[ 15.889904] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[ 15.889911] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[ 15.889912] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[ 15.890892] Bluetooth: hci0: rom_version status=0 version=2
[ 15.890893] Bluetooth: hci0: didn't find patch for chip id 2
[ 16.178379] RTW: rtl8723de BT-Coex version = BTCOEX20170111-1414
[ 16.314058] RTW: Hal_EfuseParseBTCoexistInfo_8723D: Enable BT-coex, ant_num=1
[ 21.683260] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 21.683261] Bluetooth: BNEP filters: protocol multicast
[ 21.683266] Bluetooth: BNEP socket layer initialized
[ 48.346634] RTW: LocBTQosNull: 3
[ 48.346641] RTW: RsvdPageLoc: ProbeRsp=0 PsPoll=2 Null=4 QoSNull=5 BTNull=3

```
$ rfkill list all

```

0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

---

### Post by aravind1994cs on 2018-07-27
```
$ lsusb

```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c9b Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
$ usb-devices

```

T: Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=480 MxCh=12
D: Ver= 2.00 Cls=09(hub ) Sub=00 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=1d6b ProdID=0002 Rev=04.15
S: Manufacturer=Linux 4.15.0-29-generic xhci-hcd
S: Product=xHCI Host Controller
S: SerialNumber=0000:00:14.0
C: #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub


T: Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 2 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=0bda ProdID=b009 Rev=02.00
S: Manufacturer=Realtek
S: Product=802.11n WLAN Adapter
S: SerialNumber=00e04c000001
C: #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I: If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T: Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=1bcf ProdID=2c9b Rev=00.05
S: Manufacturer=DGENB019I99GZC
S: Product=HP TrueVision HD Camera
C: #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I: If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T: Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=5000 MxCh= 6
D: Ver= 3.00 Cls=09(hub ) Sub=00 Prot=03 MxPS= 9 #Cfgs= 1
P: Vendor=1d6b ProdID=0003 Rev=04.15
S: Manufacturer=Linux 4.15.0-29-generic xhci-hcd
S: Product=xHCI Host Controller
S: SerialNumber=0000:00:14.0
C: #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub


```
$ lsmod

```

Module Size Used by
bnep 20480 2
binfmt_misc 20480 1
nls_iso8859_1 16384 1
snd_hda_codec_hdmi 49152 1
snd_hda_codec_realtek 98304 1
snd_hda_codec_generic 73728 1 snd_hda_codec_realtek
uvcvideo 86016 0
videobuf2_vmalloc 16384 1 uvcvideo
videobuf2_memops 16384 1 videobuf2_vmalloc
videobuf2_v4l2 24576 1 uvcvideo
videobuf2_core 40960 2 uvcvideo,videobuf2_v4l2
videodev 180224 3 uvcvideo,videobuf2_core,videobuf2_v4l2
media 40960 2 uvcvideo,videodev
8723de 1687552 0
cfg80211 622592 1 8723de
snd_soc_skl 90112 0
snd_soc_skl_ipc 65536 1 snd_soc_skl
snd_hda_ext_core 24576 1 snd_soc_skl
snd_soc_sst_dsp 32768 1 snd_soc_skl_ipc
snd_soc_sst_ipc 16384 1 snd_soc_skl_ipc
snd_soc_acpi 16384 1 snd_soc_skl
snd_soc_core 241664 1 snd_soc_skl
snd_compress 20480 1 snd_soc_core
ac97_bus 16384 1 snd_soc_core
snd_pcm_dmaengine 16384 1 snd_soc_core
snd_hda_intel 40960 3
snd_hda_codec 126976 4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core 81920 7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep 20480 1 snd_hda_codec
snd_pcm 98304 8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi 16384 0
snd_seq_midi_event 16384 1 snd_seq_midi
snd_rawmidi 32768 1 snd_seq_midi
snd_seq 65536 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 16384 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 32768 2 snd_seq,snd_pcm
intel_rapl 20480 0
x86_pkg_temp_thermal 16384 0
intel_powerclamp 16384 0
coretemp 16384 0
kvm 598016 0
irqbypass 16384 1 kvm
crct10dif_pclmul 16384 0
crc32_pclmul 16384 0
ghash_clmulni_intel 16384 0
pcbc 16384 0
aesni_intel 188416 0
aes_x86_64 20480 1 aesni_intel
crypto_simd 16384 1 aesni_intel
glue_helper 16384 1 aesni_intel
cryptd 24576 3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate 20480 0
intel_rapl_perf 16384 0
btusb 45056 0
btrtl 16384 1 btusb
btbcm 16384 1 btusb
btintel 16384 1 btusb
bluetooth 557056 12 btrtl,btintel,bnep,btbcm,btusb
joydev 24576 0
input_leds 16384 0
hp_wmi 16384 0
wmi_bmof 16384 0
snd 81920 19 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
serio_raw 16384 0
intel_wmi_thunderbolt 16384 0
soundcore 16384 1 snd
ecdh_generic 24576 1 bluetooth
shpchp 36864 0
mei_me 40960 0
intel_pch_thermal 16384 0
processor_thermal_device 16384 0
mei 90112 1 mei_me
int340x_thermal_zone 16384 1 processor_thermal_device
intel_soc_dts_iosf 16384 1 processor_thermal_device
intel_vbtn 16384 0
sparse_keymap 16384 2 intel_vbtn,hp_wmi
kxcjk_1013 20480 0
industrialio_triggered_buffer 16384 1 kxcjk_1013
kfifo_buf 16384 1 industrialio_triggered_buffer
industrialio 69632 3 kxcjk_1013,industrialio_triggered_buffer,kfifo_buf
int3400_thermal 16384 0
acpi_pad 180224 0
acpi_thermal_rel 16384 1 int3400_thermal
mac_hid 16384 0
hp_wireless 16384 0
parport_pc 36864 0
ppdev 20480 0
lp 20480 0
parport 49152 3 lp,parport_pc,ppdev
autofs4 40960 2
amdgpu 2732032 0
chash 16384 1 amdgpu
radeon 1478656 1
i915 1630208 63
ttm 106496 2 amdgpu,radeon
i2c_algo_bit 16384 3 amdgpu,radeon,i915
drm_kms_helper 172032 3 amdgpu,radeon,i915
syscopyarea 16384 1 drm_kms_helper
sysfillrect 16384 1 drm_kms_helper
sysimgblt 16384 1 drm_kms_helper
fb_sys_fops 16384 1 drm_kms_helper
psmouse 147456 0
r8169 86016 0
drm 401408 11 amdgpu,radeon,i915,ttm,drm_kms_helper
ahci 36864 4
mii 16384 1 r8169
libahci 32768 1 ahci
wmi 24576 3 wmi_bmof,intel_wmi_thunderbolt,hp_wmi
video 45056 1 i915

---

### Post by chili555 on 2018-07-27
> 8723de 1687552 0
cfg80211 622592 1 8723deThis is one of the drivers that allows antenna selection and I am interested in this line from your log:> RTW: Hal_EfuseParseBTCoexistInfo_8723D: Enable BT-coex, [COLOR="#FF0000"]ant_num=1[/COLOR]Is your wireless working well? Do you have good signal strength?

Frankly, so far, I see nothing that looks like a problem that disables your bluetooth.

---

### Post by praseodym on 2018-07-27
For the BT firmware see here

[https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640](https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640)

---

### Post by aravind1994cs on 2018-08-04
> **chili555 said:**
> This is one of the drivers that allows antenna selection and I am interested in this line from your log:Is your wireless working well? Do you have good signal strength?

Frankly, so far, I see nothing that looks like a problem that disables your bluetooth.

Do you mean Wi-Fi? Yes, I have a good signal strength.
I downloaded the driver from [https://github.com/smlinux/rtl8723de](https://github.com/smlinux/rtl8723de).

---

### Post by aravind1994cs on 2018-08-04
> **praseodym said:**
> For the BT firmware see here

[https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640](https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640)

That is a good thread. But my kernel version is 4.15.0-29-generic. I am not okay with the idea of manually updating the kernel(say using ukuu) as I read in this blog([https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)) that it might not be reliable enough for everyday use.

---

