---
title: "tplink t9e archer ac1900 AND/OR t4u cant connect easily"
date: 2017-12-17
forum: Networking &amp; Wireless
---

### Post by cillowjr on 2017-12-17
i have these two tp link hardware:
tpe archer ac1900
t4u usb modem

both are connected. connecting to either or both is problematic. even if used separately.
it takes a decade to connect sometimes.
keeps asking me my password, which is correct and is automatically put in.

whats wrong, do you know?

---

### Post by praseodym on 2017-12-17
Please run the wireless script from the sticky thread and show the outputs

---

### Post by cillowjr on 2017-12-17
do you mean this?
02:00.0 Network controller [0280]: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

---

### Post by praseodym on 2017-12-17
Thats the PCI NIC. What about
```

lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by cillowjr on 2017-12-18
```
Lsusb:
Bus 004 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002:ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 006:ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004:ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
lsmod
Module                 Size  Used by
rtl8812au           1359872  0
snd_hda_codec_hdmi    49152  1
bnep                  20480  2
intel_rapl            20480  0
x86_pkg_temp_thermal   16384  0
intel_powerclamp      16384  0
coretemp              16384  0
kvm_intel            200704  0
kvm                  581632  1 kvm_intel
snd_usb_audio        196608  2
irqbypass             16384  1 kvm
snd_usbmidi_lib       32768  1 snd_usb_audio
crct10dif_pclmul      16384  0
crc32_pclmul          16384  0
snd_seq_midi          16384  0
snd_seq_midi_event    16384  1 snd_seq_midi
ghash_clmulni_intel   16384  0
pcbc                  16384  0
snd_rawmidi           32768  2 snd_seq_midi,snd_usbmidi_lib
aesni_intel          188416  0
aes_x86_64            20480  1 aesni_intel
crypto_simd           16384  1 aesni_intel
glue_helper           16384  1 aesni_intel
cryptd                24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate          20480  0
intel_rapl_perf       16384  0
snd_seq               65536  2 snd_seq_midi_event,snd_seq_midi
snd_hda_codec_realtek   94208  1
snd_hda_codec_generic   73728  1 snd_hda_codec_realtek
snd_hda_intel         40960  6
snd_hda_codec        126976  4snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core          81920  5snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep             20480  2 snd_hda_codec,snd_usb_audio
snd_pcm               98304  5snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
snd_seq_device        16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer             32768  2 snd_seq,snd_pcm
wl                  6447104  0
uvcvideo              90112  0
videobuf2_vmalloc     16384  1 uvcvideo
videobuf2_memops      16384  1 videobuf2_vmalloc
videobuf2_v4l2        24576  1 uvcvideo
cfg80211             610304  2 wl,rtl8812au
videobuf2_core        40960  2 uvcvideo,videobuf2_v4l2
videodev             176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
snd                   81920  29snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
media                 40960  2 uvcvideo,videodev
joydev                20480  0
mei_me                40960  0
input_leds            16384  0
shpchp                36864  0
mei                   98304  1 mei_me
soundcore             16384  1 snd
intel_pch_thermal     16384  0
hci_uart             106496  0
btbcm                 16384  1 hci_uart
serdev                20480  1 hci_uart
btqca                 16384  1 hci_uart
btintel               16384  1 hci_uart
bluetooth            540672  11 hci_uart,btintel,btqca,bnep,btbcm
ecdh_generic          24576  1 bluetooth
intel_lpss_acpi       16384  0
intel_lpss            16384  1 intel_lpss_acpi
mac_hid               16384  0
acpi_pad             180224  0
tpm_infineon          20480  0
acpi_als              16384  0
kfifo_buf             16384  1 acpi_als
industrialio          69632  2 acpi_als,kfifo_buf
parport_pc            32768  0
ppdev                 20480  0
lp                    20480  0
parport               49152  3 lp,parport_pc,ppdev
ip_tables             24576  0
x_tables              40960  1 ip_tables
autofs4               40960  2
hid_logitech_hidpp    32768  0
hid_logitech_dj       20480  0
usbhid                49152  0
i915                1798144  38
e1000e               245760  0
nvme                  32768  1
ptp                   20480  1 e1000e
pps_core              20480  1 ptp
nvme_core             53248  3 nvme
mxm_wmi               16384  0
i2c_algo_bit          16384  1 i915
drm_kms_helper       167936  1 i915
syscopyarea           16384  1 drm_kms_helper
sysfillrect           16384  1 drm_kms_helper
sysimgblt             16384  1 drm_kms_helper
fb_sys_fops           16384  1 drm_kms_helper
ahci                  36864  0
drm                  356352  27 i915,drm_kms_helper
libahci               32768  1 ahci
wmi                   24576  1 mxm_wmi
pinctrl_sunrisepoint   28672  0
pinctrl_intel         20480  1 pinctrl_sunrisepoint
video                 40960  1 i915
i2c_hid               20480  0
hid                  118784  11 i2c_hid,usbhid,hid_logitech_dj,hid_logitech_hidpp
```

```
 iwconfig
