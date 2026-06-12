---
title: "getting sound working"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by tbrownarcher on 2010-10-30
I have ubuntu 10.10.  My sound does not work when playing a video ... but when i test it it works.

for instance a you tube fishing video sound does not work (any of them) but when i go to ... **_[SIZE="4"]system - preferences - sound - hardware - choose a device - test speakers[/SIZE]_** ...... the speakers play a 
sound.  

there are 2 soundblaster icons in the list one is analog the other is digital. the analog works but the digital does not.

So why does it work on one hand and not the other ?

I think i just don't know where to set it up. 


I have a soundblaster system

thanks,
Nate

---

### Post by tbrownarcher on 2010-10-30
No one has help on this one ?????

---

### Post by starcraft.man on 2010-10-30
> **tbrownarcher said:**
> No one has help on this one ?????

When you play a flash video, open soud preferences and go to applications tab. See alsa plugin, make sure it's max. Alternatively, in a terminal use:

alsamixer

and tab over to the pcm controller, push all the way up on the Up Arrow key. Push esc to quit. Hate when pcm gets muted. Also disable the digital hardware if your not using it might confuse other apps.

---

### Post by tbrownarcher on 2010-10-30
ok! what i did was install the updates that i did not know about ... the sound works.


This problem is fixed ... ty ty ty for the help

thanks,
Nate

---

