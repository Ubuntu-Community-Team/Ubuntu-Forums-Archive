---
title: "Alfa AWUS036H Issues. Connected, but no browsing."
date: 2013-12-05
forum: Networking &amp; Wireless
---

### Post by jacobdtarr on 2013-12-05
Hello! I was wondering how I would be able to browse the internet on my computer. I am posting on it right now, but the problem is that it drops out a lot and that it has a pretty bad signal for what type of card it is. The network card is the Alfa AWUS036H. Help would be appreciated.

Machine: Gateway GT5082
Wireless brand/chipset: Alfa AWUS036H, Realtek RTL8187.
OS: Linux Mint Petra (Sorry i'm a noob. Is this allowed here?)
Kernel: 3.11.0-12-generic x86_64

Thanks again!

---

### Post by praseodym on 2013-12-05
Hi,
please show the terminal outputs of
```

lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
sudo iwlist scan
```
I recommend using pure WPA2-AES encryption, check the router manual

---

### Post by jacobdtarr on 2013-12-05
My network does not have an encryption right now :( I guess I should put one on.

lsusb
```
Bus 001 Device 010: ID 05dc:a817 Lexar Media, Inc. 
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 008: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 007: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 05ac:129e Apple, Inc. iPod Touch 4.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 003: ID 0566:3107 Monterey International Corp. Keyboard
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
binfmt_misc            17468  1 
ppdev                  17671  0 
arc4                   12608  2 
snd_intel8x0           38104  2 
snd_ac97_codec        130236  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm               102033  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         18710  2 snd_intel8x0,snd_pcm
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
dm_multipath           22843  0 
serio_raw              13413  0 
scsi_dh                14882  1 dm_multipath
snd_rawmidi            30095  1 snd_seq_midi
k8temp                 12978  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
edac_core              62312  0 
snd_timer              29433  2 snd_pcm,snd_seq
edac_mce_amd           22617  0 
snd                    69141  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
rtl8187                64909  0 
mac80211              596969  1 rtl8187
cfg80211              479757  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187
joydev                 17377  0 
nv_tco                 13564  0 
i2c_nforce2            13221  0 
parport_pc             32701  1 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
usb_storage            62062  2 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
pata_acpi              13038  0 
firewire_ohci          40060  0 
forcedeth              67371  0 
nouveau               943295  3 
firewire_core          64476  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sata_nv                27716  0 
pata_amd               18225  2 
ohci_pci               13561  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19318  1 nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    83995  1 nouveau
drm_kms_helper         52651  1 nouveau
drm                   296739  5 ttm,drm_kms_helper,nouveau


```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TarrNet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:D5:FD:1E   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:39   Missed beacon:0


```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:15:58:3e:1d:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25483 (25.4 KB)  TX bytes:25483 (25.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:40:ed:65  
          inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe40:ed65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3491868 (3.4 MB)  TX bytes:650016 (650.0 KB)


```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search ok.shawcable.net
```

sudo iwlist scan
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:D5:FD:1E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"TarrNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e890ebea44
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 0007546172724E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B0001031047001043F6FB1DEBC4E7400E6A2B820F18B3F010210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30341042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180206F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 02 - Address: 20:76:00:C4:7B:DC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"TELUS1183"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c973537a0
                    Extra: Last beacon: 6164ms ago
                    IE: Unknown: 000954454C555331313833
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B0001031047001030262747DFF76A0EBFF8225449B6175D1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000

```

Thanks so much for the help!

---

### Post by praseodym on 2013-12-06
Try a fixed channel and WPA2-AES

---

