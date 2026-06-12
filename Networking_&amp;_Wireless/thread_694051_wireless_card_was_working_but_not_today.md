---
title: "wireless card was working but not today"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by buppy on 2008-02-11
My wireless card was working not sure what happened here is some info if anyone can help...i would hate to have to reinstall ubuntu ! it took a while to get it just the way i want it.
lspci:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
05:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)


lsmod:
Module Size Used by
af_packet 24840 2
ipv6 273892 8
nls_cp437 6784 1
isofs 36412 1
udf 87204 0
binfmt_misc 12936 1
savage 34176 2
drm 83348 3 savage
rfcomm 42136 2
l2cap 26240 11 rfcomm
bluetooth 57060 4 rfcomm,l2cap
ppdev 10244 0
snd_atiixp_modem 17160 0
snd_via82xx_modem 16264 0
snd_intel8x0m 18572 5
speedstep_lib 6404 0
cpufreq_ondemand 9612 0
cpufreq_conservative 8072 0
cpufreq_powersave 2688 0
cpufreq_stats 7232 0
freq_table 5792 2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace 5280 0
dock 10656 0
button 8976 0
battery 11012 0
ac 6148 0
sbs 19592 0
container 5504 0
video 18060 0
toshiba_acpi 11952 0
vboxdrv 61104 0
lp 12580 0
bcm43xx 127336 0
ieee80211softmac 31360 1 bcm43xx
ieee80211 35656 2 bcm43xx,ieee80211softmac
ieee80211_crypt 7040 1 ieee80211
joydev 11328 0
pcmcia 41388 0
snd_intel8x0 34972 1
snd_ac97_codec 100644 4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44672 0
snd_mixer_oss 17664 1 snd_pcm_oss
irda 202300 0
snd_pcm 80388 8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33152 0
crc_ccitt 3072 1 irda
parport_pc 37412 0
parport 37448 3 ppdev,lp,parport_pc
snd_seq_midi 9600 0
snd_rawmidi 25728 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
yenta_socket 27532 3
rsrc_nonstatic 14080 1 yenta_socket
pcspkr 4224 0
psmouse 39952 0
serio_raw 8068 0
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
pcmcia_core 40980 3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 54660 23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_o ss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_tim er,snd_seq_device
soundcore 8800 1 snd
iTCO_wdt 11940 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd_page_alloc 11400 5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_pcm
intel_agp 25620 1
agpgart 35016 2 drm,intel_agp
shpchp 34580 0
pci_hotplug 32704 1 shpchp
evdev 11136 4
ext3 133896 1
jbd 60456 1 ext3
mbcache 9732 1 ext3
sg 36764 0
sr_mod 17828 1
cdrom 37536 1 sr_mod
sd_mod 30336 3
floppy 60004 0
ata_piix 17540 3
ata_generic 8452 0
libata 125168 2 ata_piix,ata_generic
scsi_mod 147084 4 sg,sr_mod,sd_mod,libata
e100 37644 0
mii 6528 1 e100
uhci_hcd 26640 0
usbcore 138632 2 uhci_hcd
thermal 14344 0
processor 32072 1 thermal
fan 5764 0
fuse 47124 1
apparmor 40728 0
commoncap 8320 1 apparmor


the card is a microsoft mn720 not to sure of the revision if any. i can find out if absolutely necessary. laptop is a toshiba satellite 2400.
any help will be greatly appreciated and returned to the community when i become a linux pro LOL.
__________________
Thanks Edit/Delete Message

---

### Post by mrsteveman1 on 2008-02-11
Run the following commands and post the results:

```
sudo iwconfig eth0/ath0/wifi0 (depending on which it is, might be eth1)

sudo ifconfig -a

sudo dmesg | grep bcm43xx
```

---

