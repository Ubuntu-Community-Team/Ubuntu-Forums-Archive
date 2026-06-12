---
title: "Wifi dont work ubuntu 18.10"
date: 2019-03-24
forum: Networking &amp; Wireless
---

### Post by hmcosta on 2019-03-24
I installed ubuntu 18.10, but the wireless card does not work. The lspci command return:

[HTML]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Skylake GT2 [HD Graphics 520] (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 920MX] (rev a2)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5286 PCI Express Card Reader (rev 01)
02:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 06)

[/HTML]

What do I have to do to fix it?

---

### Post by overdrank on 2019-03-24
Hi and welcome, please refer to the [sticky__]("https://ubuntuforums.org/showthread.php?t=370108") in this sub-forum and post the out put from the script. Please follow the sticky &#128512;

---

### Post by praseodym on 2019-03-24
Please show
```

lsusb
lsmod
```

---

### Post by hmcosta on 2019-03-25
Results of pastebin:
[http://paste.ubuntu.com/p/BFcCF5BVKW/](http://paste.ubuntu.com/p/BFcCF5BVKW/)

Previously, it had recognized normally, until the pastebin points the network-controler. When I turn on the pc, sometimes the network works, sometimes it does not.

---

### Post by hmcosta on 2019-03-25
```
lsmod:

Module                  Size  Used by
cfg80211              663552  0
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_skl           102400  0
snd_soc_skl_ipc        61440  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_acpi           16384  1 snd_soc_skl
snd_soc_core          229376  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
asus_nb_wmi            28672  0
snd_pcm_dmaengine      16384  1 snd_soc_core
asus_wmi               28672  1 asus_nb_wmi
snd_hda_intel          40960  5
sparse_keymap          16384  1 asus_wmi
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             208896  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
nouveau              1875968  1
kvm                   622592  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
crc32_pclmul           16384  0
i915                 1740800  18
snd_timer              32768  2 snd_seq,snd_pcm
mxm_wmi                16384  1 nouveau
ghash_clmulni_intel    16384  0
pcbc                   16384  0
ttm                   106496  1 nouveau
joydev                 20480  0
aesni_intel           200704  2
rtsx_pci_ms            20480  0
aes_x86_64             20480  1 aesni_intel
uvcvideo               98304  0
crypto_simd            16384  1 aesni_intel
input_leds             16384  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
memstick               16384  1 rtsx_pci_ms
glue_helper            16384  1 aesni_intel
videobuf2_vmalloc      16384  1 uvcvideo
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd                    81920  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  45056  0
drm_kms_helper        172032  2 i915,nouveau
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
videobuf2_v4l2         24576  1 uvcvideo
btintel                20480  1 btusb
serio_raw              16384  0
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
soundcore              16384  1 snd
bluetooth             548864  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
drm                   458752  9 drm_kms_helper,i915,ttm,nouveau
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
i2c_algo_bit           16384  2 i915,nouveau
media                  40960  2 videodev,uvcvideo
ecdh_generic           24576  2 bluetooth
fb_sys_fops            16384  1 drm_kms_helper
processor_thermal_device    16384  0
hid_multitouch         20480  0
intel_pch_thermal      16384  0
syscopyarea            16384  1 drm_kms_helper
mei_me                 40960  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
idma64                 20480  0
mei                    98304  1 mei_me
virt_dma               16384  1 idma64
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
wmi                    24576  3 asus_wmi,mxm_wmi,nouveau
video                  45056  3 asus_wmi,i915,nouveau
mac_hid                16384  0
asus_wireless          16384  0
int3400_thermal        16384  0
acpi_pad              180224  0
acpi_thermal_rel       16384  1 int3400_thermal
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
rtsx_pci_sdmmc         24576  0
r8169                  86016  0
mii                    16384  1 r8169
ahci                   40960  2
libahci                32768  1 ahci
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
intel_lpss_pci         20480  0
i2c_hid                20480  0
intel_lpss             16384  1 intel_lpss_pci
hid                   126976  3 i2c_hid,hid_multitouch,hid_generic
```

```
lsusb:

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b721 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:57de Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by geestbos on 2019-03-29
Could it be that your WIFI card is disabled? Are there any related BIOS settings that you can check? And have you tried running a non-Ubuntu live Linux distribution with good network support (e.g. Knoppix)?

---

