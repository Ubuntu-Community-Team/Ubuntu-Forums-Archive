---
title: "Wireless Adapter not showing up as a interface"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by blackax on 2008-03-13
I have a ZyDAS usb wifi card and i have the "zd1211rw" module loaded  but it doesnt show up as a interface. I'm running on a version of ubuntu 7.10. If i could get any help that would be great.

lsusb

Bus 005 Device 003: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 002 Device 001: ID 0000:0000

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by blackax on 2008-03-14
bump :( any help guys???

---

### Post by kevdog on 2008-03-14
Probably because you dont have a driver (kernel module) loaded for the device.  You might have to google around, but you need to tell us the internal chipset in the device so we can be of assistance.

---

### Post by blackax on 2008-03-14
My card has a ZyDAS 1201 based chipset and it is supose to use the zd1211rw driver and it is already loaded.

```

Module                  Size  Used by
sg                     36764  0
autofs4                23044  0
acpi_cpufreq           10568  0
cpufreq_powersave       2688  0
cpufreq_conservative     8072  0
cpufreq_stats           7232  0
cpufreq_ondemand        9612  1
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0
dock                   10656  0
video                  18060  0
ac                      6148  0
battery                11012  0
sbs                    19592  0
container               5504  0
button                  8976  0
ipv6                  273892  14
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  2 parport_pc,lp
fuse                   47124  0
zd1211rw               53508  0
joydev                 11328  0
snd_via82xx            29336  0
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
ieee80211softmac       31360  1 zd1211rw
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
pl2303                 22148  0
usbserial              34920  1 pl2303
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
ieee80211              35656  2 zd1211rw,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usbhid                 29536  0
hid                    28928  1 usbhid
usbtouchscreen         10628  0
xpad                    9988  0
hci_usb                18332  0
bluetooth              57060  1 hci_usb
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0
psmouse                39952  0
serio_raw               8068  0
snd                    54660  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10004  0
soundcore               8800  1 snd
i2c_core               26112  1 i2c_viapro
af_packet              24840  2
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
via_agp                11264  1
agpgart                35016  1 via_agp
evdev                  11136  4
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0
cdrom                  37536  1 ide_cd
ide_disk               18560  4
ata_generic             8452  0
libata                125168  1 ata_generic
scsi_mod              147084  3 sg,sbp2,libata
via_rhine              25992  0
mii                     6528  1 via_rhine
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  10 zd1211rw,pl2303,usbserial,usbhid,usbtouchscreen,xpad,hci_usb,ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0
capability              5896  0
commoncap               8320  1 capability


```

---

### Post by kevdog on 2008-03-14
Im going to have to defer as Im definitely not an expert with this chipset.  This is the only thing I could come up with:
[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211?highlight=%28zydas%29#head-3cca5be9a7b403810805de04195bd19861e9611e](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211?highlight=%28zydas%29#head-3cca5be9a7b403810805de04195bd19861e9611e)

---

### Post by blackax on 2008-03-14
Thank you I'm gonna compile the driver from source and see if that help at all.

---

