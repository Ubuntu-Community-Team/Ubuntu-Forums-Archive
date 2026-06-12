---
title: "Installed new soundcard and no sound..HELP!!!"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by 365baxter on 2009-04-14
I installed my new soundcard. Its SABRENT brand and i can't figure out how to get it to work...Help I need to record tonight..

---

### Post by 365baxter on 2009-04-14
new Sabrent soundcard installed and i cant figure out how to get it to work. No sound at all. please help. Is there an easy fix?

---

### Post by jbrown96 on 2009-04-14
> **365baxter said:**
> new Sabrent soundcard installed and i cant figure out how to get it to work. No sound at all. please help. Is there an easy fix?

Try changing all your sound devices to ALSA mixer in System--->Preferences--->sound. You may need to reboot and then check ```
alsamixer
``` in a terminal to make sure that nothing is muted and that the volume for all channels are turned up.

If that doesn't work, could you give some more information? Please post the output of the following commands. ```
lsmod
``` ```
lspci
```

---

### Post by overdrank on 2009-04-14
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by 365baxter on 2009-04-14
I already had ubuntu installed and running. My old sound card went out. Installed a new one. Its a sabrent ^ channel 5.1 sound 3D pci sound card. I think it shows up as C-media PCI iec958. Iselected it and no sound. I also selested asla (advanced linux sound architecture) and nothing. asla-mixer is not and option. hereis what you asked for. Hear you go. Hope this helps!
```

Module                  Size  Used by
ipv6                  267908  8 
xt_limit                3584  8 
xt_tcpudp               4096  13 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  0 
nf_conntrack_ftp       10144  0 
xt_state                3328  6 
binfmt_misc            12808  1 
radeon                124192  2 
drm                    82452  3 radeon
af_packet              23812  2 
rfcomm                 41744  6 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
battery                14212  0 
ac                      6916  0 
lp                     12324  0 
evdev                  13056  4 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
analog                 13600  0 
hci_usb                16540  2 
bluetooth              61028  7 rfcomm,l2cap,hci_usb
snd_cmipci             38528  2 
pcspkr                  4224  0 
gameport               16008  2 analog,snd_cmipci
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
snd_seq_midi            9376  0 
ac97_bus                3072  1 snd_ac97_codec
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                78596  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24836  3 snd_opl3_lib,snd_seq,snd_pcm
snd                    56996  25 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
soundcore               8800  1 snd
button                  9232  0 
i2c_sis96x              6148  0 
sis_agp                10116  1 
i2c_core               24832  1 i2c_sis96x
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,sis_agp
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
floppy                 59588  0 
pata_sis               15236  2 
8139cp                 24704  0 
ohci_hcd               26640  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
libata                159600  3 pata_acpi,ata_generic,pata_sis
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146412  4 hci_usb,usbhid,ohci_hcd
thermal                16796  0 
processor              36488  1 thermal
fan                     5636  0 
fuse                   50708  1 
vesafb                  8964  1 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit

```
baxter@baxter-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:08.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

---

### Post by mprince on 2009-04-15
Does your motherboard have onboard audio? If so, make sure you disable that in the BIOS.

---

### Post by markbuntu on 2009-04-15
Sorry if this may be a little late but, when adding a new soundcard you often need to reinstall alsa to get it recognized.


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

For more on using multiple sound cards you can go here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

