---
title: "[HELP]Which module should I blacklist?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by kwan062 on 2008-04-03
Im trying to setup my usb wireless driver in ubuntu. But when I use ndisgtk to load driver or type 'ndiswrapper -m', the system alwarys returns this message "module configuration already contains alias directive". I checked the module list, but cannot find a driver which looks like a usb wireless driver...Can anyone take a look plz.Thanks a lot.

kwan062@ubuntu:~/DDD$ cat /proc/modules
ndiswrapper 233632 0 - Live 0xffffffff88326000
rfcomm 47656 2 - Live 0xffffffff88319000
l2cap 28672 11 rfcomm, Live 0xffffffff88311000
bluetooth 63876 4 rfcomm,l2cap, Live 0xffffffff88300000
ppdev 11272 0 - Live 0xffffffff882fc000
powernow_k8 16608 1 - Live 0xffffffff882f6000
cpufreq_ondemand 10896 1 - Live 0xffffffff882f2000
cpufreq_conservative 9608 0 - Live 0xffffffff882ee000
cpufreq_userspace 6048 0 - Live 0xffffffff882eb000
cpufreq_stats 8160 0 - Live 0xffffffff882e8000
freq_table 6464 3 powernow_k8,cpufreq_ondemand,cpufreq_stats, Live 0xffffffff882e5000
cpufreq_powersave 3072 0 - Live 0xffffffff88072000
button 10400 0 - Live 0xffffffff882e1000
sbs 21520 0 - Live 0xffffffff882da000
ac 7304 0 - Live 0xffffffff882d7000
container 6400 0 - Live 0xffffffff882d4000
dock 12264 0 - Live 0xffffffff882d0000
video 21140 0 - Live 0xffffffff882c9000
battery 12424 0 - Live 0xffffffff882c4000
sbp2 27144 0 - Live 0xffffffff882bc000
lp 15048 0 - Live 0xffffffff882b7000
loop 21764 0 - Live 0xffffffff882b0000
snd_intel8x0 40104 1 - Live 0xffffffff882a5000
snd_ac97_codec 122200 1 snd_intel8x0, Live 0xffffffff88286000
ac97_bus 4096 1 snd_ac97_codec, Live 0xffffffff88065000
snd_pcm_oss 50048 0 - Live 0xffffffff88278000
snd_mixer_oss 20096 1 snd_pcm_oss, Live 0xffffffff88272000
snd_pcm 94344 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xffffffff88259000
snd_seq_dummy 5380 0 - Live 0xffffffff88256000
snd_seq_oss 36864 0 - Live 0xffffffff8824c000
snd_seq_midi 11008 0 - Live 0xffffffff88248000
ide_cd 35488 0 - Live 0xffffffff8823e000
cdrom 41768 1 ide_cd, Live 0xffffffff88232000
snd_rawmidi 29824 1 snd_seq_midi, Live 0xffffffff88229000
snd_seq_midi_event 9984 2 snd_seq_oss,snd_seq_midi, Live 0xffffffff88225000
snd_seq 62496 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffff88214000
shpchp 38300 0 - Live 0xffffffff88209000
snd_timer 27272 2 snd_pcm,snd_seq, Live 0xffffffff88201000
snd_seq_device 10260 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffff881fd000
pcspkr 4608 0 - Live 0xffffffff881fa000
parport_pc 41896 1 - Live 0xffffffff881ee000
parport 44172 3 ppdev,lp,parport_pc, Live 0xffffffff881e2000
k8temp 7680 0 - Live 0xffffffff881df000
pci_hotplug 36612 1 shpchp, Live 0xffffffff881d5000
snd 69288 12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffff881c3000
i2c_nforce2 7808 0 - Live 0xffffffff880db000
soundcore 10272 1 snd, Live 0xffffffff881bf000
snd_page_alloc 12560 2 snd_intel8x0,snd_pcm, Live 0xffffffff881ba000
i2c_core 30208 1 i2c_nforce2, Live 0xffffffff881b1000
evdev 13056 3 - Live 0xffffffff881ac000
ext3 146576 1 - Live 0xffffffff88187000
jbd 69360 1 ext3, Live 0xffffffff88175000
mbcache 11272 1 ext3, Live 0xffffffff88171000
sg 41384 0 - Live 0xffffffff88165000
sd_mod 32512 5 - Live 0xffffffff8815c000
usbhid 32576 0 - Live 0xffffffff88153000
hid 33408 1 usbhid, Live 0xffffffff88149000
amd74xx 17328 0 [permanent], Live 0xffffffff88143000
sata_nv 24068 3 - Live 0xffffffff8813c000
ide_core 141200 2 ide_cd,amd74xx, Live 0xffffffff88118000
ohci1394 38984 0 - Live 0xffffffff8810b000
ieee1394 109528 2 sbp2,ohci1394, Live 0xffffffff880ef000
forcedeth 55048 0 - Live 0xffffffff880de000
floppy 69608 0 - Live 0xffffffff880c9000
ata_generic 9988 0 - Live 0xffffffff880c3000
libata 138928 2 sata_nv,ata_generic, Live 0xffffffff880a0000
scsi_mod 172856 4 sbp2,sg,sd_mod,libata, Live 0xffffffff88074000
ehci_hcd 40076 0 - Live 0xffffffff88067000
ohci_hcd 25092 0 - Live 0xffffffff8805d000
usbcore 161584 5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd, Live 0xffffffff88034000
thermal 16528 0 - Live 0xffffffff8802e000
processor 36232 2 powernow_k8,thermal, Live 0xffffffff88024000
fan 6920 0 - Live 0xffffffff88021000
fuse 52528 3 - Live 0xffffffff88013000
apparmor 47008 0 - Live 0xffffffff88006000
commoncap 9472 1 apparmor, Live 0xffffffff88002000

---

### Post by kevdog on 2008-04-03
That message you are receiving is not an error.  It just associates wlan0 with ndiswrapper.  Its ok.

---

