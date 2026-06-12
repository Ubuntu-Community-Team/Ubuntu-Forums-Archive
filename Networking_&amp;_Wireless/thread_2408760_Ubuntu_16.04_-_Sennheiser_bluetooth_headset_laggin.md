---
title: "Ubuntu 16.04 - Sennheiser bluetooth headset lagging with A2DP"
date: 2018-12-22
forum: Networking &amp; Wireless
---

### Post by carlo8 on 2018-12-22
Hi there,
I just got a Sennheiser HD 4.40 BT headset, and it works perfectly with my phone and on Windows 10 (I have a dual boot on my laptop), but it's giving me problems on Ubuntu 16.04.

I can use it with the HSP/HFP audio profile, but the audio quality is plainly horrible. If I switch to A2DP the sound quality gets much better, but then the audio starts lagging. The lag starts almost immediately, it seems the audio is buffering (after I stop the video or the song, it keeps playing the sound for a few seconds afterwards).
I seem to understand it is a common issue, but I can't figure a way to fix it. I read it could be related to the Wi-Fi and the Bluetooth conflicting, but the lag still happens if I connect to Internet through an ethernet cable, or even if I watch a movie on my laptop.

Any suggestion on how to fix this? Thanks!

---

### Post by jeremy31 on 2018-12-23
Can you post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by carlo8 on 2018-12-23
Hi, thanks for the answer! 
This is the output

```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:81ef]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Sanji2 
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
	Kernel driver in use: rtl8723be
	Kernel modules: rtl8723be

```

---

### Post by praseodym on 2018-12-23
```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Sanji2 
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
	Kernel driver in use: rtl8723be
	Kernel modules: rtl8723be
```
Thats an integrated BT card as well. Check
```
lsusb
usb-devices
lsmod
```
without and with the headset

---

### Post by carlo8 on 2018-12-23
This is the output WITHOUT the headset:

**lsusb:**
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b56c Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**usb-devices:**
```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=12
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-141-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b008 Rev=02.00
S:  Manufacturer=Realtek 
S:  Product=Bluetooth Radio 
S:  SerialNumber=00e04c000001
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b56c Rev=88.03
S:  Manufacturer=Generic
S:  Product=HP TrueVision HD
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-141-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```



[B]lsmod:
[/B]```

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
rfcomm                 69632  12
cmac                   16384  2
algif_hash             16384  0
algif_skcipher         20480  0
af_alg                 16384  2 algif_hash,algif_skcipher
bnep                   20480  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_soc_skl            49152  0
hp_wmi                 16384  0
kvm                   552960  0
sparse_keymap          16384  1 hp_wmi
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
irqbypass              16384  1 kvm
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
arc4                   16384  2
uvcvideo               90112  0
aesni_intel           167936  4
rtl8723be              94208  0
aes_x86_64             20480  1 aesni_intel
snd_pcm_dmaengine      16384  1 snd_soc_core
lrw                    16384  1 aesni_intel
btcoexist              53248  1 rtl8723be
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_codec_hdmi     53248  1
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
btusb                  45056  0
media                  24576  2 uvcvideo,videodev
snd_hda_core           77824  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
btrtl                  16384  1 btusb
joydev                 20480  0
snd_hwdep              16384  1 snd_hda_codec
cfg80211              565248  2 mac80211,rtlwifi
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
bluetooth             520192  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
serio_raw              16384  0
snd                    81920  19 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
processor_thermal_device    16384  0
int3400_thermal        16384  0
mei_me                 36864  0
mei                    98304  1 mei_me
hp_wireless            16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
shpchp                 36864  0
i2c_i801               28672  0
acpi_pad               24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
i915_bpo             1335296  5
radeon               1523712  1
psmouse               131072  0
ttm                    98304  1 radeon
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  2 i915_bpo,radeon
drm_kms_helper        155648  2 i915_bpo,radeon
r8169                  86016  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
mii                    16384  1 r8169
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  4
drm                   364544  9 ttm,i915_bpo,drm_kms_helper,radeon
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
video                  40960  1 i915_bpo
fjes                   28672  0

```



*******************************************************************************************************



This is the output WITH the headset

**lsusb:**
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b56c Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```



**usb-devices:**
```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=12
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-141-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b008 Rev=02.00
S:  Manufacturer=Realtek 
S:  Product=Bluetooth Radio 
S:  SerialNumber=00e04c000001
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b56c Rev=88.03
S:  Manufacturer=Generic
S:  Product=HP TrueVision HD
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-141-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```



[B]lsmod:
[/B]```

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
rfcomm                 69632  15
cmac                   16384  2
algif_hash             16384  0
algif_skcipher         20480  0
af_alg                 16384  2 algif_hash,algif_skcipher
bnep                   20480  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_soc_skl            49152  0
hp_wmi                 16384  0
kvm                   552960  0
sparse_keymap          16384  1 hp_wmi
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
irqbypass              16384  1 kvm
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
arc4                   16384  2
uvcvideo               90112  0
aesni_intel           167936  4
rtl8723be              94208  0
aes_x86_64             20480  1 aesni_intel
snd_pcm_dmaengine      16384  1 snd_soc_core
lrw                    16384  1 aesni_intel
btcoexist              53248  1 rtl8723be
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_codec_hdmi     53248  1
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
btusb                  45056  0
media                  24576  2 uvcvideo,videodev
snd_hda_core           77824  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
btrtl                  16384  1 btusb
joydev                 20480  0
snd_hwdep              16384  1 snd_hda_codec
cfg80211              565248  2 mac80211,rtlwifi
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
bluetooth             520192  47 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
serio_raw              16384  0
snd                    81920  19 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
processor_thermal_device    16384  0
int3400_thermal        16384  0
mei_me                 36864  0
mei                    98304  1 mei_me
hp_wireless            16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
shpchp                 36864  0
i2c_i801               28672  0
acpi_pad               24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
i915_bpo             1335296  5
radeon               1523712  1
psmouse               131072  0
ttm                    98304  1 radeon
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  2 i915_bpo,radeon
drm_kms_helper        155648  2 i915_bpo,radeon
r8169                  86016  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
mii                    16384  1 r8169
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  4
drm                   364544  9 ttm,i915_bpo,drm_kms_helper,radeon
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
video                  40960  1 i915_bpo
fjes                   28672  0

```

---

### Post by praseodym on 2018-12-23
So, your headset is not connected via USB?! Maybe the frequency is the same?!

---

### Post by carlo8 on 2018-12-23
Sorry, I tought I said it, the headset is connected via bluetooth.

---

