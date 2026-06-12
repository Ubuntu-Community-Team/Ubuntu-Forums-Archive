---
title: "Slow network file sharing ... Fix needed"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by timmay on 2006-12-24
Can someone post how to fix the slow file transfer speed of smb shares. 1.1Mbits/s is just not acceptable on 100Mbits/s LAN. I've looked through the forum but I don't want to waste my time reading threads with people arguing about do you mean Mb/s and MB/s and all that rubbish.

Please can someone post the fix (nothing complex please).

---

### Post by ill0gical0ne on 2006-12-26
/bump

---

### Post by timmay on 2007-01-14
Bump again.

Ubuntu to Ubuntu file transfer is getting REALLY annoying now. I'm having to plug into Ethernet just to get ~3MB/s.

Surely I'm not the only person experiencing this problem. Is there no one that can help?

---

### Post by leju on 2007-01-16
Yes, I just discovered this too. Trying to transfer some videos across from my XP machine to my Ubuntu via Samba. I am getting max 4MB speed. As a side note. My CPU usage skyrockets whilst transferring too (55 - 100%) to use the network but it's caused by Nautilus process. Not cool, I will investigate. By the way I'm using Edgy.

---

### Post by Lucardo Mamones on 2007-01-17
I have the same problem, with ftp and rcp tops off at 10 Mbps.... havent seen the CPU usage but same result even using xover cable...

---

### Post by corax on 2007-01-17
Hi all ! :-)

Can you post me what is the output of:

```
sudo ethtool eth0
```

(Don't forget to replace eth0 with your ethernet interface ! :-) )

It isn't working on wireless cards (at least it is not working any of them I tried...) .

---

### Post by Lucardo Mamones on 2007-01-17
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

---

### Post by corax on 2007-01-17
To Lucardo

It is strange indeed it says your link is 100 Mbit full duplex so it should be really 100 Mbit :-)

can you please also post the output for these:

```
sudo lspci
```
and
```
sudo lsmod
```

Have you tried it with more than one machines or just one ?

bye

---

### Post by Lucardo Mamones on 2007-01-17
lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

lsmod:

Module                  Size  Used by
isofs                  38496  0
udf                    94756  0
usbhid                 42752  0
ipv6                  286976  34
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
xfs                   649696  1
exportfs                6528  1 xfs
dm_mod                 63256  6
md_mod                 76052  0
af_packet              24520  4
sr_mod                 17988  0
sbp2                   25060  0
ieee1394              306520  1 sbp2
lp                     12356  0
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            31128  0
gameport               16776  1 snd_via82xx
snd_ac97_codec        100224  1 snd_via82xx
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
snd_page_alloc         11304  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8640  1 snd_via82xx
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60004  11 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
floppy                 64676  0
soundcore              10784  1 snd
nvidia               4552660  12
pcspkr                  2244  0
parport_pc             37988  1
parport                39400  2 lp,parport_pc
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
i2c_viapro              9108  0
psmouse                40004  0
i2c_core               22848  3 i2c_acpi_ec,nvidia,i2c_viapro
8139cp                 24032  0
8139too                29056  0
mii                     6176  2 8139cp,8139too
serio_raw               7748  0
amd64_agp              13060  1
agpgart                36784  2 nvidia,amd64_agp
sg                     40160  0
evdev                  10176  1
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  2 sr_mod,ide_cd
ide_disk               19136  4
via82cxxx               9796  0 [permanent]
sd_mod                 20448  4
generic                 5124  0
sata_via               10340  4
libata                 83440  1 sata_via
scsi_mod              145960  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  71
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit


I have tried FTPing in with a windows machine to each of the boxe with the same result. Again, with a xover cable and via a switch. No change. 10 Mbps

---

### Post by corax on 2007-01-17
Sorry I have no more idea you have a realtek chip with the proper driver (8139too, 8139cp) ! it should work fine ! Maybe someone with more knowledge about the topic will come and enlighten us :-)

---

### Post by agds on 2007-02-03
I'm running into this same issue when streaming video to my PowerBook, connected over a wireless network, from a desktop running XP Home.  I haven't been able to get sharing working properly on my Ubuntu box, so I'm not sure if it would be the same there.

The videos are stored on an external hard drive, USB 2.0, so I wonder if that's holding me back.  I'll experiment with an internal drive I have lying around.

---

### Post by jbtito03 on 2007-02-03
What is your connection on the wireless and do you have usb 2.0 support?

What kind of tream are you talkin about anyway - which format and which programm?

Cheers

JB

---

