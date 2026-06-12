---
title: "Lenovo G555-1 Problems with Ubuntu 9.10"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by grtech on 2010-05-26
Always after a few hours spending on Lenovo the screen of laptop become white with vertical black lines. Mostly when I am trying to maximize the window of some applications or of the explorer.

The line in and out of the sound card doesn't works properly. The speakers and the headphones play together and the Mic doesn't work at all.

Some times when I am trying to shutdown the laptop the screen become black and the laptop still works and it doesn't off.

I did try to install the ubuntu 10.04 but I've seen an unexplained waste of memory (850 MB of Ram) and with the same setup the ubuntu 9.10 spends only 250 MB Ram.

If anyone have the same or other problems with his Lenovo G555-1 running Ubuntu 9.10 please to respond on this thread and of course any help it will be appreciate.:)

Hardware info
BIOS
 version: 2CCN18WW(V1.07) (02/01/2010)

AMD Athlon(tm) II Dual-Core M320

System Memory
 2GiB

VGA compatible controller 
product: ATI Technologies Inc

                vendor: ATI Technologies Inc

                physical id: 5

                bus info: pci@0000:01:05.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: pm msi bus_master cap_list rom

                configuration: driver=fglrx_pci latency=0

                resources: irq:29 memory:80000000-8fffffff(prefetchable) ioport:7000(size=256) memory:92200000-9220ffff memory:92100000-921fffff

Sound Card Codec: Conexant ID 5069

---

### Post by -humanaut- on 2010-05-26
hmm... Check Jockey and see if theres any drivers (even maybe enable backports) for the ATI card.

---

### Post by grtech on 2010-05-27
> **-humanaut- said:**
> hmm... Check Jockey and see if theres any drivers (even maybe enable backports) for the ATI card.

It shows that Jockey is already updated with Karmic backports enabled:
jockey-gtk 0.5.5-0ubuntu3
jockey-common 0.5.5-0ubuntu3
fglrx-modaliases
Identifiers supported by the ATI graphics driver 2.8.660-0ubuntu4
:(
anyhow thanks for the reply.

---

### Post by lidex on 2010-07-09
For headphone jack-sense: 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by grtech on 2010-07-29
> **lidex said:**
> For headphone jack-sense: 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

Thanks lidex but unfortunately it didn't work.
As for the white with vertical black lines screen thing I am suspecting that there is a conflict or a bug on the ATI drivers code. On the windows I have never experience any of this problems.

---

### Post by lidex on 2010-07-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by grtech on 2010-09-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

```
uname -a = Linux lintop 2.6.31-22-generic #64-Ubuntu SMP Tue Aug 24 09:31:57 UTC 2010 i686 GNU/Linux
```

```
aplay -l = **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
dpkg -l | grep "alsa"
ii  alsa-base                            1.0.20+dfsg-1ubuntu5                       ALSA driver configuration files
ii  alsa-utils                           1.0.20-2ubuntu6                            ALSA utilities
ii  bluez-alsa                           4.51-0ubuntu2                              Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.25-2ubuntu1.2                         GStreamer plugin for ALSA
ii  libesd-alsa0                         0.2.41-5                                   Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                 1.2.13-4ubuntu4                            Simple DirectMedia Layer (with X11 and ALSA 

```

```
head -n 1 /proc/asound/card*/codec#*
Codec: Conexant ID 5069
```

---

### Post by lidex on 2010-09-15
Try updating your alsa install using the link in my sig.

---

### Post by grtech on 2010-11-27
> Try updating your alsa install using the link in my sig. 
I followed every step of the guide but the problem remains the same. It was a good try anyway, thanks.:)

I've also install the Opensuse 11.3 but the same problems occurs like the ubuntu 9.10. The sound jack sensor doesn't work, after several operational hours the system crashes (white screen with black stripes). And some times the system doesn't shutdown, it only goes on black screen but the laptop is still on.:icon_frown:

---

### Post by lidex on 2010-11-27
> **grtech said:**
> I followed every step of the guide but the problem remains the same. It was a good try anyway, thanks.:)

I've also install the Opensuse 11.3 but the same problems occurs like the ubuntu 9.10. The sound jack sensor doesn't work, after several operational hours the system crashes (white screen with black stripes). And some times the system doesn't shutdown, it only goes on black screen but the laptop is still on.:icon_frown:

Wow, where you been, brah?
You should have come back here directly after the update. That was just the first step. Anyway, have you tried the linxant driver?
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

