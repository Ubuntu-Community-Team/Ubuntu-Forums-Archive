---
title: "Ubuntu 18.04 Wireless hard blocked"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by gitsad on 2018-05-26
Hi,

I have just installed Ubuntu 18.04 on my laptop and system seems not to enable my WiFi. I was trying some solutions on Internet which most of them was connect to Ubuntu 16 but it has not solved the problem.

I have installed drivers for my WiFi card  which is
```

Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter

```

I ran this command ```
rfkill list all
```

and I have received:
```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

and after ```
lsmod
```

```

Module                  Size  Used by
rtl8821ae             233472  0
btcoexist             172032  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8821ae
mac80211              778240  3 rtl_pci,rtlwifi,rtl8821ae
rfcomm                 77824  4
cmac                   16384  0
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_realtek   102400  1
wmi_bmof               16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
intel_rapl             20480  0
arc4                   16384  2
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   593920  0
irqbypass              16384  1 kvm
snd_hda_intel          40960  6
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
pcbc                   16384  0
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  3 snd_hda_intel,snd_hda_codec,snd_hda_core
8812au               1298432  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           188416  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_timer              32768  2 snd_seq,snd_pcm
cfg80211              622592  3 8812au,mac80211,rtlwifi
snd                    81920  22 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
btusb                  45056  0
btrtl                  16384  1 btusb
uvcvideo               86016  0
btbcm                  16384  1 btusb
videobuf2_vmalloc      16384  1 uvcvideo
serio_raw              16384  0
btintel                16384  1 btusb
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
bluetooth             548864  33 btrtl,btintel,bnep,btbcm,rfcomm,btusb
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
mei_me                 40960  0
media                  40960  2 uvcvideo,videodev
soundcore              16384  1 snd
nvidia_uvm            757760  0
ecdh_generic           24576  1 bluetooth
joydev                 24576  0
mei                    90112  1 mei_me
shpchp                 36864  0
input_leds             16384  0
intel_pch_thermal      16384  0
ideapad_laptop         32768  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    24576  2 wmi_bmof,ideapad_laptop
acpi_pad              180224  0
tpm_crb                16384  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_logitech_hidpp     32768  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
nvidia_drm             40960  7
nvidia_modeset       1110016  7 nvidia_drm
nvidia              14340096  506 nvidia_modeset,nvidia_uvm
i915                 1617920  5
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  2 i915,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme                   32768  0
psmouse               147456  0
drm                   401408  12 i915,nvidia_drm,drm_kms_helper
r8169                  86016  0
ahci                   36864  1
nvme_core              61440  3 nvme
ipmi_devintf           20480  0
mii                    16384  1 r8169
libahci                32768  1 ahci
ipmi_msghandler        53248  2 nvidia,ipmi_devintf


```

So I think the hard blocking is the problem here. Does anyone know how to resolve this? Thanks!

---

### Post by him610 on 2018-05-26
Hello gitsad, and welcome to  Ubuntu Forums,

> Hard blocked: yes

The reason your wifi connection is hard blocked is because there is a switch on your laptop that needs to be set to "On" to turn on your wifi card. It may be in the form of a key combination or wifi dedicated switch. Take a look at your owner's manual; it should show where the switch is located. Once you locate it and set it to "On" you may need to reboot your machine.

---

### Post by jeremy31 on 2018-05-26
Moved to Networking and Wireless

If this is a newer Lenovo do ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

---

### Post by gitsad on 2018-05-26
Wow thanks [ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1924242_5.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1924242") 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=1924242"]**[COLOR=#C61919][B]jeremy31**[/COLOR][/B][COLOR=#C61919][B]
[/B][/COLOR][/URL]

---

### Post by gitsad on 2018-05-26
Everything works now :p

---

