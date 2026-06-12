---
title: "Wireless drops out"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by LaJuan on 2014-02-15
Hi,

I have a daul boot Ubuntu 13.10 and Windows 7 Pro, 4GB, Dell Latitude E6410. Like most daul boots, Windows also does something to the network driver. My wireless will work when I first start up in Ubuntu but, soon, it cut off. I checked additional drivers and it says none listed. Im at a complete lost how to keep the wireless up and running while operating in Ubuntu.

Confused,
:-s:-?:???:

---

### Post by praseodym on 2014-02-15
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by LaJuan on 2014-02-16
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
    Kernel driver in use: iwlwifi
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Module                  Size  Used by
bnep                   18959  2 
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_idt      44605  1 
rfcomm                 53664  12 
joydev                 17097  0 
arc4                   12536  2 
intel_powerclamp       14239  0 
coretemp               13195  0 
iwldvm                219934  0 
kvm_intel             128218  0 
mac80211              517444  1 iwldvm
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ppdev                  17391  0 
snd_timer              24447  2 snd_pcm,snd_seq
pcmcia                 51368  0 
lp                     13299  0 
snd                    60790  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
microcode              18830  0 
psmouse                90642  0 
serio_raw              13189  0 
intel_ips              18055  0 
btusb                  23443  0 
i915                  594380  8 
bluetooth             323656  22 bnep,btusb,rfcomm
iwlwifi               143736  1 iwldvm
cfg80211              401762  3 iwlwifi,mac80211,iwldvm
drm_kms_helper         46867  1 i915
yenta_socket           40193  0 
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm                   242400  4 i915,drm_kms_helper
lpc_ich                16864  0 
mei_me                 13933  0 
soundcore              12600  1 snd
mei                    66411  1 mei_me
i2c_algo_bit           13197  1 i915
wmi                    18590  1 dell_wmi
parport_pc             31981  0 
parport                40795  3 lp,ppdev,parport_pc
video                  18777  1 i915
mac_hid                13037  0 
firewire_ohci          35463  0 
firewire_core          57656  1 firewire_ohci
e1000e                223181  0 
sdhci_pci              18481  0 
crc_itu_t              12627  1 firewire_core
sdhci                  37644  1 sdhci_pci
ahci                   25579  2 
ptp                    18156  1 e1000e
libahci                26554  1 ahci
pps_core               18546  1 ptp

eth0      Link encap:Ethernet  HWaddr 00:26:b9:e6:18:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f6900000-f6920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51885 (51.8 KB)  TX bytes:51885 (51.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:27:10:1a:fd:18  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::227:10ff:fe1a:fd18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3320536 (3.3 MB)  TX bytes:531575 (531.5 KB)

wlan0     IEEE 802.11abgn  ESSID:"LaJuan's Domain"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:18:E7:ED:8A:DD   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1303  Invalid misc:14   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.447 GHz (Channel 8)

lo        no frequency information.

eth0      no frequency information.

wlan0     Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search nc.rr.com

---

### Post by praseodym on 2014-02-16
There is a bug with the N-mode of the driver:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot.

---

### Post by LaJuan on 2014-02-19
Reboot and same results...

---

### Post by LaJuan on 2014-02-20
Here are my results:

options iwlwifi 11n_disable=1

I reboot and the wireless works but, drops out after a few minutes....

---

