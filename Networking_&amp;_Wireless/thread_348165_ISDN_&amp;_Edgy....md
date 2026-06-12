---
title: "ISDN &amp; Edgy..."
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by chr1s777 on 2007-01-28
Hi there,

I just made the step from Dapper to Edgy and got a really bad Problem:
I can't connect to the internet!

I'm using ISDN with an AVM FRITZ!Card PCI.

In Dapper, I used the following HOWTO to configure my Card
[http://wiki.ubuntuusers.de/AVM_FRITZ%21Card]("http://wiki.ubuntuusers.de/AVM_FRITZ%21Card")

Because I didn't find a special HOWTO for ISDN under Edgy so far, I tried to use the same again. So I installed the packages as proposed and installed "isdnactivecards" manually, because it wasn't on my Install-DVD.

After trying to check the configuration with "capiinfo", I got the following error:

```
chris@ubuntu:~$ capiinfo
capi not installed - No such device or address (6)
```

Because I didn' find a solution for this, I tried to ignore it and just continued with the Howto, but finally endet up in a new error, when I tried to "pon provider"

```
chris@ubuntu:~$ pon provider
Plugin userpass.so loaded.
userpass: $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn:  1.13
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)]
```

Well, under Dapper it wasn't a problem at all to get my ISDN working with this HOWTO, 
but now I just don't know what do do.

Maybe one of you can help me out.

Here my "lsmod"

```
Module                  Size  Used by
nls_utf8                2304  1
nls_cp437               6016  1
vfat                   13440  1
fat                    54556  1 vfat
ipv6                  257632  8
binfmt_misc            11784  1
rfcomm                 38936  0
l2cap                  23300  5 rfcomm
cpufreq_userspace       4372  0
cpufreq_stats           5892  0
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0
cpufreq_ondemand        6944  0
cpufreq_conservative     7200  0
video                  16644  0
tc1100_wmi              7428  0
sbs                    15776  0
sony_acpi               5516  0
pcc_acpi               13184  0
i2c_ec                  5376  1 sbs
hotkey                 10660  0
dev_acpi               11140  0
button                  7056  0
battery                10756  0
container               4736  0
ac                      5892  0
asus_acpi              16792  0
reiserfs              258688  1
sg                     35356  0
sd_mod                 21648  2
capi                   17856  0
af_packet              21768  2
capifs                  6280  2 capi
sbp2                   23304  0
lp                     11972  0
usb_storage            73408  1
cx88_blackbird         21020  0
libusual               15632  1 usb_storage
hci_usb                15892  2
cx88_dvb               13700  0
cx8802                 12036  2 cx88_blackbird,cx88_dvb
cx88_vp3054_i2c         4480  1 cx88_dvb
mt352                   7044  1 cx88_dvb
or51132                10500  1 cx88_dvb
video_buf_dvb           6660  1 cx88_dvb
dvb_core               80424  1 video_buf_dvb
bluetooth              48996  7 rfcomm,l2cap,hci_usb
kernelcapi             48032  1 capi
usblp                  14336  0
nxt200x                14468  1 cx88_dvb
zl10353                 5636  1 cx88_dvb
cx8800                 33932  1 cx88_blackbird
cx88xx                 62884  4 cx88_blackbird,cx88_dvb,cx8802,cx8800
snd_intel8x0           33436  1
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
mISDN_l2               42240  0
mISDN_l1               12168  0
snd_mpu401              8616  0
snd_mpu401_uart         8704  1 snd_mpu401
cx24123                14216  1 cx88_dvb
lgdt330x                8604  1 cx88_dvb
cx22702                 6916  1 cx88_dvb
dvb_pll                12804  4 cx88_dvb,or51132,nxt200x,cx22702
tsdev                   8256  0
ir_common              27652  1 cx88xx
i2c_algo_bit            9480  2 cx88_vp3054_i2c,cx88xx
serio_raw               7300  0
snd_pcm_oss            46080  0
snd_mixer_oss          18560  1 snd_pcm_oss
avmfritz               24204  0
mISDN_isac             16128  1 avmfritz
i2c_nforce2             7296  0
snd_rawmidi            25600  1 snd_mpu401_uart
snd_seq_device          8972  1 snd_rawmidi
floppy                 60676  0
video_buf              26372  6 cx88_blackbird,cx88_dvb,cx8802,video_buf_dvb,cx8800,cx88xx
tveeprom               15248  1 cx88xx
v4l2_common            16384  2 cx88_blackbird,cx8800
compat_ioctl32          1536  1 cx8800
v4l1_compat            14212  1 cx8800
btcx_risc               5384  3 cx8802,cx8800,cx88xx
videodev                9728  3 cx88_blackbird,cx8800,cx88xx
evdev                  10496  2
analog                 11680  0
gameport               15368  1 analog
mISDN_core             73056  4 mISDN_l2,mISDN_l1,avmfritz,mISDN_isac
i2c_core               22288  13 i2c_ec,cx88_dvb,mt352,or51132,nxt200x,zl10353,cx88xx,cx24123,lgdt330x,cx22702,i2c_algo_bit,i2c_nforce2,tveeprom
parport_pc             36132  1
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
pcspkr                  3072  0
parport                37320  2 lp,parport_pc
psmouse                40072  0
rtc                    12596  0
forcedeth              30220  0
nvidia_agp              8732  1
agpgart                33456  1 nvidia_agp
shpchp                 40856  0
pci_hotplug            31284  1 shpchp
snd                    55428  12 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
ext3                  138632  1
jbd                    55700  1 ext3
ohci1394               35248  0
ieee1394              302904  2 sbp2,ohci1394
ehci_hcd               32520  0
ohci_hcd               20740  0
usbcore               130304  7 usb_storage,libusual,hci_usb,usblp,ehci_hcd,ohci_hcd
ide_generic             1536  0
ide_cd                 32416  0
cdrom                  37792  1 ide_cd
ide_disk               17664  4
generic                 4868  0
amd74xx                14364  0 [permanent]
sata_nv                10116  0
libata                 73228  1 sata_nv
scsi_mod              141320  5 sg,sd_mod,sbp2,usb_storage,libata
thermal                14600  0
processor              26028  1 thermal
fan                     5124  0
fbcon                  40480  0
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0
capability              5000  0
commoncap               7808  1 capability 
```

---