enp0s31f6  nowireless extensions.


wlp2s0    IEEE802.11  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retryshort limit:7   RTS thr:off   Fragment thr:off
          PowerManagement:on
          
lo        nowireless extensions.


rfkill list
0: phy0: WirelessLAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0:Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by praseodym on 2017-12-18
USB modem is not shown, however driver rtl8812au is loaded?! Check
```

dmesg | egrep 'rtl|wl'
```

---

### Post by cillowjr on 2017-12-18
usb modem may have been unplugged when I ran these. Here are the results of all of this, with the USB. I don't want to rely On the USB though. :( Actually, whatever is faster is what I'll use.
```
lsusb
Bus 004 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007:ID 2357:0101  
Bus 001 Device 005:ID 21b4:0083  
Bus 001 Device 003:ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002:ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 006:ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004:ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
 lsmod
Module                 Size  Used by
rtl8812au           1359872  0
bnep                  20480  2
snd_hda_codec_hdmi    49152  1
intel_rapl            20480  0
x86_pkg_temp_thermal   16384  0
intel_powerclamp      16384  0
coretemp              16384  0
kvm_intel            200704  0
kvm                  581632  1 kvm_intel
snd_usb_audio        196608  4
snd_usbmidi_lib       32768  1 snd_usb_audio
irqbypass             16384  1 kvm
crct10dif_pclmul      16384  0
crc32_pclmul          16384  0
ghash_clmulni_intel   16384  0
pcbc                  16384  0
snd_seq_midi          16384  0
snd_seq_midi_event    16384  1 snd_seq_midi
aesni_intel          188416  0
aes_x86_64            20480  1 aesni_intel
crypto_simd           16384  1 aesni_intel
glue_helper           16384  1 aesni_intel
cryptd                24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_rawmidi           32768  2 snd_seq_midi,snd_usbmidi_lib
intel_cstate          20480  0
snd_hda_codec_realtek   94208  1
snd_hda_codec_generic   73728  1 snd_hda_codec_realtek
intel_rapl_perf       16384  0
snd_hda_intel         40960  6
snd_hda_codec        126976  4snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core          81920  5snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep             20480  2 snd_hda_codec,snd_usb_audio
wl                  6447104  0
snd_pcm               98304  5snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
snd_seq               65536  2 snd_seq_midi_event,snd_seq_midi
uvcvideo              90112  0
cfg80211             610304  2 wl,rtl8812au
joydev                20480  0
snd_seq_device        16384  3 snd_seq,snd_rawmidi,snd_seq_midi
input_leds            16384  0
snd_timer             32768  2 snd_seq,snd_pcm
snd                   81920  33snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
videobuf2_vmalloc     16384  1 uvcvideo
videobuf2_memops      16384  1 videobuf2_vmalloc
videobuf2_v4l2        24576  1 uvcvideo
videobuf2_core        40960  2 uvcvideo,videobuf2_v4l2
videodev             176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
soundcore             16384  1 snd
media                 40960  2 uvcvideo,videodev
shpchp                36864  0
mei_me                40960  0
mei                   98304  1 mei_me
intel_pch_thermal     16384  0
hci_uart             106496  0
btbcm                 16384  1 hci_uart
serdev                20480  1 hci_uart
btqca                 16384  1 hci_uart
btintel               16384  1 hci_uart
bluetooth            540672  11 hci_uart,btintel,btqca,bnep,btbcm
ecdh_generic          24576  1 bluetooth
intel_lpss_acpi       16384  0
intel_lpss            16384  1 intel_lpss_acpi
mac_hid               16384  0
acpi_als              16384  0
tpm_infineon          20480  0
kfifo_buf             16384  1 acpi_als
acpi_pad             180224  0
industrialio          69632  2 acpi_als,kfifo_buf
parport_pc            32768  0
ppdev                 20480  0
lp                    20480  0
parport               49152  3 lp,parport_pc,ppdev
ip_tables             24576  0
x_tables              40960  1 ip_tables
autofs4               40960  2
hid_logitech_hidpp    32768  0
hid_logitech_dj       20480  0
usbhid                49152  0
mxm_wmi               16384  0
i915                1798144  47
i2c_algo_bit          16384  1 i915
drm_kms_helper       167936  1 i915
syscopyarea           16384  1 drm_kms_helper
e1000e               245760  0
sysfillrect           16384  1 drm_kms_helper
sysimgblt             16384  1 drm_kms_helper
fb_sys_fops           16384  1 drm_kms_helper
ptp                   20480  1 e1000e
nvme                  32768  1
pps_core              20480  1 ptp
drm                  356352  28 i915,drm_kms_helper
ahci                  36864  0
nvme_core             53248  3 nvme
libahci               32768  1 ahci
wmi                   24576  1 mxm_wmi
video                 40960  1 i915
pinctrl_sunrisepoint   28672  0
pinctrl_intel         20480  1 pinctrl_sunrisepoint
i2c_hid               20480  0
hid                  118784  11 i2c_hid,usbhid,hid_logitech_dj,hid_logitech_hidpp
```

