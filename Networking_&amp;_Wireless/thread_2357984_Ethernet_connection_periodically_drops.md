---
title: "Ethernet connection periodically drops"
date: 2017-04-08
forum: Networking &amp; Wireless
---

### Post by wallacegalloway on 2017-04-08
About twice a day my Ethernet connection drops on UbuntuGnome16.04. I go to wired connection; disconnect and reconnect and everything is fine again for several hours. Mild but annoying.

---

### Post by ajgreeny on 2017-04-08
*Thread moved to **Networking & Wireless**.* which is more appropriate and a better fit for your problem.

---

### Post by praseodym on 2017-04-09
Which hardware is it?
```

lspci -nnk
lsmod
```

---

### Post by wallacegalloway on 2017-04-10
```
desktop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
    Subsystem: ASRock Incorporation 4th Gen Core Processor DRAM Controller [1849:0c00]
    Kernel driver in use: hsw_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family USB xHCI [1849:8c31]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family MEI Controller [1849:8c3a]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: ASRock Incorporation Ethernet Connection I217-V [1849:153b]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family USB EHCI [1849:8c2d]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset High Definition Audio Controller [1849:8892]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d5)
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family USB EHCI [1849:8c26]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
    Subsystem: ASRock Incorporation Z87 Express LPC Controller [1849:8c44]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [1849:8c02]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset Family SMBus Controller [1849:8c22]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
    Subsystem: ZOTAC International (MCO) Ltd. GM107 [GeForce GTX 750 Ti] [19da:288a]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:288a]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)
```

lsmod
```
Module                  Size  Used by
snd_hda_codec_hdmi     53248  1
nvidia_uvm            647168  0
input_leds             16384  0
intel_rapl             20480  0
uvcvideo               90112  0
x86_pkg_temp_thermal    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
intel_powerclamp       16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
coretemp               16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
kvm_intel             172032  0
snd_usb_audio         176128  1
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
kvm                   544768  1 kvm_intel
snd_usbmidi_lib        36864  1 snd_usb_audio
media                  24576  2 uvcvideo,videodev
snd_hda_intel          40960  7
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
irqbypass              16384  1 kvm
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_pcm               106496  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
ghash_clmulni_intel    16384  0
snd_seq_midi           16384  0
aesni_intel           167936  0
snd_seq_midi_event     16384  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
lrw                    16384  1 aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  28 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
soundcore              16384  1 snd
mei_me                 36864  0
shpchp                 36864  0
lpc_ich                24576  0
mei                    98304  1 mei_me
8250_fintek            16384  0
soc_button_array       16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
nvidia_drm             53248  1
nvidia_modeset        790528  4 nvidia_drm
nvidia              12144640  60 nvidia_modeset,nvidia_uvm
drm_kms_helper        155648  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  4 drm_kms_helper,nvidia_drm
e1000e                237568  0
ahci                   36864  3
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
psmouse               131072  0
fjes                   28672  0
video                  40960  0
```

---

