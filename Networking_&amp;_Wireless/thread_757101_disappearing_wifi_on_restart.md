---
title: "disappearing wifi on restart"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Spectre Nexus on 2008-04-16
Greetings, I am a newb when it comes to Ubuntu and Linux in general.
 I have perused the forums and I haven't seen anything that helped.

I have a Presario V5000 with a Broadcom 43xx wi-fi card
After reading numerous posts about how horrible this card is I took
it in stride and after some trial and error I have the wi-fi working.

However the error I am getting is every time I reboot the system wi-fi is
gone and in the restricted drivers manager is still says it enabled, However
the only way to get wi-fi working again is to disable it and reboot
then go through the whole re-enable process then it works fine until the next reboot.
Due to restrictions I am forced to shut down and restart the system numerous times a day, therefor leaving it on isn't an option.

My question is Is there something I am doing wrong or something else I need
to do to make this a easier process, so I can actually use this laptop like a laptop
and not a desktop.

Ubuntu 7.10 - Gutsy Gibbon
fully updated

Thank You in advance

---

### Post by Spectre Nexus on 2008-04-17
wow No help on this one.. someone has to have a idea

Please.....

---

### Post by Whiffle on 2008-04-17
Looks like your post got buried. 

Could you boot up your laptop, and then post the output of "lsmod"? Sounds to me like the module for your wireless isn't loading.  We can fix that by adding its name to /etc/modprobe.conf if i remember correctly.

---

### Post by Spectre Nexus on 2008-04-17
here it is with wifi working, I will post a follow-up lsmod after I reboot and re-enable the card

Module                  Size  Used by
sg                     36764  0 
ipv6                  273892  8 
af_packet              24840  4 
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
battery                11012  0 
video                  18060  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
sbs                    19592  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
pcspkr                  4224  0 
snd_atiixp             21132  1 
snd_ac97_codec        100644  2 snd_atiixp_modem,snd_atiixp
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
psmouse                39952  0 
snd_pcm                80388  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
k8temp                  6656  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54660  13 snd_atiixp_modem,snd_seq_oss,snd_rawmidi,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ati_agp                10124  0 
agpgart                35016  2 drm,ati_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sg,libata
8139too                27776  0 
mii                     6528  2 8139cp,8139too
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
spectre@spectre-laptop:~$

---

### Post by Spectre Nexus on 2008-04-17
Here is lsmod after a restart with wifi not working

Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
battery                11012  0 
video                  18060  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
sbs                    19592  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_atiixp_modem       17160  0 
snd_seq_dummy           4740  0 
psmouse                39952  0 
snd_seq_oss            33152  0 
serio_raw               8068  0 
snd_seq_midi            9600  0 
pcspkr                  4224  0 
snd_atiixp             21132  1 
snd_ac97_codec        100644  2 snd_atiixp_modem,snd_atiixp
snd_rawmidi            25728  1 snd_seq_midi
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_pcm                80388  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                  6656  0 
snd                    54660  13 snd_atiixp_modem,snd_seq_oss,snd_atiixp,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ati_agp                10124  0 
agpgart                35016  2 drm,ati_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
8139cp                 25088  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by Spectre Nexus on 2008-04-19
did I get lost in the post storm again?

Anyone help me on this one?  It is really starting to get annoying,
and very much an inconvenience.

---

### Post by Whiffle on 2008-04-19
Yes, next time you restart try doing 

sudo modprobe bcm43xx

If that fixes it, add bcm43xx to /etc/modules , which will cause it to be loaded on boot.

---

### Post by Spectre Nexus on 2008-04-19
> **Whiffle said:**
> Yes, next time you restart try doing 

sudo modprobe bcm43xx

If that fixes it, add bcm43xx to /etc/modules , which will cause it to be loaded on boot.

Okay my next question would be, how do I add it to the modules to be booted?

and thanx for the help

---

### Post by Spectre Nexus on 2008-04-19
yup that fixed it. 
So now how do I add it to my start up modules?

I will surf around here and see if I can find out thou

---

### Post by KB3MKD on 2008-04-19
sudo gedit /etc/modules

---

### Post by Alan_M on 2008-04-19
> If that fixes it, add bcm43xx to /etc/modules , which will cause it to be loaded on boot.

^ theres your answer buddy :)

in a terminal window, type this:

```
sudo gedit /etc/modules
```

enter your password

follow the same format the other modules use to put "bcm43xx" in this file at the bottom.

Hope this helps! :)

---

### Post by Spectre Nexus on 2008-04-19
Thanx Much, seems to be working great now!

I appreciate you folks taking time out to help me.

And special than gos out to Whiffle for diggin my post out
and providing me with a --> in the right direction

---

