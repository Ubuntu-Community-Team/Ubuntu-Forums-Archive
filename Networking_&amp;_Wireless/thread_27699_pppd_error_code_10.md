---
title: "pppd error code 10"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by attitude on 2005-04-17
I have a problem with dialup connection. I tried to coonect with gnome-ppp and wvdial, but in both cases I got the pppd error code 10, which says that there isn't any network protocol running on sistem. I'we loaded ppp-generic module, but I don't exacly know which other module to load. I pressume that I need some tcp/ip modules... I'm using Lucent LT winmodem with compiled drivers cause those form ubuntu kernel don't work. 
I fixed /etc/ppp/options (#auth). Everything worked pefectly fine on Warty.
This is my lsmod:
```
ipv6                  229504  6
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
nvidia               3923388  12
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
usblp                  12032  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usblp,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  2 nvidia,nvidia_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
ext3                  120968  1
jbd                    54168  1 ext3
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
af_packet              20744  0
ppp_async              10752  0
crc_ccitt               2176  1 ppp_async
ppp_deflate             6016  0
tsdev                   7488  0
zlib_deflate           20632  1 ppp_deflate
evdev                   9088  0
ppp_generic            27668  2 ppp_async,ppp_deflate
slhc                    7040  1 ppp_generic
ltserial                6440  0
ltmodem               557136  1 ltserial
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
reiserfs              225616  3
ide_generic             1664  0
ide_disk               18176  8
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  708
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
``` 

Thanks!

---

### Post by attitude on 2005-04-20
Anyone???

---

