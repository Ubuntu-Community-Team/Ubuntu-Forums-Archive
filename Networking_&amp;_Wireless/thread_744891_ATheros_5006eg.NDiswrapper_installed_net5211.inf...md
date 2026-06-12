---
title: "ATheros 5006eg.NDiswrapper installed net5211.inf...still not recognizing wireles"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by nu-kid on 2008-04-04
I have read almost all the messages about similiar issues but none hit this. THe OS won't assign a device ID <eth1 or wlan0> to the wireless card. I even black listed the needed entries. Rebooted and nothing seems to work.
I know there are a lot of people smarter than I, so please can you help???
Thnx.


ghost@GHOST:~$ ndiswrapper -l
Installed ndis drivers:
net5211         driver present, hardware present 
ghost@GHOST:~$ lsmod
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
b44                    32396  0 
mii                     7424  1 b44
ndiswrapper           244608  0 
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               6400  0 
button                 10400  0 
sbs                    21520  0 
video                  21140  0 
dock                   12264  0 
ac                      7304  0 
battery                12424  0 
ath_pci               105392  0 
wlan                  225736  1 ath_pci
ath_hal               219888  1 ath_pci
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
uvcvideo               52228  0 
snd_rawmidi            29824  1 snd_seq_midi
compat_ioctl32         11136  1 uvcvideo
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  21004  0 
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
mmc_core               33416  1 sdhci
pcspkr                  4608  0 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
serio_raw               9092  0 
psmouse                45596  0 
k8temp                  7680  0 
i2c_piix4              11020  0 
i2c_core               30208  1 i2c_piix4
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  5 
ext3                  146576  3 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
atiixp                  7824  0 [permanent]
ide_core              141200  2 ide_cd,atiixp
sd_mod                 32512  5 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ata_generic             9988  0 
ehci_hcd               40076  0 
ahci                   27012  4 
libata                138928  2 ata_generic,ahci
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ohci_hcd               25092  0 
r8169                  36100  0 
usbcore               161584  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor
ghost@GHOST:~$ 

ghost@GHOST:~$ lspci
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
0e:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
ghost@GHOST:~$ 

ghost@GHOST:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:9c:17:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=10.10.3.13 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
ghost@GHOST:~$

---

### Post by kutjara on 2008-04-04
I couldn't get ndiswrapper to work with my Atheros card. One of the problems, I think, is that it misreports the card as a 5006, when it is in fact a 5007. Anyway, the solution from madwifi.net worked perfectly.

Here's the howto I used:

[http://ubuntuforums.org/showthread.php?t=669267](http://ubuntuforums.org/showthread.php?t=669267)

---

### Post by nu-kid on 2008-04-04
do I need to undo anything I had already done with ndiswrapper? WHen I went into the restricted drivers I just diabled the Atheros HArdware Access Layer(HAL).
Was that correct?
Anyway I followed the instructions on that link and still nothing.

---

### Post by kutjara on 2008-04-04
> **nu-kid said:**
> do I need to undo anything I had already done with ndiswrapper? WHen I went into the restricted drivers I just diabled the Atheros HArdware Access Layer(HAL).
Was that correct?
Anyway I followed the instructions on that link and still nothing.

I suspect you have to uninstall ndiswrapper (or at least disable its operation), since it probably conflicts with madwifi.

The only problem I had with the howto was that my card stopped being recognized every time I rebooted, so I had to add "ath-pci" to the /etc/modules file. That solved the problem for me.

Let me know if getting rid of ndiswrapper solves the problem for you.

---

