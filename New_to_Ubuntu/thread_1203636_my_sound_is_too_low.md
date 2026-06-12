---
title: "my sound is too low"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-03
i set the sound from the volume control center to the maximum and still the sound(for example watching videos on youtube...) is too low.

any ideas on how to raise it?

---

### Post by tvtech on 2009-07-03
Buy a large external amplifier and a killer set of speakers.

---

### Post by Zzl1xndd on 2009-07-03
What is your pcm volume set too?

---

### Post by heyyy on 2009-07-03
> **tweakedenigma said:**
> What is your pcm volume set too?

i dont think i understand you...,could you tell me how to check this?

---

### Post by Zzl1xndd on 2009-07-03
If you open the mixer for your should options, it should have a listen of multiple volume controls. If the pcm volume is set low it might be the cause of your problem. 

to get there click your sound icon and select Volume control.

---

### Post by heyyy on 2009-07-03
> **tweakedenigma said:**
> If you open the mixer for your should options, it should have a listen of multiple volume controls. If the pcm volume is set low it might be the cause of your problem. 

to get there click your sound icon and select Volume control.

yes already done that but the problenm remmains..

---

### Post by PureLoneWolf on 2009-07-03
Try launching a terminal and running

alsamixer

set everything to maximum in the screen that appears and see if that helps.

---

### Post by heyyy on 2009-07-03
> **PureLoneWolf said:**
> Try launching a terminal and running

alsamixer

set everything to maximum in the screen that appears and see if that helps.

i think this is the volume control again but in terminal(?)
so there was nothing to raise because everything was already in the maximun

---

### Post by tessk on 2009-07-03
is this a new problem? ie, was the sound ever louder than what you're currently getting?

---

### Post by sdlynx on 2009-07-03
go to volume control and then preferences and try checking some of the other options that seem like they might help and raise the sliders for them

---

### Post by heyyy on 2009-07-03
> **tessk said:**
> is this a new problem? ie, was the sound ever louder than what you're currently getting?

yes it was...

---

### Post by ohsnapchexmixosg on 2009-07-03
i had th same issue when i loaded ubuntu jaunty onto my netbook, turns out the line out settings were at 50%, which you can check by right clicking the volume control and hitting volume control. gl

**Edit**
if you do search for low volume in the forums, there are plenty of similar posts.

---

### Post by ecmatter on 2009-07-04
I had the same problem.  This fixed it:  [http://ubuntuforums.org/showthread.php?p=5080647](http://ubuntuforums.org/showthread.php?p=5080647)

---

