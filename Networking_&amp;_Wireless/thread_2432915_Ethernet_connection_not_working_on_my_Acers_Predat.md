---
title: "Ethernet connection not working on my Acers Predator"
date: 2019-12-10
forum: Networking &amp; Wireless
---

### Post by Nicolas_Castro on 2019-12-10
Hi all, I have a couple of Acer Predator with Ubuntu 16 installed on them and I can't make the ethernet connection work. Here are a couple of command-line outputs:

>  ~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless-AC 9560 [Jefferson Peak]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 10
       serial: a8:6d:aa:e7:ca:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-72-generic firmware=34.0.0 ip=192.168.68.114 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:c2418000-c241bfff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:40:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c2200000-c220ffff memory:c2280000-c2283fff memory:c2210000-c227ffff memory:c2284000-c229ffff

also 
>  lspci -nnk | grep -e 0200 -A2
40:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:3000] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:132d]


and for my kernel version

> ~$ uname -r
4.15.0-72-generic

Pls I will appreciate any help as this issue is driving me nuts. Cheers

Nico.

---

### Post by praseodym on 2019-12-11
Please show
```

lspci -nnk | grep -iA2 net
lsmod
dmesg | grep r8
```

---

### Post by chili555 on 2019-12-11
I suggest that you try this: [https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/Howto/Realtek-r8125/&prev=search](https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/Howto/Realtek-r8125/&prev=search)

---

### Post by Nicolas_Castro on 2019-12-11
Here it goes: 




>  lspci -nnk | grep -iA2 net
00:14.3 Network controller [0280]: Intel Corporation Wireless-AC 9560 [Jefferson Peak] [8086:a370] (rev 10)
	Subsystem: Bigfoot Networks, Inc. Device [1a56:1552]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
--
40:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:3000] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:132d]

>  lsmod
Module                  Size  Used by
hid_generic            16384  0
usbhid                 53248  0
nvidia_uvm            802816  0
rfcomm                 77824  2
ccm                    20480  3
snd_hda_codec_hdmi     49152  1
bnep                   20480  2
arc4                   16384  2
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
nvidia_drm             45056  3
nvidia_modeset       1093632  5 nvidia_drm
joydev                 24576  0
hid_multitouch         20480  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
iwlmvm                368640  0
kvm_intel             217088  0
snd_hda_intel          45056  5
nvidia              18194432  200 nvidia_uvm,nvidia_modeset
kvm                   610304  1 kvm_intel
mac80211              786432  1 iwlmvm
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
uvcvideo               86016  0
drm_kms_helper        172032  1 nvidia_drm
snd_seq_midi           16384  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
drm                   401408  6 drm_kms_helper,nvidia_drm
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           188416  2
btusb                  45056  0
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
aes_x86_64             20480  1 aesni_intel
btrtl                  16384  1 btusb
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
ipmi_devintf           20480  0
btbcm                  16384  1 btusb
videodev              188416  3 videobuf2_core,videobuf2_v4l2,uvcvideo
iwlwifi               290816  1 iwlmvm
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
btintel                16384  1 btusb
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
intel_cstate           20480  0
fb_sys_fops            16384  1 drm_kms_helper
idma64                 20480  0
syscopyarea            16384  1 drm_kms_helper
virt_dma               16384  1 idma64
media                  40960  2 videodev,uvcvideo
snd_timer              32768  2 snd_seq,snd_pcm
bluetooth             552960  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
intel_rapl_perf        16384  0
serio_raw              16384  0
sysfillrect            16384  1 drm_kms_helper
cfg80211              630784  3 iwlmvm,iwlwifi,mac80211
acer_wmi               20480  0
snd                    81920  21 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
intel_wmi_thunderbolt    16384  0
sysimgblt              16384  1 drm_kms_helper
sparse_keymap          16384  1 acer_wmi
ecdh_generic           24576  1 bluetooth
wmi_bmof               16384  0
mei_me                 40960  0
ucsi_acpi              16384  0
intel_lpss_pci         20480  0
soundcore              16384  1 snd
typec_ucsi             28672  1 ucsi_acpi
processor_thermal_device    16384  0
typec                  24576  1 typec_ucsi
intel_lpss             16384  1 intel_lpss_pci
mei                    94208  1 mei_me
intel_soc_dts_iosf     16384  1 processor_thermal_device
shpchp                 36864  0
intel_pch_thermal      16384  0
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
acpi_pad              180224  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
autofs4                40960  2
nvme                   36864  0
nvme_core              61440  5 nvme
i2c_hid                24576  0
hid                   114688  4 i2c_hid,usbhid,hid_multitouch,hid_generic
wmi                    24576  3 intel_wmi_thunderbolt,acer_wmi,wmi_bmof
video                  45056  1 acer_wmi

and
>  dmesg | grep r8
[    0.000000] percpu: Embedded 45 pages/cpu s147456 r8192 d28672 u262144
[    0.000000] pcpu-alloc: s147456 r8192 d28672 u262144 alloc=1*2097152

Thanks for the help.

---

### Post by Nicolas_Castro on 2019-12-11
> I suggest that you try this: [https://translate.google.com/transla...5/&prev=search]("https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/Howto/Realtek-r8125/&prev=search")

Do you reckon it'll work even mine is r8192? Cheers.

---

### Post by chili555 on 2019-12-11
It says: > For current 2.5G cards with the chipsets 10EC: 8125 and [COLOR="#FF0000"]10EC: 3000[/COLOR] , the module can be subsequently installed via this HowTo. And you have:>  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [[COLOR="#FF0000"]10ec:3000[/COLOR]] (rev 03)So I reckon so.

I don't have the card nor a 2.5 gHz connection, so I have no way to test, but I'd think so. I'm sure that praseodym will assist us if needed.

---

### Post by Nicolas_Castro on 2019-12-11
>  			 				[INDENT] 					I suggest that you try this: [https://translate.google.com/transla...5/&prev=search]("https://translate.google.com/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/Howto/Realtek-r8125/&prev=search") 				[/INDENT] 			
  			   		
 			 				 			 			 				

It worked, thanks again!

---

### Post by chili555 on 2019-12-11
> **Nicolas_Castro said:**
> It worked, thanks again!Awesome! Please use thread tools to mark Solved. The searchers will appreciate it.

---

### Post by praseodym on 2019-12-14
> **chili555 said:**
> ...I'm sure that praseodym will assist us if needed.

Glad it worked :)

---

