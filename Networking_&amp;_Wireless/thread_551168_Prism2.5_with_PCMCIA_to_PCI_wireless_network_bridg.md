---
title: "Prism2.5 with PCMCIA to PCI wireless network bridge"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by PhlakDabbler on 2007-09-14
I have a linksys wpc11 ver.2.5 wireless card, it is supposedly a prism2.5 chipset, which is supposed to have built in support in Ubuntu. I cannot get it to work at all. here are some of my readouts.

me@mycomputer:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 USB Controller: NEC Corporation USB (rev 43)
00:0e.1 USB Controller: NEC Corporation USB (rev 43)
00:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 Network controller: Global Sun Technology Inc PCMCIA-to-PCI Wireless Network Bridge (rev 02)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

me@mycomputer:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14208  0 
fat                    53916  1 vfat
sd_mod                 23428  0 
usb_storage            72256  0 
libusual               17936  1 usb_storage
sg                     36252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
apm                    22752  1 
ppdev                  10116  0 
ipv6                  268960  14 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
lp                     12452  0 
fuse                   46612  1 
af_packet              23816  4 
snd_cs4236             19496  1 
snd_cs4236_lib         17280  1 snd_cs4236
snd_opl3_lib           11520  1 snd_cs4236
snd_hwdep               9988  1 snd_opl3_lib
snd_cs4231_lib         26112  2 snd_cs4236,snd_cs4236_lib
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         10888  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9472  1 snd_cs4236
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          9100  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_cs4236,snd_cs4236_lib,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
ns558                   5760  0 
gameport               16520  2 ns558
orinoco_plx             9472  0 
orinoco                43028  1 orinoco_plx
hermes                  8448  2 orinoco_plx,orinoco
hostap_plx             57240  0 
hostap                113924  1 hostap_plx
ieee80211_crypt         7040  1 hostap
pcspkr                  4224  0 
prism2_plx             71296  0 
p80211                 31884  1 prism2_plx
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0 
psmouse                38920  0 
intel_agp              26140  1 
agpgart                35400  1 intel_agp
i2c_piix4               9740  0 
i2c_core               22656  1 i2c_piix4
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  1 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  4 sd_mod,usb_storage,sg,libata
generic                 5124  0 [permanent]
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
ehci_hcd               34188  0 
ohci_hcd               22532  0 
uhci_hcd               25360  0 
usbcore               134280  6 usb_storage,libusual,ehci_hcd,ohci_hcd,uhci_hcd
piix                   10756  0 [permanent]
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

me@mycomputer:~$ sudo lshw -class network
Password:
  *-network:0 DISABLED    
       description: Ethernet interface
       product: PCMCIA-to-PCI Wireless Network Bridge
       vendor: Global Sun Technology Inc
       physical id: f
       bus info: pci@00:0f.0
       logical name: wlan0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_plx driverversion=0.2.5 latency=0 link=no multicast=yes
       resources: ioport:dc00-dc7f iomemory:ff002400-ff0027ff ioport:d8c0-d8ff irq:10
  *-network:1
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth0
       version: 24
       serial: 00:c0:4f:53:d7:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.138 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d87f iomemory:ff002000-ff00207f irq:10


I am not entirely n00b, but I cannot find anything to help me with the wireless PCMCIA to PCI bridge thing. Please help me.......


2 days after first posting.

Since no one here was able to help, I figured it out on my own.
I ran a dmesg, and saw that there were some of the drivers that are supposed to be blacklisted to run hostap loading on startup. I blacklisted these, and now my prism2.5 will see the wireless network. It turns out that the PCMCIA to PCI bridge was working fine, but because of driver conflicts , I was not able to see the wireless card.  I also had to upgrade the kernel, because there was some glitch with the driver in the one I was running, so then after all that, I rebooted, and it works. Thanks for all the help, y'all.

---

