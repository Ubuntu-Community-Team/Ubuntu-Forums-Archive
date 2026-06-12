---
title: "Toshiba A120 Notebook, 7.10"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Aesir09 on 2007-12-15
hi, i purchased a toshiba a120 notebook on black friday, i have been using windows and have not gotten my wireless card working.

here are some commands that you may find useful :)


please help me get rid of vista :) :)
**lspci**
```

dom@dom-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by Aesir09 on 2007-12-15
lsmod
```

dom@dom-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  21140  0 
button                 10400  0 
container               6400  0 
ac                      7304  0 
sbs                    21520  0 
dock                   12264  0 
battery                12424  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
snd_hda_intel         337192  0 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
pcspkr                  4608  0 
k8temp                  7680  0 
i2c_piix4              11020  0 
uvcvideo               52228  0 
psmouse                45596  0 
compat_ioctl32         11136  1 uvcvideo
i2c_core               30208  1 i2c_piix4
sdhci                  21004  0 
serio_raw               9092  0 
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
mmc_core               33416  1 sdhci
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  5 
ext3                  146576  2 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
loop                   21764  4 
sg                     41384  0 
sd_mod                 32512  2 
ide_cd                 35488  1 
cdrom                  41768  1 ide_cd
atiixp                  7824  0 [permanent]
ide_core              141200  2 ide_cd,atiixp
r8169                  36100  0 
ahci                   27012  1 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ata_generic             9988  0 
libata                138928  2 ahci,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  4 uvcvideo,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

---

### Post by Aesir09 on 2007-12-15
lsusb
```

Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

---

