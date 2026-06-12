---
title: "Wifi not working HP OMEN laptop"
date: 2019-03-12
forum: Networking &amp; Wireless
---

### Post by tyrz on 2019-03-12
just installed ubuntu alongside with windows.

Wifi was working in the test, but not now after installed.

[http://paste.ubuntu.com/p/cv6HkGNhyt/](http://paste.ubuntu.com/p/cv6HkGNhyt/)

---

### Post by kc1di on 2019-03-13
Try disabling bluetooth and see if it works.

---

### Post by tyrz on 2019-03-13
> **kc1di said:**
> Try disabling bluetooth and see if it works.

Not working ](*,)](*,)

---

### Post by wildmanne39 on 2019-03-13
Your wifi is hardblocked, which usually means it is turned off, turn it on with the switch or a key combination, if that does not help hopefully someone else will stop in to help, I am going to be away from my computer for several hours today.

---

### Post by jeremy31 on 2019-03-13
```
sudo apt remove bcmwl-kernel-source
```
Reboot and see if rfkill list still shows wifi blocked

---

### Post by tyrz on 2019-03-13
> **jeremy31 said:**
> ```
sudo apt remove bcmwl-kernel-source
```
Reboot and see if rfkill list still shows wifi blocked

It says that the app isn't installed

---

### Post by tyrz on 2019-03-13
> **wildmanne39 said:**
> Your wifi is hardblocked, which usually means it is turned off, turn it on with the switch or a key combination, if that does not help hopefully someone else will stop in to help, I am going to be away from my computer for several hours today.
I don't have any key that blocks my wifi, and in windows everything works fine

---

### Post by #&amp;thj^% on 2019-03-13
There must be a hardware switch. Check it. And also check in BIOS see if it is not disabled there. I see hard-block too.
Also this may help for someone to help:
```
ls -al /lib/firmware | grep 7265

```
paste back the return with code tags please.

---

### Post by jeremy31 on 2019-03-13
> **tyrz said:**
> It says that the app isn't installed

Well try ```
sudo apt remove broadcom-sta-common broadcom-sta-dkms
```
The script results showed that some broadcom driver was installed

---

### Post by kc1di on 2019-03-13
The wireless on/off key is the airplane mode key try pressing that it should turn the wireless card on/off. 
you may still need a driver for the card. 
Page 15 of the HP manual.  found [here.]("http://h10032.www1.hp.com/ctg/Manual/c05356862")

---

### Post by tyrz on 2019-03-13
> **kc1di said:**
> The wireless on/off key is the airplane mode key try pressing that it should turn the wireless card on/off. 
you may still need a driver for the card. 
Page 15 of the HP manual.  found [here.]("http://h10032.www1.hp.com/ctg/Manual/c05356862")

Yes the button it's there but when I press it nothing happens...
I found [this]("http://martinsosic.com/linux/2015/03/01/arch-linux-on-hp-omen.html") I am not sure if this will work tho, what you think?

---

### Post by tyrz on 2019-03-13
> **jeremy31 said:**
> Well try ```
sudo apt remove broadcom-sta-common broadcom-sta-dkms
```
The script results showed that some broadcom driver was installed

oh yes i don't know why it didn't work before, no I tried, but nothing changed.

---

### Post by tyrz on 2019-03-13
> **1fallen said:**
> There must be a hardware switch. Check it. And also check in BIOS see if it is not disabled there. I see hard-block too.
Also this may help for someone to help:
```
ls -al /lib/firmware | grep 7265

```
paste back the return with code tags please.

```
-rw-r--r--  1 root root  736844 Mar 30  2017 iwlwifi-7265-10.ucode
-rw-r--r--  1 root root  880604 Mar 30  2017 iwlwifi-7265-12.ucode
-rw-r--r--  1 root root  885224 Mar 30  2017 iwlwifi-7265-13.ucode
-rw-r--r--  1 root root 1180356 Mar 30  2017 iwlwifi-7265-16.ucode
-rw-r--r--  1 root root 1180412 Dec 14 12:54 iwlwifi-7265-17.ucode
-rw-r--r--  1 root root  690452 Mar 30  2017 iwlwifi-7265-8.ucode
-rw-r--r--  1 root root  697828 Mar 30  2017 iwlwifi-7265-9.ucode
lrwxrwxrwx  1 root root      21 Mar 12 12:44 iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r--  1 root root 1002800 Mar 30  2017 iwlwifi-7265D-12.ucode
-rw-r--r--  1 root root 1008692 Mar 30  2017 iwlwifi-7265D-13.ucode
-rw-r--r--  1 root root 1384500 Mar 30  2017 iwlwifi-7265D-16.ucode
-rw-r--r--  1 root root 1383604 Nov 17  2017 iwlwifi-7265D-17.ucode
-rw-r--r--  1 root root 1385368 Nov 17  2017 iwlwifi-7265D-21.ucode
-rw-r--r--  1 root root 1028376 Apr 24  2018 iwlwifi-7265D-22.ucode
-rw-r--r--  1 root root 1032740 Dec  5  2017 iwlwifi-7265D-27.ucode
-rw-r--r--  1 root root 1036432 May 18  2018 iwlwifi-7265D-29.ucode


```

---

### Post by tyrz on 2019-03-14
any solutions? :(

---

### Post by mc4man on 2019-03-14
> **tyrz said:**
> Yes the button it's there but when I press it nothing happens...

 did you press it while holding down fn button?

---

### Post by kc1di on 2019-03-15
What is the output of ```
rfkill list
``` and ```
lsmod
```

---

### Post by tyrz on 2019-03-15
> **mc4man said:**
> did you press it while holding down fn button?

yes

---

### Post by tyrz on 2019-03-15
> **kc1di said:**
> What is the output of ```
rfkill list
``` and ```
lsmod
```

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

```
 
Module                  Size  Used by
rfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
nls_iso8859_1          16384  1
rndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
arc4                   16384  2
iwlmvm                376832  0
mac80211              802816  1 iwlmvm
iwlwifi               299008  1 iwlmvm
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             208896  0
kvm                   626688  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
rtsx_pci_ms            20480  0
aesni_intel           200704  2
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
uvcvideo               94208  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  40960  2 videodev,uvcvideo
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
joydev                 24576  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
i915                 1740800  22
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
input_leds             16384  0
mac_hid                16384  0
serio_raw              16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                20480  1 btusb
bluetooth             552960  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  2 bluetooth
video                  45056  1 i915
ttm                   110592  0
snd_timer              32768  2 snd_seq,snd_pcm
drm_kms_helper        172032  1 i915
memstick               16384  1 rtsx_pci_ms
drm                   458752  16 drm_kms_helper,i915,ttm
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
cfg80211              667648  3 iwlmvm,iwlwifi,mac80211
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
mei_me                 40960  0
mei                    98304  1 mei_me
processor_thermal_device    16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 usbhid,hid_generic
rtsx_pci_sdmmc         24576  0
psmouse               151552  0
r8169                  86016  0
mii                    16384  2 r8169,usbnet
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
ahci                   40960  4
libahci                32768  1 ahci




```

---

### Post by kc1di on 2019-03-16
is there any setting in bios that may turn wireless on or off?  

your wireless is still hard lock by something in the machine. 
You can try issuing the following command and see if it turns it on, but I doubt it. ```
sudo rfkill unblock all
```

---

### Post by praseodym on 2019-03-16
What about
```

sudo modprobe -v hp_wmi wireless=1
sudo rfkill unblock all
rfkill list
iwconfig
```

---

