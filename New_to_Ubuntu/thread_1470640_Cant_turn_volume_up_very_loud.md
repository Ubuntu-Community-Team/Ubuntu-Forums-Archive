---
title: "Cant turn volume up very loud"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Falc7 on 2010-05-03
I am pretty sure that my laptops full sound volume is not being used by lucid. I have turned all the dials (including kmix and the media players sound) up to full, and the volume still isen't very loud. What can i do?

---

### Post by llamabr on 2010-05-03
```
alsamixer
```

post any errors

---

### Post by Falc7 on 2010-05-03
The 3rd bar is 3/4 full. The 5th and 6th (both mics) and beep are completely empty. The one labelled S/PDIF dosen't have a bar there

---

### Post by garvinrick4 on 2010-05-03
> **Falc7 said:**
> I am pretty sure that my laptops full sound volume is not being used by lucid. I have turned all the dials (including kmix and the media players sound) up to full, and the volume still isen't very loud. What can i do?
In Gnome it is code:

gnome-volume-control

In its preferences there is a control to raise the volume output.

---

### Post by waspbr on 2010-05-03
You also use the graphical interface by installing the "gnome alsa mixer" package in the software centre.

The you can adjust some of you volume controls just as you would do with the alsamixer.

But for extra volume you can try to use the volume applet on your gnome indicator panel. left click on it and go to sound preferences, you should notice that the bar goes beyond 100%, there you can augment your audio a bit.

---

### Post by Elfy on 2010-05-03
Had someone on irc yesterday - 2 soundcards used F6 in alsamixer to see the other card and found levels low in that one.

---

