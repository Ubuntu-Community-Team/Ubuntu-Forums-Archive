---
title: "Slow speeds after upgrading to 13.10"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Andy_Lee on 2013-10-20
I have a problem with wired connection & NAS file copy. When connect with wifi adapter, surf internet very smooth and file copy to NAS server ~ 3-4MB/s. But with wired connection it too slow, file copy to NAS freeze.

```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
Kernel driver in use: r8168

lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmod
Module                  Size  Used by
cfg80211              479757  0 
parport_pc             32701  0 
bnep                   19564  2 
ppdev                  17671  0 
rfcomm                 69070  0 
bluetooth             371874  10 bnep,rfcomm
snd_hda_codec_hdmi     41276  1 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
r8712u                184124  0 
snd_hda_codec_realtek    51465  1 
radeon               1402449  3 
snd_hda_intel          48171  5 
kvm                   431315  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ttm                    83995  1 radeon
microcode              23518  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm_kms_helper         52651  1 radeon
serio_raw              13413  0 
drm                   296739  5 ttm,drm_kms_helper,radeon
sp5100_tco             13979  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
k10temp                13126  0 
i2c_algo_bit           13413  1 radeon
edac_core              62312  0 
edac_mce_amd           22617  0 
i2c_piix4              22106  0 
ohci_pci               13561  0 
wmi                    19070  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
pata_atiixp            13242  0 
r8168                 261295  0 
ahci                   25819  3 
libahci                31898  1 ahci

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"XXX"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 4C:E6:76:F9:8E:9E   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:18:a1:79:62  
          inet6 addr: fe80::230:18ff:fea1:7962/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25839 errors:0 dropped:34 overruns:0 frame:0
          TX packets:24187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22714992 (22.7 MB)  TX bytes:4749769 (4.7 MB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:230209 (230.2 KB)  TX bytes:230209 (230.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:a1:cc:f8:f9  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fecc:f8f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3417027 errors:0 dropped:653749 overruns:0 frame:0
          TX packets:3153685 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2704274105 (2.7 GB)  TX bytes:2720809543 (2.7 GB)

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

---

### Post by wildmanne39 on 2013-10-20
Please use code tags and start your own thread instead of posting in someone else's.
Thanks

---

### Post by Andy_Lee on 2013-10-20
I'm sry. Tks.

---

### Post by Andy_Lee on 2013-10-20
I try connect to router through 100mbps switch, file copy to NAS speed normally, internet surfing smooth.

My router WZR-HP-AG300H, fw: dd-wrt.

Also try Ubuntu gnome 13.10 amd64 & Xubuntu 13.10 amd64, same issue.

---

