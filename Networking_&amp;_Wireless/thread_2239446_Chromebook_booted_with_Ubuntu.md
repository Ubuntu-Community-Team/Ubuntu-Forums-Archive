---
title: "Chromebook booted with Ubuntu"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by hayden4 on 2014-08-13
I'm just booted Ubuntu 14.04 on my Chromebook. When I realized the i couldn't connect to any wireless networks, I did some research. A lot of people were saying that sometimes you need to download additional drivers for your wireless card, but it can't, because you can't connect to the internet in order to download those drivers. So you need to connect via Ethernet. Well, Chromebooks don't have Ethernet ports. So I went out and got a USB to Ethernet adapter, and it works like a charm. But, when I got to looking for additional drivers, it tells me nothing could be found. Can anyone help?

---

### Post by Hadaka on 2014-08-13
Hi,with your ethernet/usb connected to the internet please do.
```
sudo apt-get update
sudo apt-get upgrade
```
remove the ethernet/usb adapter and boot
*If it does not connect please post the output of.
```
lsusb
rfkill list all
lsmod
```
thanks

---

### Post by hayden4 on 2014-08-14
Thanks for the quick reply. The update and upgrade didn't work though...

Here's the output

**lsusb**
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

**lsmod**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
user@chrubuntu:~$ lsmod
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
cyapa                  13132  0 
gpio_ich               13476  0 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13435  0 
kvm_intel             143060  0 
snd_rawmidi            30144  1 snd_seq_midi
chromeos_laptop        14148  0 
kvm                   451511  1 kvm_intel
arc4                   12608  2 
ath9k                 164164  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
bnep                   19624  2 
rfcomm                 69160  8 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  783805  5 
serio_raw              13462  0 
videodev              134688  2 uvcvideo,videobuf2_core
mac80211              630653  1 ath9k
lpc_ich                21080  0 
ath3k                  13318  0 
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 ath,ath9k,mac80211
btusb                  32412  0 
bluetooth             391196  23 bnep,ath3k,btusb,rfcomm
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
tpm_infineon           17372  0 
mac_hid                13205  0 
video                  19476  1 i915
i2c_designware_pci     13135  0 
i2c_designware_core    14768  1 i2c_designware_pci
drm_kms_helper         53081  1 i915
soundcore              12680  1 snd
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  1 
libahci                32560  1 ahci

---

### Post by Hadaka on 2014-08-14
try the commands in post #4
[http://ubuntuforums.org/showthread.php?t=2161506](http://ubuntuforums.org/showthread.php?t=2161506)

---

### Post by hayden4 on 2014-08-14
I saw this post earlier, and tried his fix. All the inputs work, accept the last one.

When I input 
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]sudo iwconfig wlan0 power off

My output is

Error for wireless request "Set Power Management" (8B2C)
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Power Management" (8B2C)
    SET failed on device wlan0 ; Operation not supported.

---

### Post by Hadaka on 2014-08-14
hi, make sure you do not have your ethernet/usb adapter pluged in
for those last commands, and please post the output of..
```
iwconfig
```
thanks.

---

### Post by hayden4 on 2014-08-14
Yes, I made sure the Ethernet adapter was unplugged.

The output returned:

lo 		no wireless extentions.


wlan0		IEEE 802.11abgn ESSID:off/any
		Mode:Managed Access Point: Not-Associated Tx-Power=16 dBm
		Retry long limit:7 RTS thr:off
		Power Management:off

---

### Post by hayden4 on 2014-08-14
Sorry about the smiley faces. xD

---

### Post by hayden4 on 2014-08-14
-bump-

---

