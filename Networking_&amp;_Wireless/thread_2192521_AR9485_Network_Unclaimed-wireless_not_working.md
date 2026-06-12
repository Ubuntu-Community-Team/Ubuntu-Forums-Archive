---
title: "AR9485 Network Unclaimed-wireless not working"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by vinze86 on 2013-12-08
Dear all,
I am Vincenzo, a new forum user and a new Ubuntu user.
I am trying (without success) to solve a wireless connection problem, also reading other threads with similar problems.

I am not able to have a wireless connection while I am on Ubuntu. I have a Samsung NP350-V5C, on which I have dual boot with windows 7. On windows the wireless connection works fine, but on Ubuntu not. I had ubuntu 10.04; after that i Upgraded to Ubuntu 12.04 and now to ubuntu 12.10. In all ubuntu versions I have no wireless connection.

I will post you the results of some terminal commands written in order to have some informations on wireless devices.
I will thank you If someone could help me in solving this problem.
[B]
sudo lshw -C network[/B]
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 09
       serial: b8:88:e3:3f:de:9a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff

```
 
**rfkill list**
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

**iwconfig**
```

eth0      no wireless extensions.

lo        no wireless extensions.

```

Thanks all

---

### Post by praseodym on 2013-12-08
Please show
```

uname -a
lsmod
cat /etc/resolv.conf

```
Load the driver by hand:
```

sudo modprobe -v ath9k
```

---

### Post by vinze86 on 2013-12-08
[QUOTE=praseodym;12868327]Please show

uname -a
```

Linux vincenzo-laptop 3.5.0-44-generic #67-Ubuntu SMP Tue Nov 12 19:36:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```
lsmod
```

Module                  Size  Used by
dm_crypt               23012  0 
parport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 46620  12 
bnep                   18141  2 
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414111  1 kvm_intel
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
samsung_laptop         14533  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
microcode              22804  0 
snd_seq_midi_event     14900  1 snd_seq_midi
joydev                 17458  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
rts5139               356200  0 
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ath3k                  12919  0 
btusb                  22475  0 
bluetooth             209438  23 rfcomm,bnep,ath3k,btusb
psmouse               100424  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13216  0 
lpc_ich                17062  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
mei                    40691  0 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100658  2 hid_generic,usbhid
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
ahci                   25721  2 
libahci                31192  1 ahci
r8169                  61671  0 
radeon                900791  1 
i915                  520925  4 
ttm                    83596  1 radeon
drm_kms_helper         49113  2 radeon,i915
video                  19391  2 samsung_laptop,i915
drm                   288972  8 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13414  2 radeon,i915

```

cat /etc/resolv.conf
```

Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.0.1

```


Load the driver by hand:
```

sudo modprobe -v ath9k
```
sORRY, this is the command to load the driver? DO I have to type it from terminal?
Thank you

---

### Post by praseodym on 2013-12-08
Yes, this loads the driver.

---

### Post by vinze86 on 2013-12-08
Ok, I have done as suggested by you: this is the result
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/3.5.0-44-generic/updates/compat/compat.ko 
insmod /lib/modules/3.5.0-44-generic/updates/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-44-generic/updates/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-44-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.5.0-44-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.5.0-44-generic/updates/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-44-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko 

```
It seems no good.

---

### Post by praseodym on 2013-12-08
Lets check
```

lsmod
route -n
iwconfig
ifconfig -a
sudo iwlist scan
```

---

### Post by vinze86 on 2013-12-08
lsmod
```

Module                  Size  Used by
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100658  2 hid_generic,usbhid
arc4                   12530  2 
ath9k                 101457  0 
mac80211              549124  1 ath9k
ath9k_common           13860  1 ath9k
ath9k_hw              410231  2 ath9k,ath9k_common
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
cfg80211              537288  3 ath9k,mac80211,ath
compat                 22766  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
dm_crypt               23012  0 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  12 
binfmt_misc            17501  1 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414111  1 kvm_intel
psmouse               100424  0 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
samsung_laptop         14533  0 
snd                    78921  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13206  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
microcode              22804  0 
ath3k                  12919  0 
btusb                  22475  0 
rts5139               356200  0 
videodev              120310  2 uvcvideo,videobuf2_core
bluetooth             209438  23 bnep,rfcomm,ath3k,btusb
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
lpc_ich                17062  0 
serio_raw              13216  0 
soundcore              15048  1 snd
lp                     17760  0 
mei                    40691  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
parport                46346  3 parport_pc,ppdev,lp
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
r8169                  61671  0 
ahci                   25721  2 
libahci                31192  1 ahci
radeon                900791  1 
i915                  520925  3 
ttm                    83596  1 radeon
drm_kms_helper         49113  2 radeon,i915
drm                   288972  7 radeon,i915,ttm,drm_kms_helper
video                  19391  2 samsung_laptop,i915
i2c_algo_bit           13414  2 radeon,i915

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

iwconfig
```


eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr b8:88:e3:3f:de:9a  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba88:e3ff:fe3f:de9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91958530 (91.9 MB)  TX bytes:7673142 (7.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3232 (3.2 KB)  TX bytes:3232 (3.2 KB)

wlan0     Link encap:Ethernet  HWaddr e8:03:9a:c4:86:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

sudo iwlist scan

```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:E5:2A:45:42:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00094E4554474541523432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606051600000000000000000000000000000000000000
                    IE: Unknown: DD7D0050F204104A00011010440001021041000100103B00010310470010DAB0F7074A4E38CE42A120E8C6F35FCE102100074E6574676561721023000944474E3232303076331024000944474E32323030763310420004313233341054000800060050F20400011011000944474E323230307633100800020084103C000101
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:22:3F:1E:C9:40
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UGO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000095921aef7e
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000355474F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 070A474200010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B000103104700108328DD28C6ABBA833B87585F1A97C045102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086
          Cell 03 - Address: 00:0C:F6:EE:39:93
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"SitecomEE3993"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000035082bd90
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 000D53697465636F6D454533393933
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E101EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    IE: Unknown: DD1E00904C336E101EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 04 - Address: A4:B1:E9:D8:EB:CB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"TNCAPD8EBCB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000210ebab6a42
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000B544E434150443845424342
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD9C0050F204104A0001101044000102103B00010310470010D6B391223E075E50A7124B2189510A0F1021000B546563686E69636F6C6F721023000E4D6564696141636365737320544710240008373838766E207632104200093133313452414130341054000800060050F2040001101100164D65646961416363657373205447373838766E207632100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

I forgot to say that with LAN cable, connection works without problems.

---

### Post by praseodym on 2013-12-08
Try now to connect wireless, LAN is always preferred.

---

### Post by vinze86 on 2013-12-08
You are a genius. Now, finally, ubuntu sees wireless connections. It is very very slow, but now I see it. 
First question
1) Can you say me what was the problem and what kind of operation you have suggested me to solve it?
2) Why connection is so slow?

Sorry if I am annoying you, but I would like to understand what are the problems.

---

### Post by praseodym on 2013-12-08
Which of the networks from the scan is yours? I recommend using a fixed channel and pure WPA2-AES encryption

---

### Post by vinze86 on 2013-12-09
My Network is Netgear42; however, today morning, trying in a different place, the problem seems not completely solved. As before, the laptop doesn't see any wireless network.

---

### Post by vinze86 on 2013-12-09
But every time Have I to load the drivers?

---

