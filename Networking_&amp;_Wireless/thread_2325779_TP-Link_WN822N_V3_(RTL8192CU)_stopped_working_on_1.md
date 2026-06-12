---
title: "TP-Link WN822N V3 (RTL8192CU) stopped working on 14.04 LTS after minor core update"
date: 2016-05-25
forum: Networking &amp; Wireless
---

### Post by han2 on 2016-05-25
After an automatic Xubuntu core update, the wifi network stopped working completely. It's not even showing the wifi indicator, and the green light in the TP-Link is always off.

In the past, I made it work properly using the following drivers and installation instructions: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I tried removing the native drivers from the blacklist, and removing and installing again the dkms module, but nothing changed.

I tried *modprobe -r 8192cu* and *modprobe 8192cu*, again with no results.

Any suggestion would be deeply appreciated.

lsusb

```
han@han-xubuntu:~$ lsusb
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 004: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 003 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod

```
han@han-xubuntu:~$ lsmod
Module                  Size  Used by
8192cu                528384  0 
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               446464  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69632  4 
bnep                   20480  2 
bluetooth             512000  10 bnep,rfcomm
snd_ice1712            77824  2 
snd_cs8427             16384  1 snd_ice1712
snd_i2c                16384  2 snd_ice1712,snd_cs8427
nouveau              1368064  3 
snd_ice17xx_ak4xxx     16384  1 snd_ice1712
intel_rapl             20480  0 
snd_hda_codec_hdmi     49152  1 
snd_hda_codec_realtek    86016  1 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       16384  0 
coretemp               16384  0 
mac80211              741376  0 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm_intel             167936  0 
cfg80211              552960  1 mac80211
snd_ak4xxx_adda        20480  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_hda_intel          36864  5 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
kvm                   512000  1 kvm_intel
snd_mpu401_uart        16384  1 snd_ice1712
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_ac97_codec        131072  1 snd_ice1712
input_leds             16384  0 
ac97_bus               16384  1 snd_ac97_codec
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  6 snd_ice1712,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
joydev                 20480  0 
snd_seq_midi           16384  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
ttm                    94208  1 nouveau
snd_seq_midi_event     16384  1 snd_seq_midi
crct10dif_pclmul       16384  0 
snd_rawmidi            32768  2 snd_mpu401_uart,snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper        126976  1 nouveau
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   360448  6 ttm,drm_kms_helper,nouveau
crc32_pclmul           16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  31 snd_ice1712,snd_hda_codec_realtek,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs8427
aesni_intel           167936  0 
parport_pc             32768  0 
aes_x86_64             20480  1 aesni_intel
mei_me                 36864  0 
lrw                    16384  1 aesni_intel
i2c_algo_bit           16384  1 nouveau
ppdev                  20480  0 
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
tpm_infineon           20480  0 
serio_raw              16384  0 
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
lp                     20480  0 
mei                    98304  1 mei_me
soundcore              16384  1 snd
ie31200_edac           16384  0 
lpc_ich                24576  0 
shpchp                 36864  0 
edac_core              53248  1 ie31200_edac
8250_fintek            16384  0 
mac_hid                16384  0 
parport                49152  3 lp,ppdev,parport_pc
video                  40960  1 nouveau
hid_generic            16384  0 
usbhid                 49152  0 
hid                   118784  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            69632  1 uas
psmouse               126976  0 
ahci                   36864  2 
alx                    36864  0 
libahci                32768  1 ahci
mdio                   16384  1 alx
```

iwconfig

```
han@han-xubuntu:~$ iwconfig
eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.
```

---

### Post by praseodym on 2016-05-25
Please check
```
sudo dkms autoinstall
dkms status
dmesg | grep 8192
```

---

### Post by han2 on 2016-05-25
Thanks praseodym.

```
han@han-xubuntu:~$ dkms status
8192cu, 1.10, 3.13.0-85-generic, x86_64: installed
8192cu, 1.10, 3.13.0-86-generic, x86_64: installed
8192cu, 1.10, 4.2.0-27-generic, x86_64: installed
8192cu, 1.10, 4.2.0-30-generic, x86_64: installed
8192cu, 1.10, 4.2.0-35-generic, x86_64: installed
8192cu, 1.10, 4.2.0-36-generic, x86_64: installed
vboxhost, 5.0.16, 3.13.0-86-generic, x86_64: installed
vboxhost, 5.0.16, 4.2.0-35-generic, x86_64: installed
vboxhost, 5.0.16, 4.2.0-36-generic, x86_64: installed
```

```
han@han-xubuntu:~$ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88021ec00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[   15.782511] 8192cu: module verification failed: signature and/or required key missing - tainting kernel
[   15.831833] usbcore: registered new interface driver rtl8192cu
```

I also did a normal dmesg and saw some errors related to network-manager.

```
han@han-xubuntu:~$ dmesg | grep network-manager
[   17.121609] init: network-manager main process (929) killed by SEGV signal
[   17.121617] init: network-manager main process ended, respawning
[   17.127141] init: network-manager main process (938) killed by SEGV signal
[   17.127148] init: network-manager main process ended, respawning
[   17.132142] init: network-manager main process (942) killed by SEGV signal
[   17.132149] init: network-manager main process ended, respawning
[   17.137255] init: network-manager main process (946) killed by SEGV signal
[   17.137263] init: network-manager main process ended, respawning
[   17.142643] init: network-manager main process (953) killed by SEGV signal
[   17.142650] init: network-manager main process ended, respawning
[   17.147932] init: network-manager main process (961) killed by SEGV signal
[   17.147942] init: network-manager main process ended, respawning
[   17.153703] init: network-manager main process (969) killed by SEGV signal
[   17.153710] init: network-manager main process ended, respawning
[   17.159182] init: network-manager main process (973) killed by SEGV signal
[   17.159188] init: network-manager main process ended, respawning
[   17.164760] init: network-manager main process (977) killed by SEGV signal
[   17.164766] init: network-manager main process ended, respawning
[   17.169979] init: network-manager main process (981) killed by SEGV signal
[   17.169985] init: network-manager main process ended, respawning
[   17.175184] init: network-manager main process (985) killed by SEGV signal
[   17.175191] init: network-manager respawning too fast, stopped
```

---

### Post by praseodym on 2016-05-25
Does it work with kernel 3.13? Or an earlier kernel 4.x?

---

### Post by han2 on 2016-05-26
Tried to boot with all the earlier kernels (until 4.2.0-27, the oldest I have available), and the same thing happened. 

However, after trying that, the first time I booted with 4.2.0-36 an error window jumped, with some info about network-manager.

[http://i.imgur.com/I7FP3Iq.png](http://i.imgur.com/I7FP3Iq.png)

---

