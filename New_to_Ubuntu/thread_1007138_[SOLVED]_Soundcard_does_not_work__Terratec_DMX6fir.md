---
title: "[SOLVED] Soundcard does not work / Terratec DMX6fire 24/96 (ICE1712 Chipset)"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by jpka on 2008-12-10
My dmx6fire not produces any sound in Ubuntu 8.10. aplay -l says no devices; lspci shows strange VIA 1710 or 17xx, i don't remember (instead of normal 1712 / envy24 string)... I change many Ubuntu versions, machines, read many HOWTOs without any success. 
Same problem other people reports, like [http://ubuntuforums.org/showthread.php?t=189368](http://ubuntuforums.org/showthread.php?t=189368)

The solution I found is once load this card with Windows driver. I use win2k and this working driver [http://193.125.34.222:888/ftp/distrib/drivers/audio_DMX6fire_baddisk/dmx.zip](http://193.125.34.222:888/ftp/distrib/drivers/audio_DMX6fire_baddisk/dmx.zip)
*upd* [http://93.182.12.2:888/ftp/distrib/drivers/audio_DMX6fire_baddisk/dmx.zip](http://93.182.12.2:888/ftp/distrib/drivers/audio_DMX6fire_baddisk/dmx.zip)
then play some sounds under Windows.

After this, my dmx6fire fully works in Ubuntu 8.10 out-of-box. Also envy24control applet works.

---

