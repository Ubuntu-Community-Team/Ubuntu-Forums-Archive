---
title: "No Connection with Ethernet - Lenovo T430"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by ben62 on 2014-03-20
So I'm brand new to Linux and having problems (aka no connection) with getting on the internet. I have a Lenovo T430. Whenever I plug in the ethernet, the network manager tries to connect and pops up a message that it disconnected. It will continue to try to connect each time. I have plugged this in directly from the cable modem and my Netgear switch, but neither works (I have internet to my Windows desktop through the switch). 


> benfox@Bens:~$ uname -a
Linux Bens 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

> benfox@Bens:~$ lspci -nnk|grep -ia2 net 
   Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: serial
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

> benfox@Bens:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 004: ID 04f2:b2db Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

> benfox@Bens:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
bnep                   24107  2 
rfcomm                 74718  0 
parport_pc             32866  0 
ppdev                  17711  0 
bluetooth             391726  10 bnep,rfcomm
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56448  1 
arc4                   12573  2 
iwldvm                244465  0 
joydev                 17613  0 
snd_hda_intel          53038  3 
mac80211              619465  1 iwldvm
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               82247  0 
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
iwlwifi               175459  1 iwldvm
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
thinkpad_acpi          81839  0 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
cfg80211              499466  3 iwldvm,mac80211,iwlwifi
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
i915                  688281  3 
wmi                    19256  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         53237  1 i915
mei_me                 18418  0 
drm                   306660  4 i915,drm_kms_helper
mei                    78537  1 mei_me
i2c_algo_bit           13564  1 i915
snd                    73753  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,thinkpad_acpi,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                21163  0 
video                  19574  1 i915
psmouse               104093  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
soundcore              12680  1 snd
serio_raw              13413  0 
tpm_tis                19255  0 
mac_hid                13253  0 
nvram                  14413  1 thinkpad_acpi
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_logitech_dj        18767  0 
usbhid                 53329  0 
hid                   106315  2 hid_logitech_dj,usbhid
usb_storage            66567  1 
e1000e                257955  0 
ptp                    18627  1 e1000e
ahci                   30063  2 
pps_core               19056  1 ptp
sdhci_pci              19146  0 
libahci                32118  1 ahci
sdhci                  43292  1 sdhci_pci

> benfox@Bens:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

> benfox@Bens:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:cc:d6:83:b5  
          inet6 addr: fe80::221:ccff:fed6:83b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361928 (361.9 KB)  TX bytes:65640 (65.6 KB)
          Interrupt:20 Memory:f2500000-f2520000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72816 (72.8 KB)  TX bytes:72816 (72.8 KB)


wlan0     Link encap:Ethernet  HWaddr 60:67:20:d6:bf:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> benfox@Bens:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Iowan on 2014-03-20
You can try resetting the modem. Modems frequently "lock onto" a MAC address. A router would present the modem with a constant MAC address - the switch probably does not. If it works, you may lose Internet on the Windows desktop until you reset again.

---

### Post by ben62 on 2014-03-20
> **Iowan said:**
> You can try resetting the modem. Modems frequently "lock onto" a MAC address. A router would present the modem with a constant MAC address - the switch probably does not. If it works, you may lose Internet on the Windows desktop until you reset again.

I feel stupid now, the switch I have has only 1 good port on it and of course I was trying to use all the dead ones for my laptop. Thanks for the reply.

---

