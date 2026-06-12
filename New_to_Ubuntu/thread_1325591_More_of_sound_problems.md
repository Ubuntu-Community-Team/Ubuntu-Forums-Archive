---
title: "More of sound problems"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by mdrsc on 2009-11-13
Hey,
I tried to do what is suggested in the site [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I get this information
 	Code:
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
and I can see also the ALSA mixer, however in the sound preferences box there is no hardware detected, there is really nothing.

I am just an amateur, so HELP!!!!

---

