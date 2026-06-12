---
title: "Wi-Fi off - Doesn't turn on"
date: 2016-09-28
forum: Networking &amp; Wireless
---

### Post by Aeretic on 2016-09-28
I've just bought a Xiaomi Mi Air 13.3 and I want to use Linux on it.

I tried Arch Linux, I connected it via wireless (it doesn't have the ethernet port) using wpa_supplicant in command line during the installation.
I installed NetworkManager (and its relative applet) then booted on.
The applet was working but I couldn't turn the WiFi ON. It stays on OFF "unavailable".
After an headache I decided to go back to my beloved Ubuntu and the problem is still there, I can't turn it ON.

My card should be working fine, I had internet access with wpa_supplicant and no additional drivers or tweaks were needed.

I have Ubuntu 16.04LTS with Gnome (I directly installed Ubuntu Gnome.
My laptop doesn't have neither a wireless port nor a toggle wifi button.
I can buy a wireless adapter but only if necessary.

How can I fix it? ^^

---

### Post by chili555 on 2016-09-28
Please open a terminal and run and post:```
rfkill list all
lsmod
```

---

### Post by Aeretic on 2016-09-28
Darn, I wanted to try rfkill on Arch (after lurking a bit) but it was not in the base package and I couldn't connect anymore.
Forgot Ubuntu comes with a lot more things.

```
andreafiocchi@eden:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
andreafiocchi@eden:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  2
bnep                   20480  2
acer_wmi               20480  0
dell_wmi_aio           16384  0
sparse_keymap          16384  2 dell_wmi_aio,acer_wmi
snd_hda_codec_hdmi     53248  1
snd_soc_skl            49152  0
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
arc4                   16384  2
snd_hda_codec_realtek    86016  1
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_soc_core          212992  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_intel          36864  6
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
nls_iso8859_1          16384  1
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
kvm                   536576  1 kvm_intel
snd_rawmidi            32768  1 snd_seq_midi
irqbypass              16384  1 kvm
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
joydev                 20480  0
serio_raw              16384  0
iwlwifi               200704  1 iwlmvm
snd                    81920  25 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
tpm_crb                16384  0
mac_hid                16384  0
acpi_pad               20480  0
shpchp                 36864  0
mei_me                 36864  0
mei                    98304  1 mei_me
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
jitterentropy_rng      16384  0
drbg                   32768  1
ansi_cprng             16384  0
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  2
hid_generic            16384  0
usbhid                 49152  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  107
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  55 aesni_intel,ablk_helper
psmouse               126976  0
nouveau              1495040  0
i915_bpo             1261568  8
mxm_wmi                16384  1 nouveau
intel_ips              20480  1 i915_bpo
ttm                    94208  1 nouveau
i2c_algo_bit           16384  2 i915_bpo,nouveau
drm_kms_helper        147456  2 i915_bpo,nouveau
nvme                   65536  4
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  11 ttm,i915_bpo,drm_kms_helper,nouveau
ahci                   36864  0
libahci                32768  1 ahci
wmi                    20480  4 dell_wmi_aio,acer_wmi,mxm_wmi,nouveau
video                  40960  3 i915_bpo,acer_wmi,nouveau
pinctrl_sunrisepoint    28672  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  3 i2c_hid,hid_generic,usbhid
fjes                   28672  0



```

---

### Post by chili555 on 2016-09-28
> acer_wmi               20480  0
dell_wmi_aio           16384  0
sparse_keymap          16384  2 dell_wmi_aio,acer_wmiHmmm. Your Xiaomi Mi Air 13.3 is either a Dell OEM or an Acer; but probably not both. We may have to experiment a bit. From the terminal:```
sudo -i
echo "blacklist acer-wmi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and try again:```
rfkill list all
```We hope this is missing and the wireless is working:> 2: acer-wireless: Wireless LAN
    [COLOR="#FF0000"]Soft blocked: yes[/COLOR]
    Hard blocked: no

---

### Post by Aeretic on 2016-09-28
I'm posting from the Xiaomi, I guess you fixed my problem :P

Thank you very much for your help and the explanation!

---

