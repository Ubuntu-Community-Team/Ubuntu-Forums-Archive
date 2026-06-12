---
title: "no sound from amarok 2"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by melrokz on 2009-11-17
Hi i'm Melvin, and i'm running amarok 2 on Ubuntu 9.04 (not kubuntu)
Please help me with this: no sound while playing. 
I've configured audio in amarok to pulseaudio and test button gives a proper output!
But nothing plays in amarok 2...

---

### Post by melrokz on 2009-11-17
error:
> xine is asking to seek behind the end of the data stream 

---

### Post by laidback on 2009-11-17
Try System>Preferences>Sound to check your audio outside Amarok, or Alsa mixer:-

$ alsamixer

to adjust volumes and what's switched on,

or I have also used :-

Top right of screen loudspeaker icon, press it, then click Volume Control..., you'll get a window that allows you to adjust volumes via a mixer system.

You could also install Gnome Alsa Mixer which is a gui for Alsa mixer. It's in the repositories.

Hope this helps track down the problem.

---

