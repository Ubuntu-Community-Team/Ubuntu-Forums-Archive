---
title: "sound on hp 6735s not working"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-04-20
ok here is my documents

i tried "aplay -l"

[B]card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]


then this command and uner audio
"lspci -v | less"

[B]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Hewlett-Packard Company Device 3613
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel[/B]

i tried to play with volume control all day doesnt work still!

---

### Post by northern lights on 2009-04-20
Could you please also post the outputs of ```
sudo lshw -C multimedia
```and```
cat /proc/asound/cards
```Thank you.

P.S. Please enclose the outputs in code tags (hash/pound/# button).

---

### Post by alexeyhurricane on 2009-04-20
*-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel


cat /proc/asound/cards

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd4400000 irq 16

---

### Post by alexeyhurricane on 2009-04-20
```
*-multimedia
description: Audio device
product: SBx00 Azalia (Intel HDA)
vendor: ATI Technologies Inc
physical id: 14.2
bus info: pci@0000:00:14.2
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=HDA Intel latency=64 module=snd_hda_intel
```

```
0 [SB ]: HDA-Intel - HDA ATI SB
HDA ATI SB at 0xd4400000 irq 16 
```

---

### Post by alexeyhurricane on 2009-04-20
video works fine , but there are no sound ! and i switched to ubuntu because i think there was audio crashes in vista blue screen(0x00000124) because of audio and i got lots of trojans and worms!

---

### Post by alexeyhurricane on 2009-04-20
if i dont get my sound working ill send my laptop to manufactureres soon! and get windows 7 propably looks nicer!

---

### Post by alexeyhurricane on 2009-04-20
i fixed it by  ```
sudo gedit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot 
```

but still there is very bad sound quality how to improve it??????????? any ideas

---

### Post by alexeyhurricane on 2009-04-20
yeh i think i fixed it thank you for your help ubunters , lazy people!

---

### Post by northern lights on 2009-04-23
> **alexeyhurricane said:**
> yeh i think i fixed it thank you for your help ubunters , lazy people!

Admittedly, this thread sort of got away. From both me and everyone else.

Still, you can't help but notice how active these forums are - please don't take this experience of yours as an example of how support requests are handled generally.

Sorry for not getting back to you, Johannes

---

### Post by breedtan on 2009-05-11
Just had same problem, tried the normal Sound Troubleshooting page, but to no avail.

Adding the below to the ALSA config file seems to have worked a treat. Sound quality decent also.




options snd-hda-intel model=laptop

---

