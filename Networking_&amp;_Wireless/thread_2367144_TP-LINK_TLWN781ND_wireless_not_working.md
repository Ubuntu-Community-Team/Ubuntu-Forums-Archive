---
title: "TP-LINK TLWN781ND wireless not working"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by bagasghufronalfaiz on 2017-07-26
I just installed ubuntu on a desktop computer, but there was a wireless problem that did not show up.


I tried to figure out the solution and found some solutions but did not work on the problems I was facing.
I have tried several solutions, like, [https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04#_=_](https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04#_=_) and [https://ubuntuforums.org/showthread.php?t=1857808&page=6](https://ubuntuforums.org/showthread.php?t=1857808&page=6) , but it didn't work on me.

I installed ubuntu 16.04, the wireless hardware I use is TP-LINK TL-WN781ND.

maybe this information can help.

lshw :
```

[FONT=monospace][COLOR=#000000]-network UNCLAIMED[/COLOR]
 description: Network controller
 product: AR9485 Wireless Network Adapter
 vendor: Qualcomm Atheros
 physical id: 0
 bus info: pci@0000:09:00.0
 version: 01
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress cap_list
 configuration: latency=0
 resources: memory:fd200000-fd27ffff memory:fd280000-fd28ffff
[/FONT]
```


iwconfig :
```

[FONT=monospace][COLOR=#000000]enp3s0    no wireless extensions.[/COLOR]

lo        no wireless extensions.
[/FONT]
```

lspci -nnk | grep -iA2 net :
```

[FONT=monospace][COLOR=#000000]03:00.0 Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10[/COLOR]
ec:8168] (rev 16)
        Subsystem: Biostar Microtech Int'l Corp RTL8111/8168/8411 PCI Express Gigabit Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [1565:2313][/COLOR]
        Kernel driver in use: r8169
        Kernel modules: r8169
[COLOR=#18B2B2]--[/COLOR]
09:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Qualcomm Atheros AR9485 Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [168c:0032] (rev 01)[/COLOR]
        Subsystem: Qualcomm Atheros AR9485 Wireless [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [168c:3118][/COLOR]
        Kernel modules: ath9k
11:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device [1022:145a]
[/FONT]
```

dmesg | grep ath :
```

[COLOR=#000000][FONT=monospace][   11.345486] [/FONT][/COLOR][COLOR=#FF5454][FONT=monospace]**ath**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]: EEPROM regdomain: 0x21 [/FONT][/COLOR]
[FONT=monospace][   11.345486] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: EEPROM indicates we should expect a direct regpair map[/COLOR]
[   11.345487] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Country alpha2 being used: AU[/COLOR]
[   11.345487] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Regpair used: 0x21[/COLOR]
[   11.345511] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: phy0: dma_mapping_error() on RX init[/COLOR]
[   11.345555] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k 0000:09:00.0: Failed to initialize device[/COLOR]
[   11.345601] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k: probe of 0000:09:00.0 failed with error -12[/COLOR]
[   11.347868] usbcore: registered new interface driver [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k_htc[/COLOR]
[  700.467251] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k: [/COLOR][COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k: Driver unloaded[/COLOR]
[  720.519444] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: EEPROM regdomain: 0x21[/COLOR]
[  720.519445] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: EEPROM indicates we should expect a direct regpair map[/COLOR]
[  720.519446] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Country alpha2 being used: AU[/COLOR]
[  720.519447] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Regpair used: 0x21[/COLOR]
[  720.519484] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: phy1: dma_mapping_error() on RX init[/COLOR]
[  720.519512] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k 0000:09:00.0: Failed to initialize device[/COLOR]
[  720.519564] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k: probe of 0000:09:00.0 failed with error -12[/COLOR]
[/FONT]
```

lsmod :
```

[FONT=monospace][COLOR=#000000]Module                  Size  Used by[/COLOR]
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
nvidia_uvm            647168  0
edac_mce_amd           28672  0
edac_core              53248  0
kvm                   593920  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
input_leds             16384  0
crc32_pclmul           16384  0
joydev                 20480  0
ghash_clmulni_intel    16384  0
aziokbd                16384  0
pcbc                   16384  0
nvidia_drm             45056  1
nvidia_modeset        790528  7 nvidia_drm
nvidia              12304384  206 nvidia_modeset,nvidia_uvm
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_intel          36864  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
serio_raw              16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
i2c_piix4              24576  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper        151552  1 nvidia_drm
snd_timer              32768  2 snd_seq,snd_pcm
drm                   352256  4 nvidia_drm,drm_kms_helper
snd                    77824  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_c
odec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ccp                    57344  0
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
wmi                    16384  0
shpchp                 36864  0
tpm_crb                16384  0
i2c_designware_platform    16384  0
mac_hid                16384  0
8250_dw                16384  0
i2c_designware_core    20480  1 i2c_designware_platform
ath9k_htc              77824  0
ath9k                 147456  0
ath9k_common           36864  2 ath9k_htc,ath9k
ath9k_hw              466944  3 ath9k_htc,ath9k,ath9k_common
ath                    28672  4 ath9k_htc,ath9k_hw,ath9k,ath9k_common
mac80211              782336  2 ath9k_htc,ath9k
cfg80211              602112  5 ath9k_htc,mac80211,ath9k,ath,ath9k_common
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
btrfs                1089536  0
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
hid_holtek_mouse       16384  0
usbhid                 53248  0
hid                   118784  2 hid_holtek_mouse,usbhid
r8169                  81920  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
gpio_amdpt             16384  0
fjes                   77824  0
gpio_generic           16384  1 gpio_amdpt
[/FONT]
```
Can someone help me, please

---

### Post by johndough2 on 2017-07-27
Hi

Could you please refer to the sticky post 

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

and post the results of 

[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

---

### Post by chili555 on 2017-07-27
> [  720.519484] ath: phy1: dma_mapping_error() on RX init
[  720.519512] ath9k 0000:09:00.0: Failed to initialize device
[  720.519564] ath9k: probe of 0000:09:00.0 failed with error -12If you Google these messages, there are dozens of hits and no real solutions. I suggest that you make certain that the card is correctly seated in its slot. If that doesn't help, try a different PCI slot. you might also reset the BIOS to default.

If none of these are effective, then I'm unaware of further steps you might try.

---

### Post by praseodym on 2017-07-28
You could try the boot options 

```
acpi=force pnpbios=off pci=acpi acpi_irq_nobalance irqpoll
```
or
```
pnpbios=off acpi=force irqpoll acpi_irq_nobalance
```
or
```
pnpbios=off acpi=force irqpoll pci=acpi
```
or
```
pnpbios=off acpi=force irqpoll
```
or
```
acpi=force irqpoll
```
From here:
[https://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507](https://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507)

---

