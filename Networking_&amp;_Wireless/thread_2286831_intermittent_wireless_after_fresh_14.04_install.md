---
title: "intermittent wireless after fresh 14.04 install"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by brouhaha_gewgaw on 2015-07-14
This is a continuation (of sorts) to this thread: [http://ubuntuforums.org/showthread.php?t=2286666&p=13321244#post13321244](http://ubuntuforums.org/showthread.php?t=2286666&p=13321244#post13321244)

My WiFi is uneven-- I can go for days without a problem, then go for days without internet. I keep getting signed out, get a password prompt for our WiFi, our WiFi tries to reconnect but fails. Sometimes, if I'm lucky, it takes me one to several reboots to be able to sign in, but sometimes I have to turn the WiFi off and on one to several times. I was going to update and upgrade, as it says in the forum sticky, but I ran into problems setting up an Ethernet connection. As I'd posted in that other thread, instead of my Ethernet connecting automatically when I plugged it in I got a "Disconnected--you are now offline" message and the slot in the router(?) (wireless device?) I'd plugged the cable into doesn't light up. But my Ethernet appeared under my Wired Connections. Since I have no idea about the router (if that's the correct term), for lack of a better way to put it, which button do I push?

---

### Post by Moofus on 2015-07-15
who is the manufacturer of your wireless card?

---

### Post by brouhaha_gewgaw on 2015-07-15
My laptop's an Asus x401u. In case this might be relevant, I'd dropped my laptop around 3 times, though, but I haven't had parts replaced because of them (everything seemed to be in working order)-- though I had to replace my hard drive (bad sectors) once in what I thought wad an unrelated incident.

---

### Post by praseodym on 2015-07-15
Please show the terminal outputs of these commands
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
ifconfig -a
route -n
iwconfig
lsmod
iwlist chan
sudo iwlist scan
```

---

### Post by brouhaha_gewgaw on 2015-07-16
Sorry for sounding too much of a newbie, but I'd just reinstalled again, thinking it might just be something in my last install. I haven't tried the Ethernet yet. Do I input those commands with the Ethernet attached, or after I'd gotten a Wired connection identified by my laptop?

---

### Post by praseodym on 2015-07-16
No, without cable.

---

### Post by brouhaha_gewgaw on 2015-07-16
```
home@home:~$ uname -a
Linux home 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686 athlon i686 GNU/Linux
```
```
home@home:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7340] [1002:9808]
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
    Kernel driver in use: snd_hda_intel
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1512]
    Kernel driver in use: pcieport
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7812] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 14)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller [1022:780c]
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1c93]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.7 SD Host controller [0805]: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller [1022:7806]
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: sdhci-pci
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) [1022:43a0]
    Kernel driver in use: pcieport
00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1) [1022:43a1]
    Kernel driver in use: pcieport
00:15.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 3) [1022:43a3]
    Kernel driver in use: pcieport
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: r8169
07:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. Device [105b:e055]
    Kernel driver in use: rt2800pci
07:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
    Subsystem: Foxconn International, Inc. Device [105b:e056]
home@home:~$ lsusb
Bus 002 Device 002: ID 0bda:5705 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
home@home:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 30:85:a9:76:b6:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:[deleted bec looks like our ip? dunno, just in case.]  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:219145 (219.1 KB)  TX bytes:219145 (219.1 KB)

wlan0     Link encap:Ethernet  HWaddr 68:94:23:3e:ba:3b  
          inet addr:[see above]  Bcast:[this too]  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe3e:ba3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17133885 (17.1 MB)  TX bytes:1692513 (1.6 MB)
```

```
home@home:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [deleted]     0.0.0.0         UG    0      0        0 wlan0
[ditto]     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
home@home:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"[deleted]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:33:D0:77:97   
          Bit Rate=13.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1588  Invalid misc:7439   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

