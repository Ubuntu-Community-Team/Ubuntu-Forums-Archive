---
title: "Ubuntu 12.04.3 LTS - How to install WUSB100 ver. 2"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by psnowacki on 2013-11-09
Good Morning,

I tried to install my USB WiFi adapter on Ubuntu Server 12.04.3 and I failed.

I tried already few recommendations from this forum but none of this worked for me.

Can somebody assist me with this, I am beginner in such a matter and I even do not know if my WUSB is activated in system when I am inserting it to USB slot.

Please help me I cannot stand to have my system on cable connected because it is in my sleeping room.

I will be very gratefull for help.

---

### Post by varunendra on 2013-11-11
Welcome to the forums psnowacki !

While the USB adapter is plugged in, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lsusb
nm-tool
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by matt_symes on 2013-11-11
Thread moved to **wireless and networking**

---

### Post by psnowacki on 2013-11-12
As I said in my first post, I tried already with some instructions rom this forum and it can happen that now I have a little mess in the system.
But according Your sugestions, here are my outputs of commands mentioned by You...

From **lsusb**
```

Bus 001 Device 002: ID 1737:0078 Linksys WUSB100 v2 RangePlus Wireless Network Adapter [Ralink RT3070]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

From **nm-tool**
```



** (process:6179): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


NetworkManager Tool


State: unknown




** (process:6179): WARNING **: error: could not connect to NetworkManager

```

I am not using any GUI on server, I am trying to manage everything throught shell connected to server throught ssh.

From **lsmod**:
```

Module                  Size  Used by
arc4                   12509  2
rt2800usb              22525  0
rt2800lib              61785  1 rt2800usb
rt2x00usb              20099  1 rt2800usb
rt2x00lib              49144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              541819  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              453919  2 rt2x00lib,mac80211
radeon                892497  1
joydev                 17329  0
ttm                    72088  1 radeon
snd_atiixp             19415  0
snd_atiixp_modem       18702  0
drm_kms_helper         47749  1 radeon
snd_ac97_codec        110254  2 snd_atiixp,snd_atiixp_modem
drm                   233935  3 radeon,ttm,drm_kms_helper
pcmcia                 39854  0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                85934  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
yenta_socket           27427  0
i2c_algo_bit           13316  1 radeon
snd_timer              28931  1 snd_pcm
psmouse                82769  0
snd                    57014  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_timer
irda                  107987  0
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
microcode              18433  0
serio_raw              13031  0
shpchp                 32265  0
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         18398  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ppdev                  12849  0
i2c_piix4              13227  0
ati_agp                13242  1
crc_ccitt              12627  2 rt2800lib,irda
video                  19116  0
parport_pc             27612  1
mac_hid                13077  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
pata_acpi              12886  0
firewire_ohci          35914  0
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
8139too                27407  0
8139cp                 26687  0
pata_atiixp            13058  3

```

My USB device worked a while but I had some errors during connection which I cannot remember now. I think I done something wrong with drivers, maybe bad driver file used...

Please provide me with steps, how to clear driver and install new one for this device.

---

