---
title: "no wireless in ubuntu studio"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by dmcaudio on 2007-08-26
Hello, I am in desperate need of expertise.  I was running dapper/edgy/feisty just fine with my D-Link wireless card.  When I made the move to ubuntu studio, it suddenly dropped off my network cards list.  I cannot seem to get it back.  HELP!!!


iwconfig
lo no wireless extensions.
eth0 no wireless extensions.

lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:01.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)

lsmod
Module Size Used by
nls_utf8 3072 1
ntfs 108276 1
binfmt_misc 13064 1
ipv6 273568 14
rfcomm 41752 0
l2cap 26112 5 rfcomm
bluetooth 57444 4 rfcomm,l2cap
ppdev 10116 0
i915 24448 3
drm 81812 4 i915
speedstep_lib 6148 0
cpufreq_userspace 5408 0
cpufreq_stats 7488 0
cpufreq_powersave 2688 0
cpufreq_ondemand 9356 0
freq_table 5792 2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative 8200 0
tc1100_wmi 8068 0
pcc_acpi 13184 0
dev_acpi 12164 0
sony_acpi 6284 0
video 16260 0
sbs 15528 0
i2c_ec 5888 1 sbs
i2c_core 23552 1 i2c_ec
dock 10424 0
button 8720 0
battery 10756 0
container 5248 0
ac 6020 0
asus_acpi 17308 0
backlight 6784 1 asus_acpi
fuse 46996 3
sbp2 24324 0
parport_pc 36644 0
lp 12548 0
parport 37576 3 ppdev,parport_pc,lp
snd_usb_audio 79872 0
snd_pcm_oss 45056 0
snd_hda_intel 22168 1
snd_hda_codec 205440 1 snd_hda_intel
xpad 9988 0
snd_seq_dummy 4740 0
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 80260 4 snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_hda_co dec
snd_usb_lib 17536 1 snd_usb_audio
snd_hwdep 10500 1 snd_usb_audio
snd_seq_oss 33408 0
snd_seq_midi 9600 0
snd_rawmidi 25856 2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
usblp 14976 0
iTCO_wdt 12072 0
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
shpchp 34324 0
pci_hotplug 33608 1 shpchp
pcspkr 4224 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd_timer 24196 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 54788 14 snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_hda_co dec,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,sn d_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 9440 1 snd
snd_page_alloc 10888 2 snd_hda_intel,snd_pcm
intel_agp 25116 1
agpgart 35788 3 drm,intel_agp
af_packet 24072 4
evdev 11008 5
tsdev 8768 0
ext3 134152 1
jbd 63528 1 ext3
mbcache 9604 1 ext3
sg 35996 0
sd_mod 23556 6
sr_mod 17188 0
cdrom 37664 1 sr_mod
usbhid 26720 0
hid 27392 1 usbhid
ata_piix 15620 0
ahci 22148 4
ata_generic 9092 0
libata 125848 3 ata_piix,ahci,ata_generic
scsi_mod 143116 5 sbp2,sg,sd_mod,sr_mod,libata
e100 36488 0
mii 6528 1 e100
ohci1394 36528 0
ieee1394 300120 2 sbp2,ohci1394
generic 5124 0 [permanent]
ehci_hcd 34316 0
uhci_hcd 25488 0
usbcore 135048 8 snd_usb_audio,xpad,snd_usb_lib,usblp,usbhid,ehci_h cd,uhci_hcd
thermal 14856 0
processor 31560 1 thermal
fan 5636 0
fbcon 43296 0
tileblit 3584 1 fbcon
font 9216 1 fbcon
bitblit 6912 1 fbcon
softcursor 3200 1 bitblit
vesafb 9220 0
capability 5896 0
commoncap 8192 1 capability

---

