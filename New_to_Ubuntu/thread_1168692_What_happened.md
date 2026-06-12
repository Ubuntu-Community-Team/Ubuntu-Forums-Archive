---
title: "What happened?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ChemShock on 2009-05-24
I shut down my computer, with auto-detect working. Then hI shut it down now it doesnt work. What happened?

I wish I can be more specific but that's it. I installed some programs, some sound events, and that's it. Oh, and I am the only user.

---

### Post by NHArticleTen on 2009-05-24
so nothing happens when you depress the on button?

no POST or anything?

wow...

---

### Post by albinootje on 2009-05-24
> **ChemShock said:**
> I shut down my computer, with auto-detect working. Then hI shut it down now it doesnt work.

Is it a laptop ? Did your battery run out of power ?
Can you tell us the brand and type of your computer ?

---

### Post by pbpersson on 2009-05-24
If it is a desktop, to remove all power unplug it from the wall, wait several seconds, and then plug it in again.

If it is a laptop, to remove all power unplug it from the wall, remove the battery, wait several seconds, and then reverse the procedure.

If none of this helps it is my professional opinion that something has gone terribly wrong.

---

### Post by ChemShock on 2009-05-24
Its a toshiba laptop and autodetect "tests" but there is no sound.

Im on AC

Oh and im using ubuntu not kubuntu.

I tried the Battery fix, it didnt work.

I think its defaulting to a card that doesn't exist can I change that?

---

### Post by NHArticleTen on 2009-05-24
> **ChemShock said:**
> Its a toshiba laptop and autodetect "tests" but there is no sound.

Im on AC

Oh and im using ubuntu not kubuntu.

I tried the Battery fix, it didnt work.

I think its defaulting to a card that doesn't exist can I change that?

so you're just having a problem with the sound?

---

### Post by ChemShock on 2009-05-24
Yes, my problem is only sound. Auto-detect for sound isnt working. The test comes up, but nothing through the speakers

---

### Post by pbpersson on 2009-05-28
Discover what sound chip you have and then Google it with Ubuntu in front of it, like:

> Ubuntu YM2151

and see what other people have done to solve your problem

---

### Post by albinootje on 2009-05-28
It might make more sense to use the output of :
```

lspci (the line about the soundcard)
aplay -l
cat /proc/asound/cards 

```

---

### Post by ChemShock on 2009-06-01
That line command didnt work for me. I had other issues so I just wiped the entire thing and restarted, but guess wat same problem. 

The good news is I narrowed down the issue. Only until do I change the login sounds (System>Administation>Login Window) does it only Autodetect loses sound. If I change it back and restart, I'm normal. So I ask, "What happened?"

There's gotta be a fix!

---

