---
title: "Linksys wpc11 not showing in ifconfig, please help!"
date: 2005-10-03
forum: Networking &amp; Wireless
---

### Post by ubonetu on 2005-10-03
Hello, friends,

ifconfig only shows the loopback (lo) when the Linksys card is inserted.  It shows my ethernet card fine at eth0.  I've tried restarting pcmcia with sudo /etc/init.d/pcmcia restart and added the card in /etc/pcmcia/wlan-ng.conf with no luck:confused: 

Any help greatly appreciated.

Thanks,
Ubonetu

---

### Post by az on 2005-10-03
Did the card work before?

Does the light come on?

What is the output of

lspci
lsmod

How old is the laptop?

---

### Post by ubonetu on 2005-10-03
azz,

Here's the output:

bones@ebony:~$ lsmod
Module                  Size  Used by
ipv6                  229376  6
speedstep_smi           5520  0
speedstep_lib           4228  1 speedstep_smi
proc_intf               4100  0
freq_table              4100  1 speedstep_smi
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0bones@ebony:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host
bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP
bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev
01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:0d.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394
Controller
0000:00:10.0 Multimedia audio controller: ESS Technology ES1978 Maestro
2E (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT
Pro AGP-133 (rev dc)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
RTL-8139/8139C/8139C+ (rev 10)

cpufreq_powersave       1920  0
apm                    19948  2
snd_es1968             27648  2
snd_ac97_codec         64608  1 snd_es1968
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_es1968,snd_pcm
gameport                4608  1 snd_es1968
snd_mpu401_uart         7168  1 snd_es1968
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9
snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
ohci1394               31876  0
yenta_socket           19584  1
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
irtty_sir               7936  0
sir_dev                18092  1 irtty_sir
irda                  168000  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
orinoco_cs              8968  0
pcmcia                 21380  5 orinoco_cs
pcmcia_core            53568  3 yenta_socket,orinoco_cs,pcmcia
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  774
processor              22708  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

The laptop is five years old.  The card works (last time I checked [a few months ago]) in Windows.

What do you see happening here?

Thanks for the help,

Ubonetu

---

### Post by ubonetu on 2005-10-04
Okay, so I'm up and running now.  Firstly, WPC11 may be supported but i don't think ver. 4 of the card is in the kernel modules by default.  Soooooo... I found that I needed to install ndiswrapper after downloading the driver from Linksys and getting the .ini file from it through wine.  This didn't work initially but did after I uncommented the card from /etc/pcmcia/wlan-ng.conf and HALTed the system (restart doesn't work so shutdown first).  I also added ndiswrapper, pcmcia-cs and ornioco-cs to /etc/modules (I don't know that pcmcia and especially ornioco are significant but if you want the card to load for clock sync it may need it).

Here are some urls that are helpful:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

(This may work for you but I had to use above)

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Thanks, azz and I hope this helps somebody:) :) :) 

ubonetu

---

