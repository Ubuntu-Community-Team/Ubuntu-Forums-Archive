---
title: "how do i install DGE-530T driver to ubuntuserver 7.10"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by wenhui100 on 2009-01-05
i am trying to install DGE-530T drivers to ubuntu 7.10 . how do i go about doing it ??? can anyone help me pls. thanks

lspci give me this

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
00:0c.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

so i could see that dge-530t was detected

lsmod give me this 

Module Size Used by
ipt_LOG 7552 0 
iptable_filter 3968 0 
ip_tables 13924 1 iptable_filter
x_tables 16260 2 ipt_LOG,ip_tables
af_packet 24840 0 
lp 12452 0 
loop 19076 0 
snd_via82xx 29464 0 
gameport 16776 1 snd_via82xx
snd_ac97_codec 100260 1 snd_via82xx
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0 
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 11528 2 snd_via82xx,snd_pcm
snd_mpu401_uart 9600 1 snd_via82xx
snd_seq_dummy 4740 0 
snd_seq_oss 33152 0 
snd_seq_midi 9600 0 
snd_rawmidi 25728 2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
pcspkr 4224 0 
snd_seq 53104 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via686a 17288 0 
i2c_isa 5248 1 via686a
snd 54532 11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro 10132 0 
soundcore 8800 1 snd
via_agp 11264 1 
i2c_core 26112 3 via686a,i2c_isa,i2c_viapro
shpchp 34580 0 
pci_hotplug 32576 1 shpchp
agpgart 35144 1 via_agp
parport_pc 37668 1 
parport 37448 2 lp,parport_pc
ipv6 278916 17 
evdev 11136 0 
sg 36380 0 
sd_mod 30336 1 
8139cp 25344 0 
ext3 133640 5 
jbd 60456 1 ext3
mbcache 9732 1 ext3
ide_cd 32416 0 
cdrom 37408 1 ide_cd
ide_disk 18432 6 
floppy 59876 0 
8139too 27776 0 
mii 6656 2 8139cp,8139too
sata_via 12676 1 
skge 43280 0 
uhci_hcd 26640 0 
via82cxxx 10244 0 [permanent]
ide_core 116932 3 ide_cd,ide_disk,via82cxxx
ata_generic 8580 0 
usbcore 138760 2 uhci_hcd
libata 125168 2 sata_via,ata_generic
scsi_mod 146828 3 sg,sd_mod,libata
dm_mirror 24320 0 
dm_snapshot 18980 0 
dm_mod 58816 7 dm_mirror,dm_snapshot
thermal 14344 0 
processor 32072 1 thermal
fan 5764 0 
fuse 47124 1 
apparmor 40600 0 
commoncap 8320 1 apparmo

mii-tool give me this

eth0: negotiated 100baseTx-FD, link ok

---

