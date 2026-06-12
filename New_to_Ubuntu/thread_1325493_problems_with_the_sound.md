---
title: "problems with the sound"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by mdrsc on 2009-11-13
Hi everybody,
I am new in the forum and I will really appreciate any help.
I just installed the new version of Ubuntu 9.10 and I can not hear a sound. When I go the sound controller there is no hardware available, how can I install my sound card hardware? I forgot to mention that my sound card was recognized in 9.4 and 8.4, but now it is not recognized after the upgrade


Please, help!!

---

### Post by nadian on 2009-11-13
have a look at
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by mdrsc on 2009-11-13
Hey,
I tried to do what is suggested in the site [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I get this information
```
mrayo@mrayo-laptop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
mrayo@mrayo-laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 

```and I can see also the ALSA mixer, however in the sound preferences box there is no hardware detected, there is really nothing.

I am just an amateur, so HELP!!!!

---

### Post by camaron1 on 2009-11-13
> **mdrsc said:**
> Hey,
I tried to do what is suggested in the site [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I get this information
```
mrayo@mrayo-laptop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
mrayo@mrayo-laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 

```and I can see also the ALSA mixer, however in the sound preferences box there is no hardware detected, there is really nothing.

I am just an amateur, so HELP!!!!

Do you have installed GNOME ALSA MIXER? if not do so and see if detects your card

---

### Post by mdrsc on 2009-11-16
Hi,
I partially solved the problem with the sound problem. I removed the pulseaudio package at it has been suggested in other threads and also I installed the alsa-mixed package. Now I have sound when I used the headphones at least. I do not have sound in the front speakers, but anyway this is better than nothing. Any help to unmute the front speakers?

---

### Post by camaron1 on 2009-11-16
> **mdrsc said:**
> Hi,
I partially solved the problem with the sound problem. I removed the pulseaudio package at it has been suggested in other threads and also I installed the alsa-mixed package. Now I have sound when I used the headphones at least. I do not have sound in the front speakers, but anyway this is better than nothing. Any help to unmute the front speakers?

Open Gnome alsa mixer under Sound and Video and start tweaking it. You probably have some slider down or ticked as muted

---

### Post by mdrsc on 2009-11-17
Hi,
I did that but nothing happens, I think when I installed the ubuntu 9.10 I forgot to turn on the sound in the front speakers, you think is this the problem and if it is so, any idea of how to solve it?
Thanks a lot for the help

---

