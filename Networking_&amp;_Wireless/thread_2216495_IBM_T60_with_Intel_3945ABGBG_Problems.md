---
title: "IBM T60 with Intel 3945ABG/BG Problems"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by DadoTheCat on 2014-04-12
Hi all,
I own a IBM T60 (Modell G5U-2007) running Ubuntu flawlesly since 2008.
Since a week, perhaps after an update,  it can't detect my Wifi-AP anymore, while other devices can. It only sees some AP's from my neighbours.
I figured out, that it might be a Firmware Issue with the non-free drivers of this Intel NIC.

I tried disabeling 802.11n, but no succes.

sudo nano /etc/modprobe.d/intel-6300.conf
contains only : 'options iwlwifi 11n_disable=1'

I'm confused about its telling me about 5 Ghz Channels, but imho this Chipset hasn't the 5Ghz feature.
iwlist wlan0 channel 
```
wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
```



lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515/M54 [Mobility Radeon X1400]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```



lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```





dmesg | egrep -i '(wlan0|3945)'
```
[    1.113945] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[   48.031089] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   48.031094] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   48.031162] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   48.085501] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   48.085508] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   48.085584] iwl3945 0000:03:00.0: irq 47 for MSI/MSI-X
[   48.123319] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   55.038809] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   55.110910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.111350] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.685734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

lspci -nnk | grep -i net -A2
```
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad T60 [17aa:2001]
    Kernel driver in use: e1000e
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation Device [8086:1010]
    Kernel driver in use: iwl3945
rob@rob-T60:/etc/modprobe.d$ 
```

dmesg | grep iw
```
[   48.031089] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   48.031094] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   48.031162] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   48.085501] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   48.085508] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   48.085584] iwl3945 0000:03:00.0: irq 47 for MSI/MSI-X
[   48.123319] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   55.038809] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

```



iwlist wlan0 scan  (My Wifi-AP not shown, also it's about 50cm away from T60).
Result nothing OR:
```
wlan0     Scan completed :
          Cell 01 - Address: BC:05:43:D1:07:6F
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Griffith"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dd8cc180
                    Extra: Last beacon: 28076ms ago
                    IE: Unknown: 00084772696666697468
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
```


ifconfig 
```
eth0      Link encap:Ethernet  Hardware Adresse 00:16:41:xx:xx:xx 
          inet Adresse:192.168.xxxxx  Bcast:192.168.xxxxx  Maske:255.255.255.0
          inet6-Adresse: 2001:xxxxxxxxxxxxxxxxx/64 Gültigkeitsbereich:Global
          inet6-Adresse: fe80::2xxxxxxxxxxxxxxxx/64 Gültigkeitsbereich:Verbindung
          inet6-Adresse: 2001:4xxx:xxxxxxxxxxxx/64 Gültigkeitsbereich:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:28636 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:21567 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:27665665 (27.6 MB)  TX-Bytes:3403403 (3.4 MB)
          Interrupt:16 Speicher:ee000000-ee020000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:2822 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:2822 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:258449 (258.4 KB)  TX-Bytes:258449 (258.4 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:18:de:2c:ba:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)
```


iwconfig 
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.
```


iwconfig wlan0
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

 lsmod
```
Module                  Size  Used by
vesafb                 13500  1 
tp_smapi               22943  0 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               285205  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13074  3 
hdaps                  14550  1 
thinkpad_ec            14139  2 hdaps,tp_smapi
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
btusb                  23443  0 
bluetooth             323656  11 bnep,btusb,rfcomm
coretemp               13195  0 
kvm                   368975  0 
joydev                 17097  0 
binfmt_misc            13140  1 
pcmcia                 51368  0 
microcode              18894  0 
snd_hda_codec_analog    75656  1 
psmouse                90642  0 
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
serio_raw              13189  0 
thinkpad_acpi          73347  0 
nvram                  13986  1 thinkpad_acpi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
arc4                   12536  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
radeon               1312332  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              517444  2 iwl3945,iwlegacy
yenta_socket           40193  0 
lpc_ich                16864  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ttm                    75982  1 radeon
cfg80211              401762  3 iwl3945,iwlegacy,mac80211
pcmcia_rsrc            18319  1 yenta_socket
drm_kms_helper         46867  1 radeon
snd_timer              24447  2 snd_pcm,snd_seq
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm                   242400  3 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
nsc_ircc               22475  0 
irda                  107345  1 nsc_ircc
snd                    60790  13 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
crc_ccitt              12627  1 irda
mac_hid                13037  0 
video                  18777  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
ahci                   25579  2 
e1000e                223181  0 
libahci                26619  1 ahci
ptp                    18156  1 e1000e
pps_core               18546  1 ptp
```

