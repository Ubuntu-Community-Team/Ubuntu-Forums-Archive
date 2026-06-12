---
title: "Realtek Realtek RTL8723BE/RTL8188EE 802.11b/g/n Wireless pci drivers not working."
date: 2018-06-12
forum: Networking &amp; Wireless
---

### Post by pandora9201 on 2018-06-12
Hello everyone. So I have  a HP laptop with realtek rtl8723BE/rtl8188EE  pci wireless card. But the drivers for that are not loaded by default.  And also i have tried installing it using modprobe and it did not  worked. Also i the dmesg log showed some error about ver-magic. The  bluetooth is also not working. Can anyone point me out to how i can  install drivers for that. I am using ubuntu 18.04 LTS. 

lspci

```
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0  Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT  [Radeon HD 8670A/8670M/8690M / R5 M330 / M430] (rev 83)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
```

I had install linux generic package too. But no help.
Now i have done modprobe again, and lsmod shows this:

lsmod
```
Module                  Size  Used by
rtl8723be              98304  0
btcoexist             131072  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
ccm                    20480  9
arc4                   16384  2
ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              471040  2 ath9k_htc,ath9k_common
ath                    28672  3 ath9k_htc,ath9k_hw,ath9k_common
mac80211              778240  4 ath9k_htc,rtl_pci,rtlwifi,rtl8723be
cfg80211              622592  5 ath9k_htc,mac80211,ath,rtlwifi,ath9k_common
bnep                   20480  2
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             204800  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
snd_hda_codec_hdmi     49152  1
crct10dif_pclmul       16384  0
snd_soc_skl            90112  0
crc32_pclmul           16384  0
snd_soc_skl_ipc        65536  1 snd_soc_skl
ghash_clmulni_intel    16384  0
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_hda_codec_realtek   102400  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_acpi           16384  1 snd_soc_skl
snd_soc_core          241664  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
pcbc                   16384  0
uvcvideo               86016  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          40960  6
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_hda_core            81920  7  snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                 98304  8  snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
aesni_intel           188416  6
media                  40960  2 uvcvideo,videodev
btusb                  45056  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
glue_helper            16384  1 aesni_intel
btintel                16384  1 btusb
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
bluetooth             548864  12 btrtl,btintel,bnep,btbcm,btusb
ecdh_generic           24576  1 bluetooth
snd_seq_midi           16384  0
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
hp_wmi                 16384  0
input_leds             16384  0
joydev                 24576  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
kxcjk_1013             20480  0
industrialio_triggered_buffer    16384  1 kxcjk_1013
intel_vbtn             16384  0
snd_timer              32768  2 snd_seq,snd_pcm
mac_hid                16384  0
sparse_keymap          16384  2 intel_vbtn,hp_wmi
shpchp                 36864  0
kfifo_buf              16384  1 industrialio_triggered_buffer
snd                     81920  25  snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
processor_thermal_device    16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
int3400_thermal        16384  0
intel_pch_thermal      16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
mei_me                 40960  0
mei                    90112  1 mei_me
industrialio           69632  3 kxcjk_1013,industrialio_triggered_buffer,kfifo_buf
hp_wireless            16384  0
soundcore              16384  1 snd
acpi_pad              180224  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
amdgpu               2703360  0
chash                  16384  1 amdgpu
radeon               1470464  2
i915                 1617920  24
ttm                   106496  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        167936  3 amdgpu,radeon,i915
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  21 amdgpu,radeon,i915,ttm,drm_kms_helper
r8169                  86016  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
wmi                    24576  3 wmi_bmof,intel_wmi_thunderbolt,hp_wmi
video                  40960  1 i915
```

As  you can see i have loaded multiple modules. I am a newbie. I have other  adapter too, which is working and using ath9k_htc drivers i guess. And  it a dual boot system, with windows 10, Bluetooth and wifi interface are  working in windows 10 properly. And also secure boot is disabled. Any  help is highly appreciated. :) I am looking for the solution and doing  hit and trials from 3 days and finally decided to post. :D

---

