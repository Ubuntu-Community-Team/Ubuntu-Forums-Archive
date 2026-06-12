---
title: "Orinoco USB Difficulties w/Xubuntu on iBook G3"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by mesartwell on 2007-10-06
Ok guys I've been trying to figure this out for hours so please help anyway that you can:

I have a Orinoco Wireless USB card that I am trying to get working on my fresh install of PPC Xubuntu on my iBook g3( dual USB version). Apparently, the card is not hotpluggable since it is not working by just plugging it in so I need to know how to load a driver or "module" or whatever its called for the card to work. Here's the output from a lsusb and a lsmod. BTW it's kernel version: 2.6.17-12-powerpc

lsmod:
```
Module                  Size  Used by
pcmcia                 45424  0 
pcmcia_core            49624  1 pcmcia
orinoco                45556  0 
hermes                  8736  1 orinoco
r128                   46724  2 
drm                    83384  3 r128
ppdev                  11268  0 
lp                     13612  0 
parport                44624  2 ppdev,lp
cpufreq_userspace       5588  1 
cpufreq_stats           6532  0 
cpufreq_powersave       2176  0 
cpufreq_ondemand        8128  0 
cpufreq_conservative     8448  0 
ieee80211              35464  0 
ieee80211_crypt         6912  1 ieee80211
ipv6                  302796  8 
sbp2                   26440  0 
scsi_mod              175824  1 sbp2
apm_emu                 8140  1 
af_packet              25192  2 
snd_powermac           49916  2 
snd_aoa_i2sbus         24516  0 
snd_pcm_oss            54048  1 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
tsdev                   9120  0 
snd                    69940  8 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  2 snd
evdev                  12736  7 
sungem                 35492  0 
sungem_phy             10720  1 sungem
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
uninorth_agp           11144  1 
agpgart                38204  2 drm,uninorth_agp
pmac_zilog             21060  0 
serial_core            24896  1 pmac_zilog
ext3                  161544  1 
jbd                    69556  1 ext3
ohci1394               41840  0 
ieee1394              431440  2 sbp2,ohci1394
ohci_hcd               24228  0 
usbcore               151676  2 ohci_hcd
ide_cd                 36420  0 
cdrom                  47932  1 ide_cd
ide_disk               19296  3 
capability              5320  0 
commoncap               8064  1 capability

```

lsusb:
```
Bus 001 Device 003: ID 047e:0300 Agere Systems, Inc. (Lucent) 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

In lsusb at least it lists the device properly, i thought this might be a good sign.

---

### Post by Lambert on 2007-10-07
> **mesartwell said:**
> Ok guys I've been trying to figure this out for hours so please help anyway that you can:

I have a Orinoco Wireless USB card that I am trying to get working on my fresh install of PPC Xubuntu on my iBook g3( dual USB version). Apparently, the card is not hotpluggable since it is not working by just plugging it in so I need to know how to load a driver or "module" or whatever its called for the card to work. Here's the output from a lsusb and a lsmod. BTW it's kernel version: 2.6.17-12-powerpc

lsmod:
```
Module                  Size  Used by
pcmcia                 45424  0 
pcmcia_core            49624  1 pcmcia
orinoco                45556  0 
hermes                  8736  1 orinoco
r128                   46724  2 
drm                    83384  3 r128
ppdev                  11268  0 
lp                     13612  0 
parport                44624  2 ppdev,lp
cpufreq_userspace       5588  1 
cpufreq_stats           6532  0 
cpufreq_powersave       2176  0 
cpufreq_ondemand        8128  0 
cpufreq_conservative     8448  0 
ieee80211              35464  0 
ieee80211_crypt         6912  1 ieee80211
ipv6                  302796  8 
sbp2                   26440  0 
scsi_mod              175824  1 sbp2
apm_emu                 8140  1 
af_packet              25192  2 
snd_powermac           49916  2 
snd_aoa_i2sbus         24516  0 
snd_pcm_oss            54048  1 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
tsdev                   9120  0 
snd                    69940  8 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  2 snd
evdev                  12736  7 
sungem                 35492  0 
sungem_phy             10720  1 sungem
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
uninorth_agp           11144  1 
agpgart                38204  2 drm,uninorth_agp
pmac_zilog             21060  0 
serial_core            24896  1 pmac_zilog
ext3                  161544  1 
jbd                    69556  1 ext3
ohci1394               41840  0 
ieee1394              431440  2 sbp2,ohci1394
ohci_hcd               24228  0 
usbcore               151676  2 ohci_hcd
ide_cd                 36420  0 
cdrom                  47932  1 ide_cd
ide_disk               19296  3 
capability              5320  0 
commoncap               8064  1 capability

```

lsusb:
```
Bus 001 Device 003: ID 047e:0300 Agere Systems, Inc. (Lucent) 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

In lsusb at least it lists the device properly, i thought this might be a good sign.

type this in a terminal and post output.

```

sudo modinfo orinoco_usb

```

orinoco is loaded per your lsmod info but that driver doesn't doesn't support usb devices. Depending if the _usb version is installed will depend on next steps. If you want to search and figure out the next steps if it is installed, you basically need to blacklist the orinoco driver and load the _usb version and try your device.

---

