---
title: "Mute not working in 8.04"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Adamantus on 2008-12-12
I just recently installed Ubuntu 8.04 and everything seems to be working fine, except the sound control. The sound itself works fine, but I can't mute or even change the sound level. I have an HP dv5 which has touch sensitive buttons (including one for mute) and the sound icon says it is muted when I push it, but I still get sound. Also, using the slider in the icon doesn't affect the volume level either. If I change the volume level in, say, Totem, the volume will change, but it seems that Gnome can't control the volume. What could be the problem?

---

### Post by nhasian on 2008-12-12
I have an HP DV9500 and i was able to fix my volume slider in:

System -> Preferences -> Keyboard Shortcuts

not sure about the mute button though, that worked for me.

---

### Post by Adamantus on 2008-12-12
It's not that the buttons on my keyboard aren't working (pressing the mute buttons actually mutes the icon in Gnome). But, even when the icon is muted, I still get sound. It's that the Gnome icon doesn't seem to be working.

And I should note: I had this same problem before in 8.04 and fixed it before by updating to 8.10, but I recently downgraded because 8.10 was giving me problems.

---

### Post by Adamantus on 2008-12-12
bump

---

### Post by sneeks on 2008-12-12
now then,i still get this problem myself now and again(when i do some fiddling!!!!)i found that the sound controller is at fault,or it gets a bit lost so to say.
i normally use alsa for sound but when it does this for me,i  just go back to the oss controller,then flit back to alsa.
it also depends on what programs im running too,if i run sl,it will always give me sound whatever i do...will work on that 1 me thinks.

---

### Post by Adamantus on 2008-12-12
Okay, I just tried it again and now neither the mute button or volume slider on my computer affects the sound icon. 

I should add that, every 30 minutes or so (it's actually really random), my computer makes a noise from the speakers, even if I'm not doing anything.

---

### Post by suncoolsu on 2008-12-12
Right Click on the Speaker icon on the panel -> Preferences -> Select Appropriate Options (Say - HDA Intel (Alsa Mixer) for Intel Card) and Front for the Laptop Speakers.

HTH
B.

---

### Post by Adamantus on 2008-12-12
Okay, I opened Volume Control through the sound icon and tried to mute the master control, but that didn't affect the sound. When I muted the PCM and Front sound things, it did mute the sound though. Is that the problem? It seems like muting the icon mutes the master, which isn't affecting the sound.

---

### Post by Adamantus on 2008-12-12
Thanks, that seemed to work. It's weird: I tried that last night and it didn't work. I do the same exact thing today, and now it works like a charm. Thanks again.

---

### Post by suncoolsu on 2008-12-12
You can say thanks by clicking the icon :D

---

