---
title: "firmware for b43-lpphy"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by K8xFGNF on 2013-10-21
I installed 12.10 on a dell 1545 and wireless card is not recognized. I researched it and found that I need to:
go to a wire connection to internet
open terminal and do
sudo apt-get update
sudo apt-get install firmare-b43-lpphy-installer

My question is do I need to go to a site first and access some repository before I run these commands?

thanks for the help.

---

### Post by Hadaka on 2013-10-21
Hi, no if you have the correct driver..it willjust load.
let's make sure you get the correct driver first.
please post the output of..
```
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by K8xFGNF on 2013-10-22
cby@cby-Inspiron-1545:~$ lspci -nnk | grep iA3 net
 grep: net: No such file or directory
  dell 1545 laptop
  cby@cby-Inspiron-1545:~$ lspci -vvnn | grep 14e4
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
  cby@cby-Inspiron-1545:~$ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:23:ae:11:bd:3b  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:18 
  lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:992 errors:0 dropped:0 overruns:0 frame:0
           TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:80928 (80.9 KB)  TX bytes:80928 (80.9 KB)
  cby@cby-Inspiron-1545:~$ iwconfig
 lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      IEEE 802.11  Access Point: Not-Associated   
           Link Quality:5  Signal level:0  Noise level:0
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0
  &#12288;
 cby@cby-Inspiron-1545:~$ lsmod
 Module                  Size  Used by
 nls_iso8859_1          12617  1 
 snd_hda_codec_idt      59761  1 
 snd_hda_intel          32515  3 
 snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
 snd_hwdep              13272  1 snd_hda_codec
 joydev                 17161  0 
 snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
 snd_seq_midi           13132  0 
 snd_rawmidi            25382  1 snd_seq_midi
 i915                  457161  3 
 snd_seq_midi_event     14475  1 snd_seq_midi
 snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
 bnep                   17707  2 
 snd_timer              24411  2 snd_pcm,snd_seq
 snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
 lib80211_crypt_tkip    17229  0 
 drm_kms_helper         45271  1 i915
 drm                   230463  4 i915,drm_kms_helper
 gpio_ich               13159  0 
 snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 wl                   2442848  0 
 soundcore              14599  1 snd
 psmouse                84843  0 
 coretemp               13168  0 
 microcode              18209  0 
 lib80211               14040  2 lib80211_crypt_tkip,wl
 rfcomm                 37276  0 
 dell_wmi               12601  0 
 dell_laptop            17161  0 
 sparse_keymap          13658  1 dell_wmi
 dcdbas                 14054  1 dell_laptop
 serio_raw              13031  0 
 wmi                    18590  1 dell_wmi
 i2c_algo_bit           13197  1 i915
 lpc_ich                16925  0 
 snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
 video                  18847  1 i915
 mac_hid                13037  0 
 bluetooth             183228  10 bnep,rfcomm
 parport_pc             31968  0 
 ppdev                  12817  0 
 lp                     13299  0 
 parport                40753  3 parport_pc,ppdev,lp
 sky2                   52926  0 
 ums_realtek            17669  0 
 uas                    17556  0 
 usb_storage            39350  2 ums_realtek
  &#12288;
 [    0.533903] agpgart-intel 0000:00:00.0: >AGP aperture is 256M @ 0xe0000000
 [    0.535355] brd: module loaded
 [    0.536142] loop: module loaded
 [    0.536277] ahci 0000:00:1f.2: >version 3.0
 [    0.536349] ahci 0000:00:1f.2: >irq 44 for MSI/MSI-X
 [    0.536409] ahci: SSS flag set, parallel bus scan disabled
 [    0.536453] ahci 0000:00:1f.2: >AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
 [    0.536457] ahci 0000:00:1f.2: >flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
 [    0.536463] ahci 0000:00:1f.2: >setting latency timer to 64
 [    0.560608] scsi0 : ahci
 [    0.560692] scsi1 : ahci
 [    0.560759] scsi2 : ahci
 [    0.560826] scsi3 : ahci
 [    0.560894] scsi4 : ahci
 [    0.560961] scsi5 : ahci
 [    0.561210] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 44
 [    0.561214] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 44
 [    0.561216] ata3: DUMMY
 [    0.561218] ata4: DUMMY
 [    0.561221] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 44
 [    0.561224] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 44
 [    0.561597] Fixed MDIO Bus: probed
 [    0.561649] tun: Universal TUN/TAP device driver, 1.6
 [    0.561651] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
 [    0.561745] PPP generic driver version 2.4.2
 [    0.561795] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 [    0.561849] ehci_hcd 0000:00:1a.7: >setting latency timer to 64
 [    0.561854] ehci_hcd 0000:00:1a.7: >EHCI Host Controller
 [    0.561861] ehci_hcd 0000:00:1a.7: >new USB bus registered, assigned bus number 1
 [    0.561898] ehci_hcd 0000:00:1a.7: >debug port 1
 [    0.565782] ehci_hcd 0000:00:1a.7: >cache line size of 64 is not supported
 [    0.565803] ehci_hcd 0000:00:1a.7: >irq 22, io mem 0xfed1c400
 [    0.576022] ehci_hcd 0000:00:1a.7: >USB 2.0 started, EHCI 1.00
 [    0.576066] usb usb1: >New USB device found, idVendor=1d6b, idProduct=0002
 [    0.576069] usb usb1: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.576073] usb usb1: >Product: EHCI Host Controller
 [    0.576075] usb usb1: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
 [    0.576077] usb usb1: >SerialNumber: 0000:00:1a.7
 [    0.576219] hub 1-0:1.0: >USB hub found
 [    0.576224] hub 1-0:1.0: >6 ports detected
 [    0.576329] ehci_hcd 0000:00:1d.7: >setting latency timer to 64
 [    0.576334] ehci_hcd 0000:00:1d.7: >EHCI Host Controller
 [    0.576340] ehci_hcd 0000:00:1d.7: >new USB bus registered, assigned bus number 2
 [    0.576368] ehci_hcd 0000:00:1d.7: >debug port 1
 [    0.580251] ehci_hcd 0000:00:1d.7: >cache line size of 64 is not supported
 [    0.580271] ehci_hcd 0000:00:1d.7: >irq 20, io mem 0xfed1c000
 [    0.592021] ehci_hcd 0000:00:1d.7: >USB 2.0 started, EHCI 1.00
 [    0.592039] usb usb2: >New USB device found, idVendor=1d6b, idProduct=0002
 [    0.592042] usb usb2: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.592045] usb usb2: >Product: EHCI Host Controller
 [    0.592047] usb usb2: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
 [    0.592050] usb usb2: >SerialNumber: 0000:00:1d.7
 [    0.592165] hub 2-0:1.0: >USB hub found
 [    0.592169] hub 2-0:1.0: >6 ports detected
 [    0.592256] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 [    0.592282] uhci_hcd: USB Universal Host Controller Interface driver
 [    0.592311] uhci_hcd 0000:00:1a.0: >setting latency timer to 64
 [    0.592315] uhci_hcd 0000:00:1a.0: >UHCI Host Controller
 [    0.592320] uhci_hcd 0000:00:1a.0: >new USB bus registered, assigned bus number 3
 [    0.592352] uhci_hcd 0000:00:1a.0: >irq 20, io base 0x00006f60
 [    0.592388] usb usb3: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.592391] usb usb3: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.592393] usb usb3: >Product: UHCI Host Controller
 [    0.592396] usb usb3: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.592398] usb usb3: >SerialNumber: 0000:00:1a.0
 [    0.592508] hub 3-0:1.0: >USB hub found
 [    0.592513] hub 3-0:1.0: >2 ports detected
 [    0.592595] uhci_hcd 0000:00:1a.1: >setting latency timer to 64
 [    0.592599] uhci_hcd 0000:00:1a.1: >UHCI Host Controller
 [    0.592605] uhci_hcd 0000:00:1a.1: >new USB bus registered, assigned bus number 4
 [    0.592645] uhci_hcd 0000:00:1a.1: >irq 21, io base 0x00006f80
 [    0.592681] usb usb4: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.592684] usb usb4: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.592686] usb usb4: >Product: UHCI Host Controller
 [    0.592689] usb usb4: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.592691] usb usb4: >SerialNumber: 0000:00:1a.1
 [    0.592799] hub 4-0:1.0: >USB hub found
 [    0.592804] hub 4-0:1.0: >2 ports detected
 [    0.592889] uhci_hcd 0000:00:1a.2: >setting latency timer to 64
 [    0.592894] uhci_hcd 0000:00:1a.2: >UHCI Host Controller
 [    0.592899] uhci_hcd 0000:00:1a.2: >new USB bus registered, assigned bus number 5
 [    0.592929] uhci_hcd 0000:00:1a.2: >irq 22, io base 0x00006fa0
 [    0.592965] usb usb5: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.592967] usb usb5: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.592970] usb usb5: >Product: UHCI Host Controller
 [    0.592972] usb usb5: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.592975] usb usb5: >SerialNumber: 0000:00:1a.2
 [    0.593082] hub 5-0:1.0: >USB hub found
 [    0.593086] hub 5-0:1.0: >2 ports detected
 [    0.593164] uhci_hcd 0000:00:1d.0: >setting latency timer to 64
 [    0.593168] uhci_hcd 0000:00:1d.0: >UHCI Host Controller
 [    0.593173] uhci_hcd 0000:00:1d.0: >new USB bus registered, assigned bus number 6
 [    0.593204] uhci_hcd 0000:00:1d.0: >irq 20, io base 0x00006f00
 [    0.593242] usb usb6: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.593245] usb usb6: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.593247] usb usb6: >Product: UHCI Host Controller
 [    0.593250] usb usb6: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.593252] usb usb6: >SerialNumber: 0000:00:1d.0
 [    0.593361] hub 6-0:1.0: >USB hub found
 [    0.593365] hub 6-0:1.0: >2 ports detected
 [    0.593448] uhci_hcd 0000:00:1d.1: >setting latency timer to 64
 [    0.593452] uhci_hcd 0000:00:1d.1: >UHCI Host Controller
 [    0.593458] uhci_hcd 0000:00:1d.1: >new USB bus registered, assigned bus number 7
 [    0.593485] uhci_hcd 0000:00:1d.1: >irq 21, io base 0x00006f20
 [    0.593521] usb usb7: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.593524] usb usb7: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.593526] usb usb7: >Product: UHCI Host Controller
 [    0.593529] usb usb7: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.593531] usb usb7: >SerialNumber: 0000:00:1d.1
 [    0.593643] hub 7-0:1.0: >USB hub found
 [    0.593647] hub 7-0:1.0: >2 ports detected
 [    0.593725] uhci_hcd 0000:00:1d.2: >setting latency timer to 64
 [    0.593730] uhci_hcd 0000:00:1d.2: >UHCI Host Controller
 [    0.593735] uhci_hcd 0000:00:1d.2: >new USB bus registered, assigned bus number 8
 [    0.593764] uhci_hcd 0000:00:1d.2: >irq 22, io base 0x00006f40
 [    0.593800] usb usb8: >New USB device found, idVendor=1d6b, idProduct=0001
 [    0.593802] usb usb8: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [    0.593805] usb usb8: >Product: UHCI Host Controller
 [    0.593807] usb usb8: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
 [    0.593809] usb usb8: >SerialNumber: 0000:00:1d.2
 [    0.593917] hub 8-0:1.0: >USB hub found
 [    0.593921] hub 8-0:1.0: >2 ports detected
 [    0.594059] usbcore: registered new interface driver libusual
 [    0.594113] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
 [    0.613166] i8042: Detected active multiplexing controller, rev 1.1
 [    0.625329] serio: i8042 KBD port at 0x60,0x64 irq 1
 [    0.625335] serio: i8042 AUX0 port at 0x60,0x64 irq 12
 [    0.625365] serio: i8042 AUX1 port at 0x60,0x64 irq 12
 [    0.625392] serio: i8042 AUX2 port at 0x60,0x64 irq 12
 [    0.625415] serio: i8042 AUX3 port at 0x60,0x64 irq 12
 [    0.625527] mousedev: PS/2 mouse device common for all mice
 [    0.626194] rtc_cmos 00:04: >RTC can wake from S4
 [    0.626348] rtc_cmos 00:04: >rtc core: registered rtc_cmos as rtc0
 [    0.626382] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
 [    0.626445] device-mapper: uevent: version 1.0.3
 [    0.626509] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
 [    0.626549] EISA: Probing bus 0 at eisa.0
 [    0.626551] EISA: Cannot allocate resource for mainboard
 [    0.626553] Cannot allocate resource for EISA slot 1
 [    0.626555] Cannot allocate resource for EISA slot 2
 [    0.626557] Cannot allocate resource for EISA slot 3
 [    0.626558] Cannot allocate resource for EISA slot 4
 [    0.626560] Cannot allocate resource for EISA slot 5
 [    0.626562] Cannot allocate resource for EISA slot 6
 [    0.626563] Cannot allocate resource for EISA slot 7
 [    0.626565] Cannot allocate resource for EISA slot 8
 [    0.626566] EISA: Detected 0 cards.
 [    0.626616] cpuidle: using governor ladder
 [    0.626667] cpuidle: using governor menu
 [    0.626669] EFI Variables Facility v0.08 2004-May-17
 [    0.626855] ashmem: initialized
 [    0.626995] TCP: cubic registered
 [    0.627106] NET: Registered protocol family 10
 [    0.627304] NET: Registered protocol family 17
 [    0.627316] Key type dns_resolver registered
 [    0.627394] Using IPI No-Shortcut mode
 [    0.627484] PM: Hibernation image not present or could not be loaded.
 [    0.627498] registered taskstats version 1
 [    0.630139] Key type trusted registered
 [    0.632395] Key type encrypted registered
 [    0.635356]   Magic number: 1:960:51
 [    0.635472] rtc_cmos 00:04: >setting system clock to 2013-10-19 00:03:05 UTC (1382140985)
 [    0.636767] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
 [    0.636769] EDD information not available.
 [    0.653627] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
 [    0.850357] isapnp: No Plug & Play device found
 [    0.916100] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 [    0.916126] usb 1-5: >new high-speed USB device number 2 using ehci_hcd
 [    0.983392] ata1.00: ATA-8: TOSHIBA MK1652GSX, LV011D, max UDMA/100
 [    0.983395] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
 [    0.984318] ata1.00: configured for UDMA/100
 [    0.984479] scsi 0:0:0:0: >Direct-Access     ATA      TOSHIBA MK1652GS LV01 PQ: 0 ANSI: 5
 [    0.984614] sd 0:0:0:0: >[sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
 [    0.984634] sd 0:0:0:0: >Attached scsi generic sg0 type 0
 [    0.984657] sd 0:0:0:0: >[sda] Write Protect is off
 [    0.984661] sd 0:0:0:0: >[sda] Mode Sense: 00 3a 00 00
 [    0.984680] sd 0:0:0:0: >[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 [    1.058994] usb 1-5: >New USB device found, idVendor=0bda, idProduct=0158
 [    1.058998] usb 1-5: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
 [    1.059000] usb 1-5: >Product: USB2.0-CRW
 [    1.059003] usb 1-5: >Manufacturer: Generic
 [    1.059005] usb 1-5: >SerialNumber: 20071114173400000
 [    1.065544] Initializing USB Mass Storage driver...
 [    1.065611] usbcore: registered new interface driver usb-storage
 [    1.065612] USB Mass Storage support registered.
 [    1.078881]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
 [    1.079471] sd 0:0:0:0: >[sda] Attached SCSI disk
 [    1.304070] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 [    1.324000] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633C, DW50, max UDMA/100
 [    1.324015] ata2.00: applying bridge limits
 [    1.342358] ata2.00: configured for UDMA/100
 [    1.344840] scsi 1:0:0:0: >CD-ROM            TSSTcorp DVD+-RW TS-L633C DW50 PQ: 0 ANSI: 5
 [    1.349182] sr0: scsi3-mmc drive: 24x/62x writer dvd-ram cd/rw xa/form2 cdda tray
 [    1.349184] cdrom: Uniform CD-ROM driver Revision: 3.20
 [    1.349313] sr 1:0:0:0: >Attached scsi CD-ROM sr0
 [    1.349407] sr 1:0:0:0: >Attached scsi generic sg1 type 5
 [    1.668087] ata5: SATA link down (SStatus 0 SControl 300)
 [    1.988067] ata6: SATA link down (SStatus 0 SControl 300)
 [    1.988163] Freeing unused kernel memory: 756k freed
 [    1.988570] Write protecting the kernel text: 5960k
 [    1.988600] Write protecting the kernel read-only data: 2424k
 [    1.988601] NX-protecting the kernel data: 4280k
 [    2.009429] udevd[106]: starting version 175
 [    2.129070] usbcore: registered new interface driver uas
 [    2.141826] scsi6 : usb-storage 1-5:1.0
 [    2.141939] usbcore: registered new interface driver ums-realtek
 [    2.152078] sky2: driver version 1.30
 [    2.152174] sky2 0000:09:00.0: >Yukon-2 FE+ chip revision 0
 [    2.152301] sky2 0000:09:00.0: >irq 45 for MSI/MSI-X
 [    2.156069] sky2 0000:09:00.0: >eth0: addr 00:23:ae:11:bd:3b
 [    2.658128] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
 [    3.142268] scsi 6:0:0:0: >Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
 [    3.143459] sd 6:0:0:0: >Attached scsi generic sg2 type 0
 [    3.147006] sd 6:0:0:0: >[sdb] Attached SCSI removable disk
 [    4.853896] Adding 3104764k swap on /dev/sda6.  Priority:-1 extents:1 across:3104764k 
 [    5.168934] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
 [    6.126497] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
 [    7.166466] udevd[428]: starting version 175
 [    8.240628] lp: driver loaded but no devices found
 [    8.240632] ppdev: user-space parallel port driver
 [    8.533071] Bluetooth: Core ver 2.16
 [    8.533113] NET: Registered protocol family 31
 [    8.533115] Bluetooth: HCI device and connection manager initialized
 [    8.533117] Bluetooth: HCI socket layer initialized
 [    8.533119] Bluetooth: L2CAP socket layer initialized
 [    8.533124] Bluetooth: SCO socket layer initialized
 [    8.754481] type=1400 audit(1382162593.614:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=459 comm="apparmor_parser"
 [    8.755050] type=1400 audit(1382162593.614:3): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=459  comm="apparmor_parser"
 [    8.804496] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts  with Region \_SB_.PCI0.VID_.TCOI 1 (20120320/utaddress-251)
 [    8.804505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
 [    8.804508] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
 [    8.815334] wmi: Mapper loaded
 [    8.823544] dcdbas dcdbas: >Dell Systems Management Base Driver (version 5.6.0-3.2)
 [    8.836371] input: Dell WMI hotkeys as /devices/virtual/input/input4
 [    8.867508] Bluetooth: RFCOMM TTY layer initialized
 [    8.867514] Bluetooth: RFCOMM socket layer initialized
 [    8.867516] Bluetooth: RFCOMM ver 1.11
 [    8.873464] lib80211: common routines for IEEE802.11 drivers
 [    8.873468] lib80211_crypt: registered algorithm 'NULL'
 [    8.880518] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa3
 [    9.223642] wl: module license 'MIXED/Proprietary' taints kernel.
 [    9.223648] Disabling lock debugging due to kernel taint
 [    9.262617] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa3
 [    9.265648] microcode: Microcode Update Driver: v2.00 <[EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL]>, Peter Oruba
 [    9.280723] gpio_ich: GPIO from 195 to 255 on gpio_ich
 [    9.298804] [drm] Initialized drm 1.1.0 20060810
 [    9.321239] lib80211_crypt: registered algorithm 'TKIP'
 [    9.322050] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.112
 [    9.376418] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
 [    9.376424] Bluetooth: BNEP filters: protocol multicast
 [    9.642317] i915 0000:00:02.0: >setting latency timer to 64
 [    9.643172] i915 0000:00:02.0: >irq 46 for MSI/MSI-X
 [    9.643189] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
 [    9.643190] [drm] Driver supports precise vblank timestamp query.
 [    9.643246] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
 [    9.792119] i915: fixme: max PWM is zero
 [   10.115909] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input5
 [   10.142830] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input6
 [   10.222233] fbcon: inteldrmfb (fb0) is primary device
 [   10.222456] Console: switching to colour frame buffer device 170x48
 [   10.222493] fb0: inteldrmfb frame buffer device
 [   10.222495] drm: registered panic notifier
 [   10.282068] acpi device:3a: >registered as cooling_device2
 [   10.282520] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
 [   10.284379] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
 [   10.284614] [Firmware Bug]: Duplicate ACPI video bus devices for  the same VGA controller, please try module parameter  "video.allow_duplicates=1"if the current driver doesn't work.
 [   10.286563] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
 [   10.356582] init: failsafe main process (675) killed by TERM signal
 [   10.865446] snd_hda_intel 0000:00:1b.0: >irq 47 for MSI/MSI-X
 [   10.993700] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
 [   10.993882] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
 [   15.630047] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
 [   15.635797] sky2 0000:09:00.0: >eth0: enabling interface
 [   15.636154] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   15.636920] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   19.066411] type=1400 audit(1382162603.930:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=920 comm="apparmor_parser"
  [   19.066802] type=1400 audit(1382162603.930:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=920 comm="apparmor_parser"
  [   19.074120] type=1400 audit(1382162603.934:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=921 comm="apparmor_parser"
  [   19.074294] type=1400 audit(1382162603.934:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=922 comm="apparmor_parser"
  [   19.074498] type=1400 audit(1382162603.934:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=921 comm="apparmor_parser"
  [   19.074661] type=1400 audit(1382162603.934:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=922 comm="apparmor_parser"
  [   19.088878] type=1400 audit(1382162603.950:10): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=923  comm="apparmor_parser"
 [   19.089380] type=1400 audit(1382162603.950:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=923 comm="apparmor_parser"
  [   19.089634] type=1400 audit(1382162603.950:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=923 comm="apparmor_parser"
 [   19.097165] type=1400 audit(1382162603.958:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=926 comm="apparmor_parser"
 [   19.515367] init: alsa-restore main process (966) terminated with status 99
 [   53.780651] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [   53.782754] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [   53.782758] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  105.496945] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  105.499050] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  105.499059] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  157.208949] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  157.211063] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  157.211071] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  208.920715] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  208.922823] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  208.922835] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  260.632845] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  260.634963] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  260.634972] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  299.988098] [Hardware Error]: Machine check events logged
 [  312.344856] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  312.346974] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  312.346983] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  364.056870] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  364.059103] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  364.059111] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  415.768876] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  415.771113] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  415.771121] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  467.480888] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  467.483004] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  467.483013] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  519.192897] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  519.195009] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  519.195017] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  570.904909] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  570.907021] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  570.907029] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  622.616666] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  622.618780] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  622.618789] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  674.328800] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  674.330913] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  674.330922] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  726.040812] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  726.043054] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  726.043062] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  777.752953] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  777.755065] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  777.755074] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  829.464958] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  829.467074] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  829.467082] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  881.176849] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  881.178956] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  881.178965] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  932.888850] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  932.890966] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  932.890974] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [  984.600741] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [  984.602850] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [  984.602858] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1036.312748] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1036.314850] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1036.314858] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1088.024760] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1088.026997] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1088.027005] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1139.737018] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1139.739138] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1139.739146] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1191.448902] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1191.451021] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1191.451030] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1243.160789] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1243.162909] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1243.162917] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1294.872674] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1294.874787] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1294.874796] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1346.584808] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1346.586924] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1346.586932] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1398.296699] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1398.298807] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1398.298815] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1450.008827] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1450.011070] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1450.011078] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1501.720971] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1501.723080] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1501.723088] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1553.432979] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1553.435093] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1553.435101] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1605.144987] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1605.147099] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1605.147107] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1656.856869] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1656.858986] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1656.858995] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1708.568753] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1708.570869] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1708.570877] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1744.140111] usb 2-1: >new high-speed USB device number 2 using ehci_hcd
 [ 1744.283576] usb 2-1: >New USB device found, idVendor=0951, idProduct=1603
 [ 1744.283584] usb 2-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
 [ 1744.283590] usb 2-1: >Product: DataTraveler 2.0
 [ 1744.283595] usb 2-1: >Manufacturer: Kingston
 [ 1744.283601] usb 2-1: >SerialNumber: 0014780F99515B8C0E090124
 [ 1744.287037] scsi7 : usb-storage 2-1:1.0
 [ 1745.285634] scsi 7:0:0:0: >Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
 [ 1745.287411] sd 7:0:0:0: >Attached scsi generic sg3 type 0
 [ 1747.503112] sd 7:0:0:0: >[sdc] [15798272 512]("tel:15798272%20512")-byte logical blocks: (8.08 GB/7.53 GiB)
 [ 1747.503730] sd 7:0:0:0: >[sdc] Write Protect is off
 [ 1747.503739] sd 7:0:0:0: >[sdc] Mode Sense: 23 00 00 00
 [ 1747.504334] sd 7:0:0:0: >[sdc] No Caching mode page present
 [ 1747.504341] sd 7:0:0:0: >[sdc] Assuming drive cache: write through
 [ 1747.508217] sd 7:0:0:0: >[sdc] No Caching mode page present
 [ 1747.508226] sd 7:0:0:0: >[sdc] Assuming drive cache: write through
 [ 1747.508966]  sdc: sdc1
 [ 1747.514330] sd 7:0:0:0: >[sdc] No Caching mode page present
 [ 1747.514340] sd 7:0:0:0: >[sdc] Assuming drive cache: write through
 [ 1747.514347] sd 7:0:0:0: >[sdc] Attached SCSI removable disk
 [ 1760.280892] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1760.283002] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1760.283011] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1811.988632] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1811.990752] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1811.990758] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1863.705033] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1863.707150] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1863.707159] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1915.416924] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1915.419036] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1915.419044] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 1967.128802] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 1967.130920] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 1967.130929] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [[ 2018.840826]("tel:%5B%202018.840826")] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [[ 2018.842932]("tel:%5B%202018.842932")] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [[ 2018.842941]("tel:%5B%202018.842941")] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 2070.552829] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 2070.555086] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 2070.555096] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [[ 2122.264835]("tel:%5B%202122.264835")] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [[ 2122.266954]("tel:%5B%202122.266954")] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [[ 2122.266962]("tel:%5B%202122.266962")] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [[ 2173.976968]("tel:%5B%202173.976968")] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [[ 2173.979107]("tel:%5B%202173.979107")] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [[ 2173.979117]("tel:%5B%202173.979117")] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 2225.688982] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 2225.691094] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 2225.691102] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
 [ 2277.400866] sd 6:0:0:0: >[sdb] Test WP failed, assume Write Enabled
 [ 2277.402982] sd 6:0:0:0: >[sdb] Asking for cache data failed
 [ 2277.402991] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
  &#12288;
 cby@cby-Inspiron-1545:~$ sudo lshw -C network
 [sudo] password for cby: 
   *-network DISABLED      
        description: Wireless interface
        product: BCM4312 802.11b/g LP-PHY
        vendor: Broadcom Corporation
        physical id: 0
        bus info: pci@0000:0c:00.0
        logical name: eth1
        version: 01
        serial: 00:23:4e:10:fb:61
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 latency=0 multicast=yes wireless=IEEE 802.11bg
        resources: irq:17 memory:f69fc000-f69fffff
   *-network
        description: Ethernet interface
        product: 88E8040 PCI-E Fast Ethernet Controller
        vendor: Marvell Technology Group Ltd.
        physical id: 0
        bus info: pci@0000:09:00.0
        logical name: eth0
        version: 13
        serial: 00:23:ae:11:bd:3b
        capacity: 100Mbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
        resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  cby@cby-Inspiron-1545:~$ iwlist scan
 lo        Interface doesn't support scanning.
  eth0      Interface doesn't support scanning.
  eth1      Interface doesn't support scanning.
  cby@cby-Inspiron-1545:~$ lsb_release -d
 Description:	Ubuntu 12.10
 cby@cby-Inspiron-1545:~$ uname -mr
 3.5.0-17-generic i686
  cby@cby-Inspiron-1545:~$ sudo /etc/init.d/networking restart
 system crashed/locked up - I was not able to retrieve any data

---

### Post by Hadaka on 2013-10-22
Hi,please open a terminal  ctrl/alt/t
then COPY and paste in one command line at a time.
```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe wl
```
thanks.

---

