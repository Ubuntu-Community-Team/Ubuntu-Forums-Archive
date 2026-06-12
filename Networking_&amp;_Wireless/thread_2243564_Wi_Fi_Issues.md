---
title: "Wi Fi Issues"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Mathieu_Leclerc on 2014-09-09
HI , im new to the Linux world and i am currently using Ubuntu , Recently updated to 14.04 lts . i run it off my laptop to host a teamspeak server . i have root enabled and everything was working fine untill i did the 14.04 update. my wi fi seems to randomly disconnect and asks me to reenter my routers password . other times itll ask for my admin password. and sometimes i just cant find my router with in the list and have to reboot . this is a big nuisance since alot of people use my server and im loosing people fast with those random crashes . i tried deleting my connection and doing a new one . i downloaded wpa_gui and got it running under root but still my system crashes , i googled the symptoms and found nothing to help me . any and all help would be appreciated . 


P.S. i forgot to introduce myself . my name is matthew and a big everything PC enthousiast . glad to have joined this forum so far . thanks in advance for help

---

### Post by Mathieu_Leclerc on 2014-09-09
uname -a
```
Linux Server 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux

```

lspci -nnk
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
Subsystem: Dell Device [1028:01bd]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
Kernel driver in use: pcieport
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 01)
Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 01)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
Subsystem: Dell Device [1028:01bd]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515/M52 [Mobility Radeon X1300] [1002:7149]
Subsystem: Dell Device [1028:2003]
Kernel driver in use: radeon
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Inspiron 6400 [1028:01af]
Kernel driver in use: b44
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: firewire_ohci
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: sdhci-pci
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: r592
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
Subsystem: Dell Device [1028:01bd]
Kernel driver in use: r852
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
Subsystem: Intel Corporation Device [8086:1020]
Kernel driver in use: iwl3945

```


lsusb

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod
```
Module Size Used by
ctr 12905 3
ccm 17496 3
bnep 18895 2
rfcomm 53664 0
bluetooth 342208 10 bnep,rfcomm
gpio_ich 13229 0
dell_wmi 12665 0
sparse_keymap 13708 1 dell_wmi
dell_laptop 17808 0
dcdbas 14448 1 dell_laptop
arc4 12536 2
snd_hda_codec_idt 48877 1
radeon 1420570 3
snd_hda_intel 42730 3
iwl3945 63619 0
snd_hda_codec 164067 2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep 13272 1 snd_hda_codec
iwlegacy 88016 1 iwl3945
mac80211 546051 2 iwl3945,iwlegacy
snd_pcm 85501 2 snd_hda_codec,snd_hda_intel
r852 17722 0
snd_page_alloc 14230 2 snd_pcm,snd_hda_intel
snd_seq_midi 13132 0
sm_common 16772 1 r852
snd_seq_midi_event 14475 1 snd_seq_midi
cfg80211 409394 3 iwl3945,iwlegacy,mac80211
nand 58760 2 r852,sm_common
snd_rawmidi 25135 1 snd_seq_midi
nand_ecc 13136 1 nand
snd_seq 55383 2 snd_seq_midi_event,snd_seq_midi
nand_bch 13067 1 nand
bch 17197 1 nand_bch
ttm 72698 1 radeon
nand_ids 8547 1 nand
snd_seq_device 14137 3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper 47182 1 radeon
mtd 52813 2 nand,sm_common
snd_timer 28584 2 snd_pcm,snd_seq
drm 244037 5 ttm,drm_kms_helper,radeon
r592 17711 0
lpc_ich 16864 0
coretemp 13195 0
joydev 17101 0
snd 60939 16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
memstick 16174 1 r592
i2c_algo_bit 13197 1 radeon
serio_raw 13230 0
soundcore 12600 1 snd
wmi 18673 1 dell_wmi
mac_hid 13037 0
video 18903 0
parport_pc 31981 0
ppdev 17391 0
lp 13299 0
parport 40836 3 lp,ppdev,parport_pc
hid_logitech 22181 0
ff_memless 13325 1 hid_logitech
usbhid 47070 0
hid 87604 2 hid_logitech,usbhid
firewire_ohci 35529 0
sdhci_pci 18535 0
psmouse 91329 0
b44 31275 0
firewire_core 61867 1 firewire_ohci
crc_itu_t 12627 1 firewire_core
ssb 51854 1 b44
sdhci 37779 1 sdhci_pci
mii 13654 1 b44
```

iwconfig
```
wlan0 IEEE 802.11abg ESSID:"Roxy"
Mode:Managed Frequency:2.412 GHz Access Point: AC:F1F:61:2E:E9
Bit Rate=54 Mb/s Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=61/70 Signal level=-49 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:53 Invalid misc:17 Missed beacon:0

lo no wireless extensions.

eth0 no wireless extensions.

```

ifconfig -a

```
eth0 Link encap:Ethernet HWaddr 00:15:c5:b1:d2:2f
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2477 errors:0 dropped:0 overruns:0 frame:0
TX packets:2477 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:233561 (233.5 KB) TX bytes:233561 (233.5 KB)

