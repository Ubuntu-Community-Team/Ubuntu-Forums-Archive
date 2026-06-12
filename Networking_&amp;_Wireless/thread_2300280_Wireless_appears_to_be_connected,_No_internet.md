---
title: "Wireless appears to be connected, No internet"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by Maggic on 2015-10-24
I have recently installed Ubuntu for the first time and am having  trouble connecting to the internet. I installed Ubuntu alongside Windows  7. (No problems with windows 7, except I have to replug the wireless  USB after restart). My wireless adapter is Netgear WNA3100, which I got  running through ndiswrapper. Now it finds networks and lets me connect  to my network, though I only get internet long enough to go to one  webpage, if even. Then I don't get any internet unless I restart, to the  same effect. The modem recognizes Ubuntu, with Ubuntu's computer name  (rather than Windows 7) but with the same IP address.
When I 'ping  10.0.0.1' it doesn't see anything; though I'm not sure if that's the  appropriate way to ping from Ubuntu. I've done some trouble shooting  from the internet, with no avail, but here are some things I did in the  terminal that hopefully gives some starting information.
Thanks for the help.

```
sir@Robotic:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux Robotic 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
 
sir@Robotic:~$ lspci -nnk | grep -iA2 net
03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 03)
            Subsystem: Elitegroup Computer Systems Device [1019:8d48]
            Kernel driver in use: r8169
 
sir@Robotic:~$ iwconfig
eth0      no wireless extensions.
 
wlan0     IEEE 802.11g  ESSID:"Moon Buggy Cadillac" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:03:FA:64:82:F4  
          Bit Rate=117 Mb/s   Tx-Power:32 dBm  
          RTS thr:2347 B   Fragment thr:2346 B  
          Power Management:off
          Link Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:1426   Missed beacon:0
 
lo        no wireless extensions.
 
sir@Robotic:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:78:d2:26:05:83 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:34313 (34.3 KB)  TX bytes:34313 (34.3 KB)
 
wlan0     Link encap:Ethernet  HWaddr 6c:b0:ce:7f:a5:8c 
          inet6 addr: 2601:603:4400:6925:6eb0:ceff:fe7f:a58c/64 Scope:Global
          inet6 addr: fe80::6eb0:ceff:fe7f:a58c/64 Scope:Link
          inet6 addr: 2601:603:4400:6925:8d2a:7fdc:e54:19c4/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20803 (20.8 KB)  TX bytes:25424 (25.4 KB)
 
sir@Robotic:~$ rfkill list all
sir@Robotic:~$ lsmod
Module                  Size  Used by
nls_utf8               16384  1
isofs                  40960  1
cfg80211              524288  0
rfcomm                 69632  0
bnep                   20480  2
bluetooth             491520  10 bnep,rfcomm
parport_pc             32768  0
ppdev                  20480  0
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          32768  3
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0
snd_timer              32768  2 snd_pcm,snd_seq
kvm_amd                61440  0
kvm                   479232  1 kvm_amd
snd                     86016  16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
k10temp                16384  0
edac_core              53248  0
edac_mce_amd           24576  0
nouveau              1368064  3
soundcore              16384  2 snd,snd_hda_codec
i2c_piix4              24576  0
mxm_wmi                16384  1 nouveau
video                  20480  1 nouveau
ttm                    94208  1 nouveau
drm_kms_helper        126976  1 nouveau
drm                   344064  6 ttm,drm_kms_helper,nouveau
ndiswrapper           286720  0
i2c_algo_bit           16384  1 nouveau
8250_fintek            16384  0
shpchp                 40960  0
mac_hid                16384  0
wmi                    20480  2 mxm_wmi,nouveau
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0
hid_generic            16384  0
usbhid                 53248  0
hid                   110592  2 hid_generic,usbhid
psmouse               114688  0
r8169                  81920  0
mii                    16384  1 r8169
ahci                   36864  3
pata_atiixp            16384  0
libahci                32768  1 ahci

```

---

### Post by Vladlenin5000 on 2015-10-24
There's no point in using an old, bad and unsupported hardware.
The time and trouble you already had are worth the $10 or less that you would be shelling out for a new, much better and supported hardware?

---

