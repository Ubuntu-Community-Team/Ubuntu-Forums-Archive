---
title: "blacklist bcm43xx"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-10-16
Am trying to blacklist bcm43xx. When I type "sudo /etc/modprobe.d/blacklist" without the quotation marks I get command not found.

---

### Post by codejunkie on 2006-10-16
> **muggins said:**
> Am trying to blacklist bcm43xx. When I type "sudo /etc/modprobe.d/blacklist" without the quotation marks I get command not found.

try ```
sudo gedit /etc/modprobe.d/blacklist
``` or 
```
sudo nano /etc/modprobe.d/blacklist
```

---

### Post by muggins on 2006-10-16
> **codejunkie said:**
> try ```
sudo gedit /etc/modprobe.d/blacklist
``` or 
```
sudo nano /etc/modprobe.d/blacklist
```
Thanks for reply the gedit did the trick. Do you know how to blacklist bcm43xx driver?

---

### Post by codejunkie on 2006-10-16
> **muggins said:**
> Thanks for reply the gedit did the trick. Do you know how to blacklist bcm43xx driver?
I've never tried to blacklist that module but with some modules if adding it to the blacklist file and restarting doesn't work, you might have to blacklist other modules that link to them. what is the module for a network card sound card etc and could you post the output of ```
lsmod
```

---

### Post by muggins on 2006-10-16
> **codejunkie said:**
> I've never tried to blacklist that module but with some modules if adding it to the blacklist file and restarting doesn't work, you might have to blacklist other modules that link to them. what is the module for a network card sound card etc and could you post the output of ```
lsmod
```
It looks like I've successfully blacklisted that module now, thanks again. Just out of curiosity how would I have posted the output of lsmod without writing it all out my hand.

---

### Post by codejunkie on 2006-10-16
> **muggins said:**
> It looks like I've successfully blacklisted that module now, thanks again. Just out of curiosity how would I have posted the output of lsmod without writing it all out my hand.

open the terminal and enter the command ```
lsmod
``` and to select the text hold the left mouse button and move the mouse upward in the terminal will highlight all terminal output then click the right mouse button and choose copy then when you reply just click the right mouse button again and choose paste or hit Ctrl+v will paste the output then select the text again and click the **#** symbol in the reply box and it will put it in a code box like this
```
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
ext3                  135816  1
jbd                    58772  1 ext3
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
tsdev                   8000  0
nvidia               4547540  12
rtc                    13492  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbhid                 39904  1
psmouse                36100  0
soundcore              10208  1 snd
serio_raw               7300  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
amd64_agp              12356  1
agpgart                34888  2 nvidia,amd64_agp
i2c_nforce2             6912  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
evdev                   9856  1
xfs                   589656  1
exportfs                6272  1 xfs
ide_generic             1536  0
uhci_hcd               33808  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130820  6 usbhid,uhci_hcd,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
generic                 5124  0
amd74xx                15260  0 [permanent]
sata_nv                 9732  0
libata                 78992  1 sata_nv
scsi_mod              139496  1 libata
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vesafb                  8476  1
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```
so the text does not run together.

---

