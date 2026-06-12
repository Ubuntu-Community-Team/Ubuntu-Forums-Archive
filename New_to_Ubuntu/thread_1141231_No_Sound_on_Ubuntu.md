---
title: "No Sound on Ubuntu"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by mllelinotte on 2009-04-28
I have lost all sound on my computer.  It was fine this morning, but now no sound. not for online vids or music, not for my music, not for DVD's.
nothing. I went to Preferences Sound and clicked "test" next to all the sound testers and this is the error massage i got:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused

anyone know how i can get sound back?

---

### Post by Bölvaður on 2009-04-28
in Sound under preferences you should test if changing to ALSA or any other type of audio will give you any sound.

If you get no sound at all. please list the ones that do not work.

---

### Post by mllelinotte on 2009-04-28
i tried them all and got the same error message for all of them.
So,
none of the HDA, ALSA, OSS, Pulse Audio, or Autodetect work.

---

### Post by mister_p_1998 on 2009-04-28
Just shutdown & reboot a couple of times, one of my pc's does this every time after a kernel update.

Steve

---

### Post by mllelinotte on 2009-04-28
well that was a no brainer :P
i got the sound back after the second reboot.

thanks!

---

### Post by mister_p_1998 on 2009-04-29
No problem, my 2.8 ghz P4 does it all the time, but my 3.00 ghz has never done it, both have soundblaster pci soundcards. Never figured it out yet?
The 2.8 is an HP motherboard, whats yours?

Steve

---

