---
title: "Speakers stopped working - do I need new drivers?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Enixine on 2008-12-05
I have speakers that used to work fine with my Ubuntu rig. Now, when I plug them in, there's a weird sort of screeching static that comes through and nothing else.

I've tested the speakers on other computers and they work fine, so I know the speakers are not at fault here.

Do I need to get new drivers for the speakers?


A little bit of background, which may or may not be related: I remember the same thing happened to my monitor with this Ubuntu computer. It was working fine, then all of a sudden it went to very basic display. I was told I needed new drivers, and I was given a complicated Terminal command to input. When I did that, the problem was solved. I reproduce the Terminal command below. Do you know if something similar will make my speakers work properly again?

> 1) Kill the GUI with:-
Code:

sudo /etc/init.d/gdm stop

After you kill the GUI, move to a tty by pressing Alt+Ctrl+F2, then enter the commands.

2) Reconfigure the X-Server with:-
Code:

sudo dpkg-reconfigure xserver-xorg

Select the options that best suit your PC.

3) Restart the GUI with:-
Code:

sudo /etc/init.d/gdm start

^ Is there something similar that I can type in as commands to get the speakers back online?

---

### Post by handydan918 on 2008-12-05
You could start with the output of the commands ```
lspci
```
and 
```
lsmod
```

The first will tell us what your sound card is, the second will show if the driver is loaded for it.

---

### Post by Enixine on 2008-12-05
Thanks for the speedy response. The first output is:

> 00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: Rockwell International Unknown device 4310
01:09.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
01:09.2 Input device controller: Rockwell International Unknown device 4312
01:0a.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller


The second output is:

> Module                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14080  0 
fat                    54300  1 vfat
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ipv6                  273892  8 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
apm                    22616  2 
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
lp                     12580  0 
snd_riptide            27412  2 
snd_ac97_codec        100644  1 snd_riptide
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_riptide,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           11520  1 snd_riptide
snd_hwdep              10244  1 snd_opl3_lib
snd_page_alloc         11400  2 snd_riptide,snd_pcm
snd_mpu401              9640  0 
snd_mpu401_uart         9600  2 snd_riptide,snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
parport_pc             37412  1 
snd                    54660  17 snd_riptide,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
analog                 13344  0 
gameport               16776  3 snd_riptide,analog
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
soundcore               8800  1 snd
psmouse                39952  0 
serio_raw               8068  0 
intel_agp              25620  1 
agpgart                35016  2 intel_agp
i2c_i810                5892  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_algo_bit            7428  1 i2c_i810
intel_rng               6656  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 i2c_i810,i2c_algo_bit
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
floppy                 60004  0 
natsemi                31328  0 
uhci_hcd               26640  0 
usbcore               138632  5 usb_storage,libusual,usbhid,uhci_hcd
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



---

### Post by Enixine on 2008-12-07
So, did I post the right info? If there's any other stuff I can provide to make the diagnosis easier, please let me know and I can do so.

---

