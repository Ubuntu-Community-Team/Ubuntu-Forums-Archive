---
title: "Very week WLAN signal on HP envy m6"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by Dominik_Bernhardt on 2014-01-26
Hello everyone! 
I just bought a HP ENVY m6 and installed Ubuntu 12.04 on it. The WLAN is working but the signal is very week, it often takes ages to download even small documents.  This is the output of sudo lshw -C network:

```
[FONT=Verdana]PCI (sysfs)  [/FONT]  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:07:00.2
       logical name: eth0
       version: 0a
       serial: 6c:3b:e5:7b:11:6c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 68:94:23:b7:41:13
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-35-generic firmware=0.37 ip=134.61.187.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
[FONT=Verdana]       resources: irq:17 memory:c1510000-c151ffff[/FONT]
```

I would be very grateful for any help or advise.

Greetings,
Dominik

---

### Post by praseodym on 2014-01-26
Please show the additional outputs of
```

ifconfig -a
iwconfig
lsmod
iwlist chan
sudo iwlist scan
dmesg | grep rt2
cat /etc/resolv.conf
```
Deactivate IPv6 in the network-manager WLAN profile and reconnect.

---

### Post by Dominik_Bernhardt on 2014-01-26
Thanks for your answer. 
```
**ifconfig -a**eth0      Link encap:Ethernet  HWaddr 6c:3b:e5:7b:11:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:504138 (504.1 KB)  TX bytes:504138 (504.1 KB)


wlan0     Link encap:Ethernet  HWaddr 68:94:23:b7:41:13  
          inet addr:134.61.159.95  Bcast:134.61.191.255  Mask:255.255.192.0
          inet6 addr: fe80::6a94:23ff:feb7:4113/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:483976310 (483.9 MB)  TX bytes:23232010 (23.2 MB)

**iwconfig**
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:84:87:3E:21   
          Bit Rate=43.3 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:467  Invalid misc:641   Missed beacon:0


**lsmod**
Module                  Size  Used by
bnep                   18399  2 
rfcomm                 47922  0 
bluetooth             247324  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_idt      71153  1 
coretemp               13596  0 
arc4                   12573  2 
rt2800pci              18754  0 
rt2800lib              67510  1 rt2800pci
uvcvideo               82214  0 
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14621  1 rt2800pci
kvm                   456261  0 
videobuf2_core         40815  1 uvcvideo
rt2x00lib              55643  3 rt2800pci,rt2800lib,rt2x00pci
videodev              130172  2 uvcvideo,videobuf2_core
ghash_clmulni_intel    13259  0 
videobuf2_vmalloc      13056  1 uvcvideo
snd_hda_intel          44339  5 
aesni_intel            55495  2 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
ablk_helper            13597  1 aesni_intel
mac80211              631450  3 rt2800lib,rt2x00pci,rt2x00lib
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13668  1 snd_hda_codec
lrw                    13323  1 aesni_intel
radeon                965747  1 
i915                  621477  3 
snd_pcm               102477  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aes_x86_64             17255  1 aesni_intel
snd_seq_midi           13324  0 
xts                    12951  1 aesni_intel
snd_rawmidi            30417  1 snd_seq_midi
gf128mul               14951  2 lrw,xts
ttm                    84183  1 radeon
cfg80211              526422  2 rt2x00lib,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
drm_kms_helper         49597  2 radeon,i915
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   287796  7 radeon,i915,ttm,drm_kms_helper
snd                    69533  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
microcode              23075  0 
hp_wmi                 18092  0 
joydev                 17613  0 
sparse_keymap          13890  1 hp_wmi
i2c_algo_bit           13564  2 radeon,i915
wmi                    19256  1 hp_wmi
mei                    45974  0 
psmouse                97902  0 
rtsx_pci_ms            13180  0 
memstick               16605  1 rtsx_pci_ms
video                  19652  1 i915
hp_accel               26012  0 
serio_raw              13215  0 
eeprom_93cx6           13344  1 rt2800pci
lis3lv02d              20200  1 hp_accel
mac_hid                13253  0 
input_polldev          13896  1 lis3lv02d
lpc_ich                17144  0 
nls_iso8859_1          12713  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17800  0 
r8169                  68904  0 
rtsx_pci               34530  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25879  3 
libahci                31636  1 ahci


**iwlist chan**
eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)



**sudo iwlist scan:**

eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:25:84:87:3E:21
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4645e4824
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 0B050200708D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F080010000000400001
                    IE: Unknown: 851E16008F000F00FF03590061702D73656D6939302D3330392D630002000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301002601
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C034A4CA99C239043010000140500000000F643E992DED24DDC
          Cell 02 - Address: 00:25:84:87:3E:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"mops"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4645e4824
                    Extra: Last beacon: 488ms ago
                    IE: Unknown: 00046D6F7073
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 7F080010000000400001
                    IE: Unknown: 851E25008F000F00FF03590061702D73656D6939302D3330392D630007000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301002601
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C034A4CD29E23904301000021A703000000022DBAA34F237D8A
          Cell 03 - Address: 00:23:EB:0C:27:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4679fd6d3
                    Extra: Last beacon: 27220ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 051300010408000000000000080000008000040000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 0B053200CD8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 7F080010000000400001
                    IE: Unknown: 851E28008F000F00FF03590061702D73656D6939302D3231322D630032000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301002601
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C034A4C445F22904301000062A4030000005277030CD106D671
          Cell 04 - Address: 00:23:EB:0C:27:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"mops"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4691ccadc
                    Extra: Last beacon: 2200ms ago
                    IE: Unknown: 00046D6F7073
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050B00010A0008000000000004
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 7F080010000000400001
                    IE: Unknown: 851E28008F000F00FF03590061702D73656D6939302D3231322D630032000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301002601
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C034A4C0D5F22904301000044A60300000039CACA3B4D0E89BF



**dmesg | grep rt2:** doesn't show any output

**cat /etc/resolv.conf **
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search eduroam.rwth-aachen.de

```

Deactivating [COLOR=#000000]IPv6 didn't change anything.

Greetings,
Dominik[/COLOR]

---

### Post by praseodym on 2014-01-26
There are two networks named "eduroam", one on channel 11 and another one on channel 1. Add the MAC-Address of your AP to "BSSID" in the network-manager profile, e.g. for Cell01:
```
          Cell 01 - Address: 00:25:84:87:3E:21
```

---

### Post by Dominik_Bernhardt on 2014-01-26
How do I get to know the MAC-Address of the AP? I'm at university and each floor has separate AP, shouldn't the MAC-Address change every time?

---

### Post by praseodym on 2014-01-26
Yes, you can check it with "sudo iwlist scan", change the MAC-address and reconnect

---

### Post by Dominik_Bernhardt on 2014-01-26
Unfortunately that doesn't help, the signal is as week as before. I tried both MAC Addresses and none improved the signal.

---

### Post by praseodym on 2014-01-26
Check:
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
This disables the hardware encryption of the driver

---

### Post by Dominik_Bernhardt on 2014-01-26
It seems that the problem is fixed now after disabling [COLOR=#000000]the hardware encryption[/COLOR], I'm going to test it for a while. Thanks a lot for your help and patience!
Greetings,
Dominik

---

