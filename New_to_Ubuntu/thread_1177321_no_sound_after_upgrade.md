---
title: "no sound after upgrade"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-06-03
Hi Ubumtu Community:

I upgraded to Jaunty Jackalope this morning and don't have no sound.

I've checked the forums for advice, fiddled with system > preference > sound settings, uninstalled pulse audio, and did the drill on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I'd be grateful if somebody could help me get my sound restored.

I have a Beheringer UCA202 external usb sound card. I bought it several years ago because one of the Ubuntu web pages said that it had drivers for ubuntu. I have not had problems with it.

Thanks,
Phil Smith
Duluth, GA

---

### Post by prvteprts on 2009-06-03
What is your machine? Laptop or desktop?

You may need to add some lines to /etc/modprobe.d/alsa-base.conf

---

### Post by Old Jimma on 2009-06-03
My machine is a desktop AMD-64.

What lines do I need to add to /etc/modprobe.d/alsa-base.conf ?


Thanks,
Phil Smith

---

### Post by prvteprts on 2009-06-03
The lines you need to add would depend on the sound card and/or the motherboard's chipset (if dealing with integrated sound). Try taking a look at this recently solved issue involving sound and graphics.

[http://ubuntuforums.org/showthread.php?t=1176892&page=2](http://ubuntuforums.org/showthread.php?t=1176892&page=2)

---

