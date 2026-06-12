---
title: "losing usb mouse on new karmic installation"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by maeseele on 2009-11-14
I just did a clean install of Karmic Koala on a Dell PC. But every time after a couple of minutes I seem to lose connection with the usb mouse, no matter which usb port I put it in. My only option to recover from this seems to do ctrl-alt-del and restart. Then again, the mouse functions properly for a couple of minutes, and then stops working again.

Anybody has any ideas how to fix this?

---

### Post by pootan on 2009-11-14
Try having a look in your bios settings for legacy usb support options for your mouse.

---

### Post by maeseele on 2009-11-14
my BIOS doesn't say anything about usb mouse support, only that all usb controllers are on and all ports are on

---

### Post by maeseele on 2009-11-14
I also tried the 

acpi=force irqpoll

fix, described here:

[http://ubuntuforums.org/archive/index.php/t-189572.html](http://ubuntuforums.org/archive/index.php/t-189572.html)

but that didn't work

---

### Post by pootan on 2009-11-15
All I can suggest is that you do a thorough search on the internet for your Bios, Mouse brand and version with Ubuntu included in the search. I have had a similar problem with my blue tooth usb keyboard and one obscure line on one page helped me to fix it. Good luck.

---