lsmod | egrep 'wl|iw'
```
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              517444  2 iwl3945,iwlegacy
cfg80211              401762  3 iwl3945,iwlegacy,mac80211

```


dmesg
 ```
0.733975] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.733981] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.734011] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    0.734051] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.734055] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.734058] usb usb5: Product: UHCI Host Controller
[    0.734061] usb usb5: Manufacturer: Linux 3.11.0-19-generic uhci_hcd
[    0.734064] usb usb5: SerialNumber: 0000:00:1d.3
[    0.734182] hub 5-0:1.0: USB hub found
[    0.734187] hub 5-0:1.0: 2 ports detected
[    0.734389] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.742262] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.742269] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.742410] mousedev: PS/2 mouse device common for all mice
[    0.742594] rtc_cmos 00:06: RTC can wake from S4
[    0.742751] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.742786] rtc_cmos 00:06: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.742880] device-mapper: uevent: version 1.0.3
[    0.742963] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.742992] platform eisa.0: Probing EISA bus 0
[    0.742997] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.743000] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.743004] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.743007] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.743010] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.743013] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.743017] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.743020] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.743023] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.743026] platform eisa.0: EISA: Detected 0 cards
[    0.743036] cpufreq-nforce2: No nForce2 chipset.
[    0.743096] cpuidle: using governor ladder
[    0.743179] cpuidle: using governor menu
[    0.743192] ledtrig-cpu: registered to indicate activity on CPUs
[    0.743328] TCP: cubic registered
[    0.743474] NET: Registered protocol family 10
[    0.743746] NET: Registered protocol family 17
[    0.743760] Key type dns_resolver registered
[    0.743987] Using IPI No-Shortcut mode
[    0.744103] PM: Hibernation image not present or could not be loaded.
[    0.744108] Loading module verification certificates
[    0.749355] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: dc76185d2ae5997387e7fb78078a8a42ed21701f'
[    0.749373] registered taskstats version 1
[    0.751631] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.752925] Key type trusted registered
[    0.755316] Key type encrypted registered
[    0.758536] AppArmor: AppArmor sha1 policy hashing enabled
[    0.759021]   Magic number: 10:216:424
[    0.759142] rtc_cmos 00:06: setting system clock to 2014-04-12 09:26:20 UTC (1397294780)
[    0.760349] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.760352] EDD information not available.
[    0.884407] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4247N, 1.01, max UDMA/33
[    0.900283] ata1.00: configured for UDMA/33
[    1.059367] isapnp: No Plug & Play device found
[    1.063777] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4247N 1.01 PQ: 0 ANSI: 5
[    1.068880] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.068883] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.069057] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.069195] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.069748] Freeing unused kernel memory: 880K (c1973000 - c1a4f000)
[    1.069820] Write protecting the kernel text: 6368k
[    1.069967] Write protecting the kernel read-only data: 2696k
[    1.069969] NX-protecting the kernel data: 5920k
[    1.084920] systemd-udevd[99]: starting version 204
[    1.113940] pps_core: LinuxPPS API ver. 1 registered
[    1.113945] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.121620] PTP clock support registered
[    1.141602] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.141608] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.141638] e1000e 0000:02:00.0: Disabling ASPM L0s L1
[    1.141642] e1000e 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.141832] e1000e 0000:02:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.141876] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.148164] ahci 0000:00:1f.2: version 3.0
[    1.148302] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.148388] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    1.148393] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.148399] ahci 0000:00:1f.2: setting latency timer to 64
[    1.149137] scsi2 : ahci
[    1.149252] scsi3 : ahci
[    1.149340] scsi4 : ahci
[    1.149435] scsi5 : ahci
[    1.149536] ata3: SATA max UDMA/133 abar m1024@0xee404400 port 0xee404500 irq 46
[    1.149539] ata4: DUMMY
[    1.149541] ata5: DUMMY
[    1.149543] ata6: DUMMY
[    1.260041] e1000e 0000:02:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:16:41:aa:4b:45
[    1.260048] e1000e 0000:02:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.260125] e1000e 0000:02:00.0 eth0: MAC: 2, PHY: 2, PBA No: 005301-003
[    1.436053] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    1.468067] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.470596] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.470601] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.472701] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.472705] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.475208] ata3.00: ATA-7: FUJITSU MHV2080BH, 00840028, max UDMA/100
[    1.475212] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.479751] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.479755] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.481764] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.481768] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.484355] ata3.00: configured for UDMA/100
[    1.484568] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 0084 PQ: 0 ANSI: 5
[    1.484799] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.484846] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.485013] sd 2:0:0:0: [sda] Write Protect is off
[    1.485017] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.485097] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.546084]  sda: sda1 sda2 sda3 sda4
[    1.546684] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.613083] usb 5-2: New USB device found, idVendor=0483, idProduct=2016
[    1.613089] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.613092] usb 5-2: Product: Biometric Coprocessor
[    1.613095] usb 5-2: Manufacturer: STMicroelectronics
[    2.151497] EXT3-fs (sda4): recovery required on readonly filesystem
[    2.151503] EXT3-fs (sda4): write access will be enabled during recovery
[   18.338205] kjournald starting.  Commit interval 5 seconds
[   18.349638] EXT3-fs (sda4): recovery complete
[   18.349642] EXT3-fs (sda4): mounted filesystem with ordered data mode
[   45.778541] Adding 1461908k swap on /dev/sda3.  Priority:-1 extents:1 across:1461908k FS
[   47.416890] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.515642] systemd-udevd[277]: starting version 204
[   47.685518] lp: driver loaded but no devices found
[   47.777179] acpi device:06: registered as cooling_device2
[   47.777250] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   47.777369] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input4
[   47.778143] NET: Registered protocol family 23
[   47.786333] nsc-ircc 00:09: [io  0x02f8-0x02ff]
[   47.786415] nsc-ircc 00:09: [irq 3]
[   47.786419] nsc-ircc 00:09: [dma 1]
[   47.797870] nsc-ircc 00:09: activated
[   47.799737] nsc-ircc, chip->init
[   47.799753] nsc-ircc, Found chip at base=0x164e
[   47.799794] nsc-ircc, driver loaded (Dag Brattli)
[   47.801194] IrDA: Registered device irda0
[   47.801199] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   47.867201] [drm] Initialized drm 1.1.0 20060810
[   47.891137] intel_rng: FWH not detected
[   47.929484] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMIO 1 (20130517/utaddress-251)
[   47.929494] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   47.929500] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20130517/utaddress-251)
[   47.929505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   47.929507] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20130517/utaddress-251)
[   47.929512] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   47.929514] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   47.935997] cfg80211: Calling CRDA to update world regulatory domain
[   47.970949] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:2012]
[   47.970979] yenta_cardbus 0000:15:00.0: Using INTVAL to route CSC interrupts to PCI
[   47.970982] yenta_cardbus 0000:15:00.0: Routing CardBus interrupts to PCI
[   47.970990] yenta_cardbus 0000:15:00.0: TI: mfunc 0x01d01002, devctl 0x64
[   47.971479] leds_ss4200: no LED devices found
[   48.000481] type=1400 audit(1397294827.739:2): apparmor="STATUS" operation="profile_load" parent=310 profile="unconfined" name="/sbin/dhclient" pid=324 comm="apparmor_parser"
[   48.000493] type=1400 audit(1397294827.739:3): apparmor="STATUS" operation="profile_load" parent=310 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=324 comm="apparmor_parser"
[   48.000500] type=1400 audit(1397294827.739:4): apparmor="STATUS" operation="profile_load" parent=310 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"
[   48.001359] type=1400 audit(1397294827.739:5): apparmor="STATUS" operation="profile_replace" parent=310 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=324 comm="apparmor_parser"
[   48.001369] type=1400 audit(1397294827.739:6): apparmor="STATUS" operation="profile_replace" parent=310 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"
[   48.001830] type=1400 audit(1397294827.739:7): apparmor="STATUS" operation="profile_replace" parent=310 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"
[   48.009420] [drm] radeon userspace modesetting enabled.
[   48.016874] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   48.016880] [drm] No driver support for vblank timestamp query.
[   48.016884] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:00.0 on minor 0
[   48.031089] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   48.031094] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   48.031162] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   48.085501] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   48.085508] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   48.085584] iwl3945 0000:03:00.0: irq 47 for MSI/MSI-X
[   48.119345] Non-volatile memory driver v1.3
[   48.123319] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   48.131121] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   48.131127] thinkpad_acpi: http://ibm-acpi.sf.net/
[   48.131129] thinkpad_acpi: ThinkPad BIOS 79ETE7WW (2.27 ), EC 79HT50WW-1.07
[   48.131131] thinkpad_acpi: Lenovo ThinkPad T60, model 2007G5U
[   48.131784] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   48.132041] thinkpad_acpi: radio switch found; radios are enabled
[   48.132060] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   48.132062] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   48.145833] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   48.149188] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   48.149358] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   48.150787] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input5
[   48.184766] hda_intel: probe_mask set to 0x1 for device 17aa:2010
[   48.184819] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   48.214013] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cf0, PCI irq 16
[   48.214021] yenta_cardbus 0000:15:00.0: Socket status: 30000007
[   48.214029] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io  0xa000-0xdfff]
[   48.214033] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xdfff:
[   48.220251] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   48.215636]  excluding 0xa000-0xa0ff 0xa400-0xa4ff
[   48.248934] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xe4300000-0xe7ffffff]
[   48.248942] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe4300000-0xe7ffffff:
[   48.248945]  excluding 0xe4300000-0xe46cffff
[   48.248958] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xe0000000-0xe3ffffff 64bit pref]
[   48.248962] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0000000-0xe3ffffff:
[   48.248976]  excluding 0xe0000000-0xe3ffffff
[   48.360970] EXT3-fs (sda4): using internal journal
[   48.912541] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000/0x0, board id: 71, fw id: 67352
[   48.912550] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   48.950832] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   49.048040] usb 5-1: new full-speed USB device number 3 using uhci_hcd
[   49.222076] usb 5-1: New USB device found, idVendor=0a5c, idProduct=2110
[   49.222081] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   49.222085] usb 5-1: Product: BCM2045B
[   49.222088] usb 5-1: Manufacturer: Broadcom Corp
[   49.296427] microcode: CPU1 sig=0x6e8, pf=0x20, revision=0x39
[   49.318699] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   49.393527] kvm: disabled by bios
[   49.506649] cfg80211: World regulatory domain updated:
[   49.506655] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   49.506658] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.506661] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.506664] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.506666] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.506669] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.708908] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   49.710187]  excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   49.711115] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   49.711590]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   49.712057] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   49.712789]  clean.
[   49.712809] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   49.713625]  clean.
[   49.713652] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   49.713659]  excluding 0xc0000-0xd3fff 0xdc000-0xfffff
[   49.713688] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   49.713700]  excluding 0xa0000000-0xa0ffffff
[   49.713721] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   49.713733]  excluding 0x60000000-0x60ffffff
[   49.713753] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   49.714588]  clean.
[   49.796048] init: failsafe main process (549) killed by TERM signal
[   49.932925] Bluetooth: Core ver 2.16
[   49.932957] NET: Registered protocol family 31
[   49.932959] Bluetooth: HCI device and connection manager initialized
[   49.938160] Bluetooth: HCI socket layer initialized
[   49.938167] Bluetooth: L2CAP socket layer initialized
[   49.938180] Bluetooth: SCO socket layer initialized
[   49.958769] Bluetooth: RFCOMM TTY layer initialized
[   49.958787] Bluetooth: RFCOMM socket layer initialized
[   49.958789] Bluetooth: RFCOMM ver 1.11
[   49.982922] usbcore: registered new interface driver btusb
[   49.997269] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.997275] Bluetooth: BNEP filters: protocol multicast
[   49.997287] Bluetooth: BNEP socket layer initialized
[   50.277579] type=1400 audit(1397294830.015:8): apparmor="STATUS" operation="profile_load" parent=738 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=743 comm="apparmor_parser"
[   50.277592] type=1400 audit(1397294830.015:9): apparmor="STATUS" operation="profile_load" parent=738 profile="unconfined" name="chromium_browser" pid=743 comm="apparmor_parser"
[   50.278297] type=1400 audit(1397294830.015:10): apparmor="STATUS" operation="profile_replace" parent=738 profile="unconfined" name="chromium_browser" pid=743 comm="apparmor_parser"
[   50.279992] type=1400 audit(1397294830.015:11): apparmor="STATUS" operation="profile_load" parent=738 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=744 comm="apparmor_parser"
[   50.976097] ppdev: user-space parallel port driver
[   51.085792] init: avahi-cups-reload main process (767) terminated with status 1
[   52.174949] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   52.325755] thinkpad_ec: module verification failed: signature and/or required key missing - tainting kernel
[   52.326145] thinkpad_ec: thinkpad_ec 0.41 loaded.
[   52.326739] hdaps: LENOVO ThinkPad T60 detected, setting orientation 1
[   52.326869] hdaps: initial mode latch is 0x01
[   52.326993] hdaps: setting ec_rate=250, filter_order=2
[   52.327212] hdaps: device successfully initialized.
[   52.327294] input: ThinkPad HDAPS joystick emulation as /devices/virtual/input/input7
[   52.327451] input: ThinkPad HDAPS accelerometer data as /devices/virtual/input/input8
[   52.327536] hdaps: driver successfully loaded.
[   52.519788] init: gdm main process (881) killed by TERM signal
[   53.415349] vboxdrv: Found 2 processor cores.
[   53.417522] vboxdrv: fAsync=1 offMin=0x89814 offMax=0x89814
[   53.420581] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   53.420585] vboxdrv: Successfully loaded version 4.2.16_Ubuntu (interface 0x001a0005).
[   53.472061] vboxpci: IOMMU not found (not registered)
[   53.631234] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   53.847891] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   54.730920] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[   54.832124] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[   54.832637] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.833155] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.026859] tp_smapi 0.41 loading...
[   55.027356] tp_smapi successfully loaded (smapi_port=0xb2).
[   55.038809] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   55.110910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.111350] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.633009] thinkpad_acpi: setting the hotkey mask to 0x00ffffff is likely not the best way to go about it
[   55.633014] thinkpad_acpi: please consider using the driver defaults, and refer to up-to-date thinkpad-acpi documentation
[   55.669123] init: plymouth-stop pre-start process (1243) terminated with status 1
[   55.700103] usb 5-1: USB disconnect, device number 3
[   56.310618] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   56.310796] e1000e 0000:02:00.0 eth0: 10/100 speed: disabling TSO
[   56.310893] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.108426] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   58.108432] vesafb: scrolling: redraw
[   58.108435] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   58.108851] vesafb: framebuffer at 0xd8000000, mapped to 0xf8c80000, using 5824k, total 5824k
[   58.109375] Console: switching to colour frame buffer device 175x65
[   58.109382] fb0: VESA VGA frame buffer device
[   58.169612] init: plymouth-splash main process (1395) terminated with status 1
[  354.809617] audit_printk_skb: 171 callbacks suppressed
[  354.809623] type=1400 audit(1397295134.545:69): apparmor="STATUS" operation="profile_replace" parent=2757 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2761 comm="apparmor_parser"
[  354.809637] type=1400 audit(1397295134.545:70): apparmor="STATUS" operation="profile_replace" parent=2757 profile="unconfined" name="/usr/sbin/cupsd" pid=2761 comm="apparmor_parser"
[  354.810626] type=1400 audit(1397295134.545:71): apparmor="STATUS" operation="profile_replace" parent=2757 profile="unconfined" name="/usr/sbin/cupsd" pid=2761 comm="apparmor_parser"
[  789.511454] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[  789.612209] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[  789.612755] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  789.685734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```[  791.222655] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  791.222838] e1000e 0000:02:00.0 eth0: 10/100 speed: disabling TSO
[/CODE]

