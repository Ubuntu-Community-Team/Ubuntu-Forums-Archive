---
title: "Very low sound with earphones"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-03-17
Hi.

The speakers on my laptop provides high volume, but when I connect an earphone or earplugs, the volume is incredibly low. I have tried with different earplugs, but with no success.

How do I fix this? Any help would be appreciated.

---

### Post by thehouseofho on 2009-03-17
You would need to change the settings in the mixer for the line you have your headphones plugged.

Open terminal and type:

alsamixer

You should see a whole bunch of bars labeled Mic, Speaker, PC Beep, Line In etc. Use the left/right arrow key to move to the correct input and use the up arrow to increase the sound level for that input.

---

### Post by Mr.Kuchinawa on 2009-03-18
Thanks and sorry for the late reply:

It appears that I have to manually lower the headphone slider in alasamixer on each log-in, because then it suddenly works. Is there a way to fix this?

---

