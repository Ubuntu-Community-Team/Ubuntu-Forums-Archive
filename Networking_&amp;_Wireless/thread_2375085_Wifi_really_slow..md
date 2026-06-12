---
title: "Wifi really slow."
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by tuan1991 on 2017-10-21
Hi all, i just got ubuntu 17.10 (never used Ubuntu before) and the Internet is really slow compairing to Windows (about 20% and unstable) . Can somebody help me ? I guess its a driver problem:

my lsmod :
```
Module                  Size  Used by
rtl8xxxu              126976  0
rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
eeprom_93cx6           16384  1 rt2800pci
ccm                    20480  6
arc4                   16384  2
nls_iso8859_1          16384  1
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
rt2800lib             114688  3 rt2800mmio,rt2800usb,rt2800pci
rt2x00lib              53248  7 rt2800lib,rt2x00pci,rt2800mmio,rt2800usb,rt2x00usb,rt2x00mmio,rt2800pci
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
edac_mce_amd           28672  0
mac80211              778240  5 rt2800lib,rt2x00pci,rt2x00lib,rt2x00usb,rtl8xxxu
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
kvm                   581632  0
cfg80211              610304  2 rt2x00lib,mac80211
input_leds             16384  0
joydev                 20480  0
irqbypass              16384  1 kvm
snd                    81920  27 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ccp                    73728  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  4
eeepc_wmi              16384  0
aes_x86_64             20480  1 aesni_intel
asus_wmi               28672  1 eeepc_wmi
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
sparse_keymap          16384  1 asus_wmi
shpchp                 36864  0
i2c_piix4              24576  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
video                  40960  1 asus_wmi
wmi_bmof               16384  0
8250_dw                16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
amdgpu               2007040  31
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
drm_kms_helper        167936  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   356352  27 amdgpu,ttm,drm_kms_helper
r8169                  81920  0
ahci                   36864  2
mii                    16384  1 r8169
libahci                32768  1 ahci
wmi                    24576  2 asus_wmi,wmi_bmof
gpio_amdpt             16384  0
gpio_generic           16384  1 gpio_amdpt
```


my " sudo lshw -C network" : 


```
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:1e:00.0
       logical name: enp30s0
       version: 15
       serial: 88:d7:f6:40:30:13
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:296 ioport:f000(size=256) memory:fe604000-fe604fff memory:fe600000-fe603fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:9
       logical name: wlx98ded0088d44
       serial: 98:de:d0:08:8d:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.13.0-16-generic firmware=N/A ip=192.168.1.7 link=yes multicast=yes wireless=IEEE 802.11
```



THANKS for any help !

---

### Post by praseodym on 2017-10-22
Lets see which device you have because it loads 2 drivers:
```

lsusb
```

---

### Post by tuan1991 on 2017-10-22
Hi, thanks for your reply, i have BOTH of those devices because i figured there was a problem with the adapter. Is having 2 drivers messing with my adapter ? , how can i remove it ?

---

### Post by praseodym on 2017-10-22
Which one causes trouble?

---