sudo lshw -C network
```
  *-network               
       Beschreibung: Ethernet interface
       Produkt: 82573L Gigabit Ethernet Controller
       Hersteller: Intel Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: eth0
       Version: 00
       Seriennummer: 00:16:41:aa:4b:45
       Größe: 100Mbit/s
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.5-1 ip=192.168.79.20 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       Ressourcen: irq:45 memory:ee000000-ee01ffff ioport:3000(Größe=32)
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: PRO/Wireless 3945ABG [Golan] Network Connection
       Hersteller: Intel Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Logischer Name: wlan0
       Version: 02
       Seriennummer: 00:18:de:2c:ba:5f
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=iwl3945 driverversion=3.11.0-19-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       Ressourcen: irq:47 memory:edf00000-edf00fff
```


sudo iwlist wlan0 scan
```
wlan0     No scan results
```

lsb_release -d
Description:    Ubuntu 13.10

uname -mr
3.11.0-19-generic i686

sudo service networking restart
Result X-Server Crash, only black Screen with Mouse Cross. (Thanks to the Auto-Save Feature here :) )

Searching the Web did't help me, altough this Problem occours since many Years, I'm not able to adopt a way to get rid of this Problem. Thanks in advance!

---

### Post by chili555 on 2014-04-12
> I'm confused about its telling me about 5 Ghz Channels, but imho this Chipset hasn't the 5Ghz feature.IMHO, it does. Not 802.11N but, instead 802.11A. > Intel Corporation PRO/Wireless 3945[COLOR="#FF0000"]A[/COLOR]BG [Golan] Network Connection (rev 02)[http://en.wikipedia.org/wiki/802.11a](http://en.wikipedia.org/wiki/802.11a)> The 802.11a amendment to the original standard was ratified in 1999. The 802.11a standard uses the same core protocol as the original standard, operates in 5 GHz band,> I tried disabeling 802.11n, but no succes.

sudo nano /etc/modprobe.d/intel-6300.conf
contains only : 'options iwlwifi 11n_disable=1'As your device doesn't use the driver iwlwifi, this is useless. Let's remove it:```
sudo rm /etc/modprobe.d/intel-6300.conf
```I own and use successfully two Intel wireless devices including a T60 and Intel 3945. I have honed a few techniques in years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

I also suggest you set Network Manager to ignore IPv6 in the wireless section only: [https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  Although this illustration refers to wired ethernet, I suggest you only ignore IPv6 in wireless.

---

### Post by tgalati4 on 2014-04-12
I have a Thinkpad T43p with the same card.  It's possible that you have an antenna problem.  Try removing the card, reseating, blowing out the dust.  Carfully reseat the 2 antenna connections.  Because the antennas run through the hinge into the bezel, they may have worn out.  No way to fix that without major disassembly.  You have 6 years of laptop use, which is twice the average life of a laptop.

---

### Post by DadoTheCat on 2014-04-12
Ok Thanks Chili!
I removed the iwlwifi file. Yes you are all right, 802.11a is the 5Ghz Band, I couldn't belive this old Thinkpad can do this... ;)

My Router is a FritzBox it does WPA2 CCMP-AES, I disabled the so called 'high Bandwith for Video' Feature, which should disable the 40Mhz Channels.

> **chili555 said:**
> 

... I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

I'm in Germany, DE. The European ETSI allows us to use the Channel 1-13 in the 2,4Ghz Band. After manually switching to a Channel between 1-11 my Router is shown in the Networkmanager! I remember this Problem in early days with some US-Drivers only allowing Channel 1-11.

> **chili555 said:**
> 
Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```

Yes it was '00'. My Regulatory Output changed from:
```

 country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
rob@rob-T60:~$ sudo iw reg set DE
rob@rob-T60:~$ sudo iw reg get
country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
```

Do you know what the 'N/A' means? (was '3' before).

> **chili555 said:**
> 
Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

Ok I did (DE instead of IS), the settings survived the reboot ;).

But when I compare the the output from *dmesg | egrep 'iw'* it still tells me the same as before:

```
iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels

```
Do you know a way to change it back to the full 1-13 Channel ETSI setting?

And generally: Has somthing 'fundamental' changed in the Linux Kernel or Driver Framework in the last days? I still wonder why this Wifi Chip was running perfectly for 7 Years and than suddenly this wired problem.

Many Greetings from Germany to Island :)

---

### Post by DadoTheCat on 2014-04-12
> It's possible that you have an antenna problem.  
I blowed the dust from the interior several months ago, because the fan got loud and the T60 quite hot ;) After cleaning there didn't occour any problems. I can't see my AP which is 50 cm away from the antenna, but can see AP's 2-3 houses away in the street.
> You have 6 years of laptop use, which is twice the average life of a laptop. 				
Yes and I'm still in love with it :) Let us hope that we have many Years of fun and stability with our Thinkpads ....

---

### Post by chili555 on 2014-04-12
> After manually switching to a Channel between 1-11 my Router is shown in the Networkmanager! I remember this Problem in early days with some US-Drivers only allowing Channel 1-11.What does this tell us?```
sudo iwlist wlan0 chan
```Mine, located in the US, says:```
wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=5.805 GHz (Channel 161)
```Is it possible that your T60 came from the US or some non-channel 12 and 13 locale? 

We might try setting the domain in cfg80211:```
gksudo gedit /etc/modprobe.d/cfg80211.conf
```Add a single line:```
options cfg80211 ieee80211_regdom=DE
```Proofread carefully, save and close gedit. Reboot and check:```
sudo iwlist wlan0 chan
```

Then you might go back to /etc/rc.local and comment out the line you added:```
[COLOR="#FF0000"]#[/COLOR]iw reg set IS
```> Many Greetings from Germany to IslandI assume you meant Iceland; I actually live in the USA. I just use Iceland as an example. Next month, I may use Antarctica.> I still wonder why this Wifi Chip was running perfectly for 7 Years and than suddenly this wired problem.I haven't any idea.

---

### Post by tgalati4 on 2014-04-12
The other thing to consider is simple interference.  A lot of tablets and smartphones floating around, each using WiFi.  

Perhaps there is an interference robustness setting:

```
modinfo iwl3545
```

filename:       /lib/modules/2.6.28-19-generic/kernel/drivers/net/wireless/ipw2200.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
..
depends:        ieee80211
vermagic:       2.6.28-19-generic SMP mod_unload modversions 586 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default on) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           **antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)**

My wireless card is actually an older Intel ABG:  

0b:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

Try setting just one antenna and see if you can see your local AP and not the ones down the street.  Something changed your wireless gains.  Sometimes pulling the battery out of the laptop for an hour will reset the antenna trims.

If this machine is dual-boot in Windows, look for the Intel wireless diagnostics and run them.  Also check the BIOS for wireless power settings--uncheck any sleep settings.

---

### Post by DadoTheCat on 2014-04-14
> **chili555 said:**
> What does this tell us?

While my Wifi-AP is on Channel 12 or 13 it's not recognized by my Intel 3945ABG/BG Wifi Chipset. I disabled Channel 12 and 13, returned to 'Auto-Channel' and had a stable connection the last hours. (This Problem could also occur for e.g. People from North America visiting Europe.)

> **chili555 said:**
> 
```
sudo iwlist wlan0 chan
```Mine, located in the US, says:```
wlan0     24 channels in total; available frequencies :
...
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
  ..
          Channel 165 : 5.825 GHz
          Current Frequency=5.805 GHz (Channel 161)
```

We might try setting the domain in cfg80211:```
gksudo gedit /etc/modprobe.d/cfg80211.conf
```Add a single line:```
options cfg80211 ieee80211_regdom=DE
```Proofread carefully, save and close gedit. Reboot and check:```
sudo iwlist wlan0 chan
```

Then you might go back to /etc/rc.local and comment out the line you added:```
[COLOR=#FF0000]#[/COLOR]iw reg set IS
```

My /etc/modprobe.d/cfg80211.conf is now one line with 'options cfg80211 ieee80211_regdom=DE'.

I also commented out the 'iw reg set DE'. (I rebooted with and without the commented out /etc/rc.local).

iw reg keeps the 'DE' setting:

```
sudo iw reg get
country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
```

But the 'iwlist wlan0 chan' output is the same as before. 

 ```
sudo iwlist wlan0 chan
wlan0     19 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.432 GHz (Channel 5)
```

> Is it possible that your T60 came from the US or some non-channel 12 and 13 locale? 
I'm not sure, it has a German Keyboard, but was bought from a second hand / refurbished Reseller.

---

### Post by DadoTheCat on 2014-04-14
> **tgalati4 said:**
> 

Perhaps there is an interference robustness setting:

```
modinfo iwl3545
```

Do you see something like this here? :

```
modinfo iwl3945 
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     35209C1F4B317C0961FADAF
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)
```


> 
If this machine is dual-boot in Windows, look for the Intel wireless diagnostics and run them.  Also check the BIOS for wireless power settings--uncheck any sleep settings.

I'll do this next. Do you think a BIOS Reset would be usefull?

```
Sometimes pulling the battery out of the laptop for an hour will reset the antenna trims. 
```
While the Laptop is powered off?

---

### Post by chili555 on 2014-04-14
> it has a German Keyboard, but was bought from a second hand / refurbished Reseller.That's my suspicion; that the wireless card within was manufactured to be used in a country that doesn't allow channels 12 and 13. Please see: [http://wireless.kernel.org/en/developers/Regulatory](http://wireless.kernel.org/en/developers/Regulatory)> For some hardware, regulatory permissions are programmed into the EEPROM, these can be observed as well, depending on the driver. Some drivers rely on EEPROM values for enforcement or calibration and drivers can continue to rely on these values by filtering the CRDA data according to the EEPROM settings. For these type of drivers, CRDA provides an extra layer of regulatory compliance, for instance when the card is in a laptop that roams between countries.I am assuming, in this context, that 'programmed into the EEPROM' means that the availability to send and receive on channels 12 and 13 and, probably, several other features, is burned into the silicon and not switchable by the driver or manageable by the router. 

I'm not an EEPROM guy, so some of this is speculation and some is based on a few years of experience.

---

### Post by tgalati4 on 2014-04-14
Yes, with the laptop off, pull the battery pack out of the bottom for an hour.  Sometimes, wireless cards retain digital trim settings which can interfere with operation.  Check to see if there is a BIOS update from IBM/Lenovo.  It's possible that you have developed a BIOS problem.  It's also possible that your wireless router has developed a problem.  Running high-frequency signals can cause circuit aging.  Do other devices connect to your wireless router OK?

---

### Post by DadoTheCat on 2014-04-14
> ...look for the Intel wireless diagnostics and run them.  Also check the  BIOS for wireless power settings--uncheck any sleep settings. 				
I run Intel Wireless Diagnostics from booted XP. All test passed, all green. Then i enforced Channel 13 on my Wifi-AP and suddenly the Router disappeared again. The same behaviour as on Ubuntu, so this is imho more a Card / Firmware Issue then a software problem (?).

---

### Post by DadoTheCat on 2014-04-14
Yes Chili555, i think your conclusion is right - it's more hardware related.
I bought this T60 while working as an technican for an ISP how opperates several tousend Wifi-APs. 
I was the person responsible for the Wifi-APs. (Shame on me - i forgot a lot in the last years...like 802.11a ;) )
And I'm nearly 100% sure that I used Chan 12 + 13 a lot (and testet it with this T60). 
After so many Years I finally recognize that Ch 12 + 13 are not usable, thats so unlikely.

BUT: One year ago I upgraded the RAM to 4Gb, and I did a BIOS Upgrade! Perhaps this is the clue: The Bios Upgrade made (undocumented) changes to the Wifi-Card EEPROM ? Or Perhaps I catched an US Bios....

---

### Post by DadoTheCat on 2014-04-14
> **tgalati4 said:**
>   It's also possible that your wireless router has developed a problem.  Running high-frequency signals can cause circuit aging.  Do other devices connect to your wireless router OK?

Yes: All other Devices had no problems, but 
No an Acer Lapptop running Ubuntu 12.04 LTS had the same Problem, Channel 12 + 13 disapered, i guess after an automatic Update. It's not my Lapptop. 

I fixed it with:

```
sudo apt-get purge bcmwl-kernel-source to remove the non-working one. Then run 
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

Got this from archive:
[HTML]http://ubuntuforums.org/archive/index.php/t-2159331.html [/HTML]

After doing this this machine runns perfektly again, even on Ch 12 or 13.

So I thought i could fix this T60 as simple as the other Acer.....

---

### Post by chili555 on 2014-04-14
> sudo apt-get purge bcmwl-kernel-source to remove the non-working one. Then run 
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installerCertainly if you had installed conflicting Broadcom drivers, there is a strong possibility that there was a conflict. I'm glad it's working by any means.

---

### Post by tgalati4 on 2014-04-14
Installing US BIOS on a DE machine might cause that issue.  Try to find a DE BIOS and flash that and see how the wireless works.

---

