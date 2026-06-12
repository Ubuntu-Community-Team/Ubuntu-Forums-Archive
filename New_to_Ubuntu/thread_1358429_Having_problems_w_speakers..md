---
title: "Having problems w/ speakers."
date: 2009-12-18
forum: New to Ubuntu
---

### Post by radamez85 on 2009-12-18
My logitech speakers arent working when i plug it in to the computer. But when i plug in my mp3 player or my phone it works just fine.
-Am i missing something here ? the sound isnt muted.
-drivers ?

---

### Post by cgb on 2009-12-18
Think we need more information.  Do any speakers work with this computer?  How are they being connected, analog/digital?

---

### Post by northern lights on 2009-12-18
The phrasing of your question makes it sound as if your machine would otherwise output sound. If that was the case, then most likely your lineout is muted and your internal speakers / headphone jack isn't.
Check using *alsamixer*.

If your machine is generally quiet, please post the output of```
sudo lshw -C multimedia && aplay -l
```

---

### Post by radamez85 on 2009-12-18
> **northern lights said:**
> The phrasing of your question makes it sound as if your machine would otherwise output sound. If that was the case, then most likely your lineout is muted and your internal speakers / headphone jack isn't.
Check using *alsamixer*.

If your machine is generally quiet, please post the output of```
sudo lshw -C multimedia && aplay -l
```

Ok keep in mind im brand new to ubuntu. <3

-Yes my system outputs sound. 

-Its analog (i think), and definitely not usb.

-im download alsamixer to see whatsup. (update: dowloaded it, very confused as to how to use it)

-i played around in the prefrence > sound > output and whenever i switched around a few things, like to mono the sound would just come out of the laptop and ignore the speakers. when i played around with anaglog outputs, the first four worked on the laptop system and the last two options didnt work with either of the speakers.

Wow confused. I hope this information helps.

---

### Post by radamez85 on 2009-12-18
Ok now im really confused.
I downloaded alsamixer, and i dont know what happend, but my intergrated speakers play and i turned up the volume on my external speakers and its like they take over at a certain point when the volume is increased...

whats up with that ?

---

### Post by radamez85 on 2009-12-18
bumpppp

---

### Post by joes7 on 2009-12-18
If use modified BIOS, return settings to normal.

---

### Post by radamez85 on 2009-12-18
I have not modified my bios, nor do i have the knowledge of how to lol.

---

### Post by radamez85 on 2009-12-19
bump

---