```
home@home:~$ lsmod
Module                  Size  Used by
ctr                    12905  1 
ccm                    17496  1 
dm_crypt               22653  0 
bnep                   18895  2 
rfcomm                 58045  0 
bluetooth             391253  10 bnep,rfcomm
asus_nb_wmi            16862  0 
asus_wmi               23414  1 asus_nb_wmi
6lowpan_iphc           18262  1 bluetooth
sparse_keymap          13708  1 asus_wmi
arc4                   12536  2 
rt2800pci              13398  0 
rt2800mmio             16189  1 rt2800pci
rt2800lib              83150  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48886  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              559049  3 rt2x00lib,rt2x00pci,rt2800lib
uvcvideo               71465  0 
kvm_amd                50814  0 
snd_hda_codec_realtek    65903  1 
kvm                   388518  1 kvm_amd
snd_hda_codec_generic    62873  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     46396  1 
videobuf2_vmalloc      13048  1 uvcvideo
snd_hda_intel          29285  5 
videobuf2_memops       13170  1 videobuf2_vmalloc
cfg80211              418811  2 mac80211,rt2x00lib
snd_hda_controller     29944  1 snd_hda_intel
videobuf2_core         48344  1 uvcvideo
snd_hda_codec         120371  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13272  1 snd_hda_codec
joydev                 17113  0 
v4l2_common            15132  1 videobuf2_core
videodev              131265  3 uvcvideo,v4l2_common,videobuf2_core
eeprom_93cx6           13168  1 rt2800pci
media                  20899  2 uvcvideo,videodev
crc_ccitt              12627  1 rt2800lib
serio_raw              13251  0 
snd_pcm                87194  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
k10temp                12976  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  1 snd_seq_midi
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28648  2 snd_pcm,snd_seq
snd                    66670  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              17734  0 
soundcore              14599  2 snd,snd_hda_codec
shpchp                 32143  0 
parport_pc             32021  0 
ppdev                  17391  0 
mac_hid                13059  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12901  0 
hid_generic            12503  0 
usbhid                 47035  0 
hid                    95946  2 hid_generic,usbhid
psmouse                91236  0 
radeon               1308261  3 
ahci                   25622  1 
sdhci_pci              18640  0 
r8169                  61579  0 
mii                    13654  1 r8169
sdhci                  38345  1 sdhci_pci
pata_atiixp            13066  0 
libahci                26970  1 ahci
i2c_algo_bit           13197  1 radeon
wmi                    18689  1 asus_wmi
ttm                    76999  1 radeon
drm_kms_helper         55007  1 radeon
drm                   255469  6 ttm,drm_kms_helper,radeon
video                  19475  1 asus_wmi
```
```
home@home:~$ iwlist chan
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
          Current Frequency=2.462 GHz (Channel 11)

lo        no frequency information.

eth0      no frequency information.
```

```
home@home:~$ sudo iwlist scan
[sudo] password for home: 
wlan0     Scan completed :
          Cell 01 - Address: 00:13:33:D0:77:97
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"[deleted]"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000095c42d9f8
                    Extra: Last beacon: 692ms ago
                    IE: Unknown: 000B504C4454484F4D4544534C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

By the way, I tried the "grep -iA2 net" right after the "lspci -nnk", but, thinking the terminal hung on me and that I was supposed to type the lspci OR grep command (correct me if I'm wrong), I exited out of that terminal window and opened a new one. Sorry, haven't had my coffee yet.

---

### Post by praseodym on 2015-07-16
Change the encryption mode to pure WPA2-AES (CCMP) and to a fixed channel, check the router manual.

---

### Post by brouhaha_gewgaw on 2015-07-16
Thanks. By the way, will this affect other users I'm sharing the WiFi with?

---

### Post by praseodym on 2015-07-16
Normally not, if you are not changing the ESSID or PW.

---

### Post by brouhaha_gewgaw on 2015-07-18
Sorry for the late reply. Unfortunately, no one can find the manual (I also tried Googling). Does anyone know of someone familiar with BaudTec RN243R4-2T2R-A6, or at least other things that can be done?

---

### Post by brouhaha_gewgaw on 2015-07-21
Since I couldn't find the manual, I called our ISP. They wouldn't tell me how, (a technician came and all) and told me to get my wireless seen by a computer technician. The only thing I got was "it's your laptop alone that has a problem, it's the one that's got to get checked. Oh, and it might be a virus." I'm a bit short on cash at the moment, so, uh, would it be quicker and cheaper in the end if I get the wireless card changed?

---