```
iwconfig
wlp2s0    IEEE802.11  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retryshort limit:7   RTS thr:off   Fragment thr:off
          PowerManagement:on
          
lo        nowireless extensions.
enp0s31f6 nowireless extensions.

wlxec086b12f618 unassociated Nickname:"<WIFI@REALTEK>"
Mode:Managed Frequency=2.437 GHz Access Point: Not-Associated 
Sensitivity:0/0 
Retry:off RTS thr:off Fragment thr:off
PowerManagement:off
LinkQuality:0 Signal level:0 Noise level:0
Rx invalidnwid:0 Rx invalid crypt:0 Rx invalid frag:0
Txexcessive retries:0 Invalid misc:0 Missed beacon:0
```

```
rfkill list
0: phy0: WirelessLAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0:Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: WirelessLAN
    Soft blocked: no
    Hard blocked: no
dmesg | egrep'rtl|wl'
[ 3.168976] wl:loading out-of-tree module taints kernel.
[ 3.168979] wl:module license 'MIXED/Proprietary' taints kernel.
[ 3.171721] wl:module verification failed: signature and/or required key missing -tainting kernel
[ 3.244633]wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller6.30.223.271 (r587334)
[ 3.812753] wl0000:02:00.0 wlp2s0: renamed from wlan0
[ 3.858326] IPv6:ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 223.048790]RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[ 223.048791]RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[ 223.144938]RTL871X: rtw_ndev_init(wlan0)
[ 223.146937]usbcore: registered new interface driver rtl8812au
[ 223.153701]rtl8812au 1-7.2:1.0 wlxec086b12f618: renamed from wlan0
[ 223.173341] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 223.560360] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 223.618763] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 232.329145]RTL871X: rtw_set_802_11_connect(wlxec086b12f618) fw_state=0x00000008
[ 278.002856] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 303.003350] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 328.003034] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
[ 353.002869] IPv6:ADDRCONF(NETDEV_UP): wlxec086b12f618: link is not ready
```

---

### Post by praseodym on 2017-12-18
Deactivate SecureBoot in your UEFI

[ 3.171721] wl:module verification failed: signature and/or **required key missing** -tainting kernel

---

### Post by cillowjr on 2017-12-18
could you tell me how, or send me link that explains it?

is the only way to accomplish this via BIOS?

oh nevermind. I accessed my bios and under secure boot state, it says: disabled.



???

---

### Post by cillowjr on 2017-12-21
> **praseodym said:**
> 

[ 3.171721] wl:module verification failed: signature and/or **required key missing** -tainting kernel

what does this bit mean?
Any ideas?
it got better this problem but sometimes keeps coming back!
I'm not asking b/c I'm not sure if it's solved!. I upgraded to 17.1 from 16.04

---

