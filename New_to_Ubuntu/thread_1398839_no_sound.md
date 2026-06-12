---
title: "no sound"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by DD70 on 2010-02-05
[SIZE=2]Help. I have lost all sound!
What should i check for?[/SIZE]

---

### Post by chillicampari on 2010-02-05
First things I'd check would be the volume control to see if anything muted it, then the connections (if using external speakers). Then reboot to see if it clears up.  If not, then go from there and check the pulse audio controls and alsa mixer.

---

### Post by DD70 on 2010-02-05
[SIZE=2]how do I check the alsa and pulse controls. Done all the rest. Including ma change of speakers which were working fine on another computer[/SIZE]

---

### Post by chillicampari on 2010-02-05
I'm going from memory (I don't have regular Ubuntu anymore), but:

What I called the Pulse Audio control should be just the regular volume control, I'd take a look to see if it sees the sound card and nothing's muted. 

If that looks alright- on the command line:

alsamixer

and look for things set to zero or muted- "M"

and that's about all I remember on the first steps. 

There's some troubleshooting guides here: 

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

And something to try is searching the forum with your sound card model number, though that seems weird that it would just stop working but you never know.

---

