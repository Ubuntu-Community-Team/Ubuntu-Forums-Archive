---
title: "Ethernet not detected in Lubuntu 12.04"
date: 2014-07-10
forum: Networking &amp; Wireless
---

### Post by TheBigH on 2014-07-10
Hi all,
I just installed lubuntu12.04 and it is not detecting ethernet, and I have no internet access on that machine at all.

Here is the outputs of ifconfig -a, lspci -nn, and lsmod:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44608 (44.6 KB)  TX bytes:44608 (44.6 KB)

00:00.0 Host bridge [0600]: Intel Corporation Haswell DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Haswell PCI Express x16 Controller [8086:0c01] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:8cb1]
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:8cba]
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:15a1]
00:1a.0 USB controller [0c03]: Intel Corporation Device [8086:8cad]
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:8ca0]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:8c90] (rev d0)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d0)
00:1d.0 USB controller [0c03]: Intel Corporation Device [8086:8ca6]
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:8cc6]
00:1f.2 SATA controller [0106]: Intel Corporation Device [8086:8c82]
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:8ca2]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450] [1002:6779]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17699  0 
usb_storage            39646  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_hdmi     31775  1 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
ppdev                  12849  0 
snd_hda_intel          32765  1 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                729591  2 
ttm                    65344  1 radeon
snd_seq_midi           13132  0 
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
usbhid                 41906  0 
video                  19068  0 
snd_rawmidi            25424  1 snd_seq_midi
hid                    77367  1 usbhid
psmouse                87140  0 
parport_pc             32114  1 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
acpi_pad               13654  0 
mac_hid                13077  0 
snd                    62064  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
```

Does anyone know how to fix this issue?

---

### Post by Vladlenin5000 on 2014-07-10
Lubuntu 12.04 isn't a LTS release and as such is currently EoL, not supported. Please use a supported version. For Lubuntu that's 14.04 only.

---

### Post by TheBigH on 2014-07-10
This was the highest numbered version unetbootin would do. When I have internet working, then I will upgrade it to the latest version. But I need to get my ethernet cable working first.

---

### Post by Vladlenin5000 on 2014-07-10
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

PS - In Unetbootin you aren't limited to the dropdown menu options. You can point it to an ISO you previously downloaded and proceed from there.
Considering you had to have internet for the option you tried first then you could as well have done as I just explained.

---

### Post by TheBigH on 2014-07-10
That's fine.

---

