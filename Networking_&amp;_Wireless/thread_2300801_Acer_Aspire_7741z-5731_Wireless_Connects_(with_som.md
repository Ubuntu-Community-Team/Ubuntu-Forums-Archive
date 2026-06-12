---
title: "Acer Aspire 7741z-5731 Wireless Connects (with some retries) but no internet"
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by Naveed_Pasha on 2015-10-28
Hello All,
I realise this question has been asked before and I have already tried the solutions that have been proposed with no result.

I have an Acer Aspire 7741z-5731 running Ubuntu 15.10. Wired connection works fine but wireless negotiates connection with router after several retries. Even after connecting, it doesn't give internet. Please help.

```

~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)

~$ uname -a
Linux adam-Aspire-7741 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

~$ lsusb
Bus 002 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ iwconfig
wlp4s0    IEEE 802.11bgn  ESSID:"HOME-35B2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D1:0C:35:B0   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:0   Missed beacon:0

enp2s0    no wireless extensions.

lo        no wireless extensions.

~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

~$ lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
arc4                   16384  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     49152  1
ath9k                 147456  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
mac80211              733184  1 ath9k
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
input_leds             16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0
intel_ips              20480  0
cfg80211              548864  4 ath,ath9k_common,ath9k,mac80211
intel_powerclamp       16384  0
snd_timer              32768  2 snd_pcm,snd_seq
coretemp               16384  0
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
shpchp                 36864  0
mei_me                 32768  0
mei                    98304  1 mei_me
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
broadcom               20480  0
i915                 1130496  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
tg3                   163840  0
ptp                    20480  1 tg3
drm                   356352  5 i915,drm_kms_helper
psmouse               126976  0
pps_core               20480  1 ptp
ahci                   36864  2
libahci                32768  1 ahci
wmi                    20480  0
video                  36864  1 i915


```

I have already tried:
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

but no joy.

please help.

Thanks

---

