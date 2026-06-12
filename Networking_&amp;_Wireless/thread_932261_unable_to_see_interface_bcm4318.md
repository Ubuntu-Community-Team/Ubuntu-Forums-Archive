---
title: "unable to see interface bcm4318"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by mau84 on 2008-09-28
Hi!
I have a simple problem:I installed a wireless network card on a old pc, pentium III with motherboard olidata oli-bx with the last bios.
Wireless card is asus with broadcom bcm4318 chip. I correctly installed restricted driver and firmware but if I check ifconfig or iwconfig I can't see it.

lspci :

```
00:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

lsmod:
```
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
sbs                    15112  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
sbshc                   7680  1 sbs
battery                14212  0 
ac                      6916  0 
lp                     12324  0 
loop                   18948  0 
snd_opl3sa2            20076  2 
snd_opl3_lib           12928  1 snd_opl3sa2
snd_hwdep              10500  1 snd_opl3_lib
snd_cs4231_lib         26624  1 snd_opl3sa2
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         11400  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9728  1 snd_opl3sa2
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  18 snd_opl3sa2,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
analog                 13600  0 
ns558                   5632  0 
soundcore               8800  1 snd
gameport               16008  3 analog,ns558
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  3 
ipv6                  267780  8 
serio_raw               7940  0 
b43                   144420  0 
rfkill                  8592  1 b43
psmouse                40336  0 
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
button                  9232  0 
pcspkr                  4224  0 
s3fb                   21760  1 
svgalib                10368  1 s3fb
intel_agp              25492  1 
i2c_piix4               9612  0 
vgastate               10496  1 s3fb
i2c_core               24832  1 i2c_piix4
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  1 intel_agp
xt_tcpudp               4096  14 
nf_conntrack_ipv4      19080  10 
xt_state                3328  10 
nf_conntrack           66752  2 nf_conntrack_ipv4,xt_state
ipt_LOG                 7296  7 
iptable_filter          3840  1 
ip_tables              14820  1 iptable_filter
x_tables               16132  4 xt_tcpudp,xt_state,ipt_LOG,ip_tables
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
ata_piix               19588  3 
ata_generic             8324  0 
floppy                 59588  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
ssb                    34308  1 b43
libata                159344  3 ata_piix,ata_generic,pata_acpi
8139too                27520  0 
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
usbcore               146028  3 ehci_hcd,uhci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```


So...what can I do?

---

### Post by mau84 on 2008-09-28
I found dmesg error:
```
[   75.502889] b43-phy0: Broadcom 4318 WLAN found
[   75.546500] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 15, Type 15, Revision 255)
[   75.546565] b43: probe of ssb0:0 failed with error -95
```

So...I try to use bcm43xx instead of b43 but nothing...

please help.

---

### Post by superprash2003 on 2008-09-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by mau84 on 2008-09-28
thanks but I don't want to use ndiswrapper! The question is: this bc43 module works or I have a proplem on my hardware?

---