wlan0 Link encap:Ethernet HWaddr 00:18:de:14:83:e2
inet addr:192.168.0.102 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::218:deff:fe14:83e2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:22248 errors:0 dropped:0 overruns:0 frame:0
TX packets:15384 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:9896386 (9.8 MB) TX bytes:2405554 (2.4 MB)

```

rfkill list
```
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
```

sudo iwlist scan

```
Cell 01 - Address: AC:F1F:61:2E:E9
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=61/70 Signal level=-49 dBm
Encryption keyn
ESSID:"Roxy"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000012b307ba1d2
Extra: Last beacon: 4ms ago
IE: Unknown: 0004526F7879
IE: Unknown: 010882848B960C121824
IE: Unknown: 030101
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
IE: Unknown: 3D1601001B00000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD940050F204104A00011010440001021057000101103B00010310470010130B38581DD211B28351B5118D836A1510210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D383235104200046E6F6E651054000800060050F2040001101100074449522D383235100800020084103C000103104900140024E26002000101600000020001600100020001
Cell 02 - Address: 00:26:50:A8:B3:41
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=31/70 Signal level=-79 dBm
Encryption keyn
ESSID:"bell420"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000014244181
Extra: Last beacon: 5092ms ago
IE: Unknown: 000762656C6C343230
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 050400010000
IE: Unknown: 0706555320010B1B
IE: Unknown: 2A0102
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32043048606C
Cell 03 - Address: 00:1E:58:3E:06:4B
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=25/70 Signal level=-85 dBm
Encryption keyn
ESSID:"gerasue"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s
Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000006a10a6842fd
Extra: Last beacon: 4368ms ago
IE: Unknown: 000767657261737565
IE: Unknown: 010882848B960C183048
IE: Unknown: 03010B
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 32041224606C
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

```

---

### Post by grahammechanical on 2014-09-09
This section of the forum is for those of us who are testing the next release of Ubuntu that is under development and that is Utopic Unicorn (14.10). You are using Ubuntu 14.04. You are in the wrong section. You should ask for this post to be moved to the Networking and Wireless section. In that section you may find posts similar to your post and solutions already found And you may also find forum members with knowledge of fixing wireless problems. That is not necessarily true of this section of the forum.

Regards.

---

### Post by mörgæs on 2014-09-09
Moved.

---

### Post by Mathieu_Leclerc on 2014-09-09
oops sorry for the inconvinience

---

### Post by varunendra on 2014-09-11
Welcome to the forums Mathieu_Leclerc ! :)

First of all, to make your post with the outputs cleaner and more readable, please edit it to change the [noparse]>  and..  tags to - ```
 and 
```[/noparse] respectively. To see how to use the 'CODE' tags properly and how it is useful, please follow the "Use Code Tags" link in my signature below.

Regarding the problem, may I assume this is your wireless Access-Point ? -
> **Mathieu_Leclerc said:**
> 
sudo iwlist scan
```
Cell 01 - Address: AC:F1F:61:2E:E9
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=61/70 Signal level=-49 dBm
Encryption key : on
**[COLOR="#0000FF"]ESSID:"Roxy"[/COLOR]**
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
....<snip>....
**IE: IEEE 802.11i/WPA2 Version 1**
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
**IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1**
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
....
```

If yes, please change the encryption type in the router/access-point to pure WPA2-PSK with AES (CCMP). As highlighted above, it is currently using WPA/WPA2 mixed mode, and weirdly, both using CCMP (WPA (1) requires TKIP). Reboot the router after saving the change.

If the above change doesn't solve the issue, Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

And while posting the outputs, please use this time for your own benefit.

**PS:**
Intel 3945 is quite an old card, and its driver/firmware keep running into bugs from time to time. If it is a commercial or production server, I recommend replacing it with a newer, better supported card. You may have to do some research on your own to figure out which cards are best supported currently. I personally use a card with Atheros AR9285 chip, and is working pretty good here, but I haven't tested it yet with the latest kernels (still using a much older one).

---

### Post by Mathieu_Leclerc on 2014-09-11
awsome , will try tonight and keep ya posted . it sometimes takes a days or 2 before crashing so ill give it a try for a few days

---

### Post by Mathieu_Leclerc on 2014-09-17
i decided to try what you suggested in your p.s since its the easiers to try , i had a ralink 11n usb wifi card wich im trying right now , been stable for 3 days so far . longest ive had it since the update . seems to be working fine . like you mentionned im guessing since its an older system i was having compatability issues .

---

### Post by varunendra on 2014-09-17
Sounds a good solution to me. The original card the problem and this thread started with couldn't get solved it seems, so I'm not sure whether we should call it 'Solved', but since the current solution is a reasonable one, I *think* you should mark the thread as [SOLVED] (using "Thread Tools" link above the top post) if it remains stable. :)

---

