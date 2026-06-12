---
title: "New linux user coming from windows trying to get wi-fi working"
date: 2020-03-09
forum: Networking &amp; Wireless
---

### Post by vanhooserb on 2020-03-09
Hi there, I just recently tried to revitalize my old laptop by installing Ubuntu and so far it's been pretty cool, but I can't seem to get the wi-fi to work. I tried to use the common steps when searching for "No wi-fi adapter found issue Ubuntu 18.04" which included cloning a git repo and installing dkms to build it, but that didn't seem to make a difference. After bailing on trying to get the built in adapter to work, I purchased a usb wi-fi adapter ([https://www.amazon.com/gp/product/B00JDVRCI0/ref=ask_ql_qh_dp_hza](https://www.amazon.com/gp/product/B00JDVRCI0/ref=ask_ql_qh_dp_hza)) which advertised its PnP with linux. Coming from Windows, that means literally plugging it in, waiting a few seconds, and then using the device. I'm not sure of what the typical steps are to get this working in a linux environment. I tried following a few posts on here ([https://ubuntuforums.org/showthread.php?t=2360710](https://ubuntuforums.org/showthread.php?t=2360710), [https://ubuntuforums.org/showthread.php?t=2415496](https://ubuntuforums.org/showthread.php?t=2415496), and [https://ubuntuforums.org/showthread.php?t=2360710](https://ubuntuforums.org/showthread.php?t=2360710)), but they didn't seem to exactly overlap with my issue since my logs ended up looking different and they were using different hardware. Any help would be greatly appreciated!

Some go-to's based on the posts I listed:
lsmod output
```
Module                  Size  Used by
rfcomm                 81920  16
cmac                   16384  1
bnep                   24576  2
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             241664  0
kvm                   651264  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
uvcvideo               94208  0
rt2800usb              32768  0
iwlmvm                397312  0
snd_hda_codec_conexant    28672  1
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
rt2x00usb              20480  1 rt2800usb
rt2800lib             126976  1 rt2800usb
aesni_intel           372736  2
rt2x00lib              61440  3 rt2800usb,rt2x00usb,rt2800lib
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
aes_x86_64             20480  1 aesni_intel
mac80211              847872  4 iwlmvm,rt2x00lib,rt2x00usb,rt2800lib
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
crypto_simd            16384  1 aesni_intel
snd_hda_codec_generic    81920  1 snd_hda_codec_conexant
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_conexant
libarc4                16384  1 mac80211
intel_cstate           20480  0
intel_rapl_perf        20480  0
snd_hda_codec_hdmi     57344  1
snd_hda_intel          49152  4
joydev                 28672  0
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
input_leds             16384  0
iwlwifi               348160  1 iwlmvm
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                 1937408  13
serio_raw              20480  0
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
btusb                  57344  0
rtsx_pci_ms            24576  0
snd_seq_midi           20480  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
snd_seq_midi_event     16384  1 snd_seq_midi
btintel                24576  1 btusb
snd_rawmidi            36864  1 snd_seq_midi
bluetooth             573440  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
drm_kms_helper        180224  1 i915
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
ecdh_generic           16384  2 bluetooth
ecc                    32768  1 ecdh_generic
drm                   491520  6 drm_kms_helper,i915
cfg80211              704512  4 iwlmvm,rt2x00lib,iwlwifi,mac80211
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
wmi_bmof               16384  0
memstick               20480  1 rtsx_pci_ms
toshiba_acpi           49152  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
sparse_keymap          16384  1 toshiba_acpi
sysfillrect            16384  1 drm_kms_helper
industrialio           73728  1 toshiba_acpi
sysimgblt              16384  1 drm_kms_helper
snd                    86016  19 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
mei                   102400  1 mei_me
lpc_ich                24576  0
soundcore              16384  1 snd
toshiba_bluetooth      20480  0
acpi_pad              184320  0
mac_hid                16384  0
dw_dmac                16384  0
dw_dmac_core           28672  1 dw_dmac
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   131072  2 usbhid,hid_generic
rtsx_pci_sdmmc         28672  0
ahci                   40960  2
r8169                  81920  0
psmouse               151552  0
libahci                32768  1 ahci
realtek                20480  1
rtsx_pci               69632  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    32768  2 toshiba_acpi,wmi_bmof
video                  49152  2 toshiba_acpi,i915

```

lsusb output:
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 13d3:5652 IMC Networks 
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 006: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 002 Device 002: ID 062a:5918 Creative Labs 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig output:
```
wlx9cefd5fcfa42  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

enp8s0    no wireless extensions.

wlp7s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

---

### Post by TheFu on 2020-03-09
First things first.
[https://github.com/UbuntuForums/](https://github.com/UbuntuForums/)
Run the wireless-info script and provide the output.

---

### Post by vanhooserb on 2020-03-09
Here's the result:  [ATTACH=CONFIG]285181[/ATTACH]

---

### Post by chili555 on 2020-03-10
I wouldn't suggest a Ralink USB device to get your wireless working in preference to the usually reliable Intel. 

This is apparently the entire fault with the Intel:

> 
2: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
In this context, 'hard blocked' suggests that the wireless switch or key combination is set to disable the wireless radio. The message log even confirms it:> 
iwlwifi 0000:07:00.0: RF_KILL bit toggled to disable radio.
Please detach the USB, find the switch or key combination, perhaps, but not always Fn+F2, and switch it!

---

### Post by vanhooserb on 2020-03-10
Looks like the key combo didn't work and this model doesn't include a physical switch, but your information set me on the right path. It appears that it's pretty common for Toshiba's to need to do a power reset (removing battery and holding down power button for 30 seconds) to unset that flag when Linux is loaded onto it. I tried looking for other solutions first, but this appeared to be the only option. After performing the reset, the hard block was removed and I have Wi-Fi access :) Thank you so much to TheFu for getting me started and Chili555 for helping me decipher those logs! Off to enjoy my old laptop's new lease on life.

---

### Post by Captain Cookie on 2020-03-13
At my Ubuntu beginning, I also faced  the wireless-connectivility problem, 
so I did retrieve a lot, spent much time.

But fortunately I could found out that the cause is just a physical switch.

What a simple solution! 

As the machine was my father's PC, so I had not known such switch exist!

---

