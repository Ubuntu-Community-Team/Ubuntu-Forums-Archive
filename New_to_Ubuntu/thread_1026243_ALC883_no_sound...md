---
title: "ALC883 no sound.."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Schok on 2008-12-30
hi, new user here [less than a week].
Currently im using 8.10 on my Acer Aspire 5050 with this sound card:

card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And the problem is there is no sound at all and I`ve tried numerous guides n solutions from the forums yet nothing worked. There is only sound when I plug in my headphones.

Is there anyone out there who has the same model/specs like mine n worked it out?

---

### Post by Schok on 2008-12-31
okay now i got the sound working, but i had to unmute everything [except the mic] to get the laptop speakers make some noise. But now the downside is, when i plug in the headphones, it won't detect it so both the headphone and the speakers make sound.

help?:(

---

### Post by Schok on 2008-12-31
FIXED [i think]:

Headphones Volume = **Front Speakers**

Laptop Speakers Volume = **Surround Speakers**

The Volume Control panel has it all mixed up. To make my life easier, in System>Pref>Sound i set the **surround** to be controlled with the keyboard. So that when i plug in my headphones i just mute it up with my keyboard default volume control buttons and use my headphone's volume knob[it came with it].

If anyone found a way to set back all the correct volume settings for each speakers, please let me know..thanx

---

### Post by Schok on 2009-01-07
Bump! can anyone help, please?  :-(

---

### Post by Hugo Bio on 2009-01-21
Add "options snd-hda-intel model=**auto**" (without quotes or bold) to your /etc/modprobe.d/alsa-base .
This way, speakers works ok, but not the earphones. If you comment the line above, the earphones works. Kinda anoying, but i haven't figured other way of doing so.

---

