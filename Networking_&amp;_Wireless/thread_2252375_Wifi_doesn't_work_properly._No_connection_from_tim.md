---
title: "Wifi doesn't work properly. No connection from time to time."
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by kamil11 on 2014-11-11
Hi! I have Windows 8 and Ubuntu 14.04 installed on one computer, but this problem only appears on Ubuntu. I'm losing connection from time to time. I'm new to Ubuntu. I don't know what's going on. Here's some info:
```

lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
arc4                   12608  2 
rtl8187                64909  0 
snd_hda_codec_hdmi     46368  1 
mac80211              630653  1 rtl8187
joydev                 17381  0 
hid_generic            12548  0 
usbhid                 52659  0 
cfg80211              484040  2 mac80211,rtl8187
hid                   106148  2 hid_generic,usbhid
eeprom_93cx6           13344  1 rtl8187
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
rfcomm                 69160  0 
mxm_wmi                13021  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_hda_codec_realtek    65580  1 
coretemp               13435  0 
snd_hda_intel          56451  5 
kvm                   451729  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
crct10dif_pclmul       14289  0 
snd_hwdep              13602  1 snd_hda_codec
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
radeon               1522640  4 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lrw                    13286  1 aesni_intel
snd_seq_midi           13324  0 
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
ttm                    85150  1 radeon
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         55071  1 radeon
lpc_ich                21080  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  6 ttm,drm_kms_helper,radeon
parport_pc             32701  0 
soundcore              12680  1 snd
mei_me                 18627  0 
i2c_algo_bit           13413  1 radeon
mei                    82276  1 mei_me
ppdev                  17671  0 
wmi                    19177  2 mxm_wmi,asus_wmi
video                  19476  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  1 
psmouse               106714  0 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

```

```

lsusb
Bus 002 Device 005: ID 1532:010e Razer USA, Ltd 
Bus 002 Device 004: ID 046d:c249 Logitech, Inc. 
Bus 002 Device 003: ID 1b75:8187 Ovislink Corp. AirLive WL-1600USB 802.11g Adapter [Realtek RTL8187L]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"AP-TVK 88/43"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:27:19:E9:E1:00   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:141   Missed beacon:0

```

```

lspci -k | egrep -iA2 'net|wire|eth'
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
    Kernel driver in use: r8169

```

```

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:64:57:18
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1.2
       logical name: wlan0
       serial: 00:4f:78:00:02:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-39-generic firmware=N/A ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11bg

```

```

ifconfig
eth0      Link encap:Ethernet  HWaddr f4:6d:04:64:57:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149549 (149.5 KB)  TX bytes:149549 (149.5 KB)


wlan0     Link encap:Ethernet  HWaddr 00:4f:78:00:02:54  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:78ff:fe00:254/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14036137 (14.0 MB)  TX bytes:2711055 (2.7 MB)

```

```

iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:27:19:E9:E1:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"AP-TVK 88/43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008179a57e1a
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 000C41502D54564B2038382F3433
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1E:2A:63:6A:B8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Waldi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001276b777
                    Extra: Last beacon: 3932ms ago
                    IE: Unknown: 000557616C6469
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 64:66:B3:4A:4C:C2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008178ad9ad4
                    Extra: Last beacon: 3928ms ago
                    IE: Unknown: 000754502D4C494E4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000000000000100000006466B34A4C101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001

```

```

nm-tool
NetworkManager Tool


State: connected (global)


- Device: wlan0  [AP-TVK 88/43] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:4F:78:00:02:54


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK:         Infra, 64:66:B3:4A:4C:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    *AP-TVK 88/43:   Infra, 00:27:19:E9:E1:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Waldi:           Infra, 00:1E:2A:63:6A:B8, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA


  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             208.67.222.222
    DNS:             208.67.220.220




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F4:6D:04:64:57:18


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

```

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

uname -a
Linux Kamil 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by sheldon-corey on 2014-11-11
try nohwcrypt or only use only one encryption type

---

### Post by kamil11 on 2014-11-12
What do you mean by one encryption type? How can I set it?

---

### Post by kamil11 on 2014-11-23
Ok, now I really need Ubuntu. Please help me. I don't know what to do.

---

### Post by Easy Limits on 2014-11-23
Try temporarily lowering your wireless security encryption level, at the router.

---

### Post by Bloodcage on 2014-11-23
how did you scan the several devices ??

---

