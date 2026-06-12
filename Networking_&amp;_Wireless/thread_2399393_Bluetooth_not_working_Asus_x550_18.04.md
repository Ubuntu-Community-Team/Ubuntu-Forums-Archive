---
title: "Bluetooth not working Asus x550 18.04"
date: 2018-08-24
forum: Networking &amp; Wireless
---

### Post by wavecycle on 2018-08-24
I disabled bluetooth in an old windows installation, deleted now, and bluetooth doesn't work. In the config panel it simply says "No bluetooth found"

Ive tried locking then unlocking in bios but no luck.

Help will be greatly appreciated :)

---

### Post by praseodym on 2018-08-24
Hi,

lets see these outputs
```

lsusb
usb-devices
lsmod
rfkill list
```

---

### Post by wavecycle on 2018-08-24
Thank you

```
justin@trollmini:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 045e:070f Microsoft Corp. LifeChat LX-3000 Headset
Bus 002 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
justin@trollmini:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.15
S:  Manufacturer=Linux 4.15.0-32-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.15
S:  Manufacturer=Linux 4.15.0-32-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  2
P:  Vendor=04e8 ProdID=6860 Rev=04.00
S:  Manufacturer=SAMSUNG
S:  Product=SAMSUNG_Android
S:  SerialNumber=4d002c7a411590ed
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=96mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=usbfs


T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=045e ProdID=070f Rev=01.00
S:  Product=Microsoft LifeChat LX-3000 
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b40a Rev=69.64
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=USB2.0 HD UVC WebCam
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.15
S:  Manufacturer=Linux 4.15.0-32-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```
```
justin@trollmini:~$ lsmod
Module                  Size  Used by
bluetooth             548864  0
ecdh_generic           24576  1 bluetooth
ccm                    20480  6
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
mei_me                 40960  0
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              622592  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
input_leds             16384  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_usb_audio         196608  5
snd_usbmidi_lib        32768  1 snd_usb_audio
mei                    90112  1 mei_me
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             208896  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  4
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
int3402_thermal        16384  0
snd_hda_codec_hdmi     49152  1
joydev                 24576  0
lpc_ich                24576  0
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
serio_raw              16384  0
sparse_keymap          16384  1 asus_wmi
intel_pch_thermal      16384  0
snd_hda_codec_realtek    94208  1
rtsx_pci_ms            20480  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
memstick               16384  1 rtsx_pci_ms
snd_hda_intel          40960  10
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_hda_codec,snd_usb_audio
snd_pcm                98304  7 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  41 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
soundcore              16384  1 snd
mac_hid                16384  0
int340x_thermal_zone    16384  2 int3402_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
asus_wireless          16384  0
binfmt_misc            20480  1
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1617920  29
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               147456  0
drm                   401408  17 i915,drm_kms_helper
r8169                  86016  0
ahci                   36864  2
libahci                32768  1 ahci
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
wmi                    24576  1 asus_wmi
video                  45056  2 asus_wmi,i915
```
```
justin@trollmini:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
justin@trollmini:~$
```

---

### Post by praseodym on 2018-08-25
Hm, maybe a combo card?!
```

lspci -nnk
```

---

### Post by wavecycle on 2018-08-25
thank you :)

justin@trollmini:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Haswell-ULT DRAM Controller [1043:131d]
	Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Haswell-ULT Integrated Graphics Controller [1043:131d]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Haswell-ULT HD Audio Controller [1043:131d]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Haswell-ULT Thermal Subsystem [8086:0a03] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Haswell-ULT Thermal Subsystem [1043:131d]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series USB xHCI HC [1043:201f]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series HECI [1043:131d]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series HD Audio Controller [1043:11af]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 4 [8086:9c16] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series USB EHCI #1 [8086:9c26] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series USB EHCI [1043:201f]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series LPC Controller [1043:131d]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series SATA Controller 1 [AHCI mode] [1043:131d]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series SMBus Controller [1043:131d]
	Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 8 Series Thermal [8086:9c24] (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series Thermal [1043:131d]
	Kernel driver in use: intel_pch_thermal
	Kernel modules: intel_pch_thermal
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)
	Subsystem: ASUSTeK Computer Inc. RTL8411B PCI Express Card Reader [1043:202f]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Foxconn International, Inc. RT3290 Wireless 802.11n 1T/1R PCIe [105b:e055]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
03:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
	Subsystem: Foxconn International, Inc. RT3290 Bluetooth [105b:e056]
justin@trollmini:~$

---

### Post by praseodym on 2018-08-25
```
03:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
Subsystem: Foxconn International, Inc. RT3290 Bluetooth [105b:e056]
```
There it is

```
sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install dkms rtbth-dkms blueman
sudo modprobe -v rtbth 
```

---

### Post by wavecycle on 2018-08-25
Yes, that is working now :) linked with my mobile, will see if I can link with the hifi. You're a champ :)

---

### Post by gammonjosh on 2019-01-04
Maybe you guys can help me.  I have the same computer and had the same BT problem.  I ran the PPA and installed DKMS rtbth and the bluetooth worked! YA!!  Here's the problem.  If I turn off BT or restart the computer I have to re run the 'sudo modprobe -v rtbth' command again to get it working.  Is there a way to keep it working without running the command everytime.  Or is it just a buggy BT driver?[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by QIII on 2019-01-04
Hello!

You would be much more likely to get help if you were to start your own thread describing your issue.  You may cite a link to this thread for reference.

Closed.

---

