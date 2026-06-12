---
title: "Problem with wireless in Xubuntu 14.04 with Lenovo G50-30"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by Nicolas_Castro on 2015-08-23
Hi everybody, i'm sorry posting about this problems as I know it has been asked before, but i can't solve mine. I have just installed Xubuntu and can't use the wireless. I have typed on the console:

lspci -nn | grep 0280
rfkill list all

and get:

Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

and the hard is blocked for the ideapad_wlan: Wireless LAN

Could I get some help? Thank you very much.

---

### Post by Hadaka on 2015-08-24
Hi, please run the wireless info text file
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
and also please post
```
rfkill list all
lsmod
```
thanks

---

### Post by Nicolas_Castro on 2015-08-25
Thank you very much. Here is what i got from rfkill list all:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

and lsmod:
Module                  Size  Used by
cfg80211              524288  0 
btrfs                 937984  0 
xor                    24576  1 btrfs
raid6_pq               98304  1 btrfs
ufs                    77824  0 
qnx4                   16384  0 
hfsplus               106496  0 
hfs                    57344  0 
minix                  36864  0 
ntfs                   98304  0 
msdos                  20480  0 
jfs                   188416  0 
xfs                   917504  0 
libcrc32c              16384  1 xfs
bnep                   20480  2 
rfcomm                 69632  4 
bluetooth             491520  10 bnep,rfcomm
snd_hda_codec_hdmi     53248  1 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
snd_hda_codec_conexant    24576  1 
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
v4l2_common            16384  1 videobuf2_core
rtsx_usb_ms            20480  0 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
memstick               20480  1 rtsx_usb_ms
media                  24576  2 uvcvideo,videodev
intel_rapl             20480  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm                   479232  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
cryptd                 20480  1 ghash_clmulni_intel
joydev                 20480  0 
bcma                   53248  0 
snd_hda_intel          32768  6 
snd_hda_controller     32768  1 snd_hda_intel
snd_intel_sst_acpi     16384  0 
i915                 1048576  3 
snd_intel_sst_core     73728  1 snd_intel_sst_acpi
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_soc_sst_mfld_platform    77824  1 snd_intel_sst_core
snd_hwdep              20480  1 snd_hda_codec
lpc_ich                24576  0 
shpchp                 40960  0 
serio_raw              16384  0 
snd_soc_rt5640         94208  0 
mei_txe                20480  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_compress           20480  1 snd_soc_core
mei                    90112  1 mei_txe
snd_pcm_dmaengine      16384  1 snd_soc_core
drm_kms_helper        126976  1 i915
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_hda_controller,snd_pcm_dmaengine
drm                   344064  5 i915,drm_kms_helper
snd_seq_midi           16384  0 
iosf_mbi               16384  1 intel_rapl
i2c_algo_bit           16384  1 i915
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
8250_fintek            16384  0 
video                  20480  1 i915
dw_dmac                16384  0 
dw_dmac_core           24576  1 dw_dmac
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
intel_smartconnect     16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
i2c_hid                20480  0 
snd                    86016  26 snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_seq_device,snd_compress
hid                   110592  1 i2c_hid
soundcore              16384  2 snd,snd_hda_codec
snd_soc_sst_acpi       16384  0 
i2c_designware_platform    16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
spi_pxa2xx_platform    24576  0 
rfkill_gpio            16384  0 
pwm_lpss_platform      16384  0 
8250_dw                16384  0 
pwm_lpss               16384  1 pwm_lpss_platform
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
psmouse               114688  0 
r8169                  81920  0 
ahci                   36864  2 
mii                    16384  1 r8169
libahci                32768  1 ahci
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi

Thank you!

---

### Post by Hadaka on 2015-08-25
Hi ,from a working wired connection please open a terminal ctrl/alt/t and COPY and paste...
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
then do..
```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then ..
```
sudo iw reg set AR
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
boot
thanks.

---

### Post by Nicolas_Castro on 2015-08-25
Thank you, thank you, thank you! And bless you, I'm replying through the wireless [-o

---

### Post by Hadaka on 2015-08-25
Excellent !, Happy to see that worked for you !

---

### Post by jeremy31 on 2015-08-25
```
sudo apt-get update && sudo apt-get dist-upgrade
``` and see if you can remove ideapad-laptop from the blacklist and reboot and have working wireless.  The source code I have from 3.19 shows the correct info in ideapad-laptop.c for rfkill on the G50-30 and it looks like the fix was added to 3.19.0-26 and your wireless-script results show you have 3.19.0-25

---

