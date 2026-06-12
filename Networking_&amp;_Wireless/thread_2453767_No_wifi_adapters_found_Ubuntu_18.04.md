---
title: "No wifi adapters found Ubuntu 18.04"
date: 2020-11-16
forum: Networking &amp; Wireless
---

### Post by avatarhzh on 2020-11-16
I dual booted Ubuntu on a laptop I bought recently and it says there's no wifi adapters found. Here are the following outputs from the terminal:

```
sudo lshw -c net
  *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:c2300000-c2303fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:0d:00.1
       logical name: enp13s0f1
       version: 12
       serial: 80:fa:5b:85:1f:b9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.20.116 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:3000(size=256) memory:c2204000-c2204fff memory:c2200000-c2203fff

```

I've tried to git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git) to fix this but it doesn't work.

```
sudo lsmod
Module                  Size  Used by
bnep                   20480  2
snd_hda_codec_hdmi     49152  2
nls_iso8859_1          16384  1
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_codec_realtek    94208  1
coretemp               16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm_intel             204800  0
kvm                   593920  1 kvm_intel
snd_hda_intel          40960  4
irqbypass              16384  1 kvm
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq_midi           16384  0
videobuf2_v4l2         24576  1 uvcvideo
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
btusb                  45056  0
aesni_intel           188416  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
crypto_simd            16384  1 aesni_intel
btintel                16384  1 btusb
glue_helper            16384  1 aesni_intel
joydev                 24576  0
input_leds             16384  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
intel_wmi_thunderbolt    16384  0
media                  40960  2 uvcvideo,videodev
bluetooth             548864  11 btrtl,btintel,bnep,btbcm,btusb
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
rtsx_pci_ms            20480  0
snd                    81920  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
memstick               16384  1 rtsx_pci_ms
ecdh_generic           24576  1 bluetooth
soundcore              16384  1 snd
shpchp                 36864  0
tpm_crb                16384  0
intel_hid              16384  0
acpi_pad              180224  0
mac_hid                16384  0
sparse_keymap          16384  1 intel_hid
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
nouveau              1716224  0
rtsx_pci_sdmmc         24576  0
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
psmouse               147456  0
ttm                   106496  1 nouveau
drm_kms_helper        172032  1 nouveau
nvme                   32768  0
r8169                  86016  0
syscopyarea            16384  1 drm_kms_helper
ahci                   36864  0
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
sysfillrect            16384  1 drm_kms_helper
mii                    16384  1 r8169
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme_core              61440  5 nvme
libahci                32768  1 ahci
drm                   401408  3 nouveau,ttm,drm_kms_helper
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
wmi                    24576  3 intel_wmi_thunderbolt,mxm_wmi,nouveau
video                  45056  1 nouveau
```

It'd be great if someone can help me with this issue

```
lspci -nnk | grep -iA2 net
0c:00.0 Network controller [0280]: Intel Corporation Device [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Device [8086:0084]
0d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)
--
0d:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:8520]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by jeremy31 on 2020-11-16
Try Ubuntu 20.04 as the wifi should be supported

---

### Post by DuckHook on 2020-11-16
Hello avatarhzh,

Please use the default fonts and styles when posting. Unusual fonts and styles are difficult to read for those on small screens or with compromised eyesight. Thanks!

---

### Post by grahammechanical on 2020-11-16
If this laptop has Microsoft Windows installed and WiFi is switched off in Windows then when Ubuntu loads WiFi does not get switched on. Also, a laptop might used a combination of key presses to switch WiFi on & off to reduce battery usage. You might need to check the BIOS/UEFI settings utility to make sure that WiFi is switched on. Run this command

```
rfkill list
```

If the printout says Soft blocked: yes then WiFi is switched off in software and a driver may be required. If the printout says Hard blocked: yes  then the WiFi adapter is not switched on.

Regards.


Regards

---

