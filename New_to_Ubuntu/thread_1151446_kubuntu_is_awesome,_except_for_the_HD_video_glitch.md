---
title: "kubuntu is awesome, except for the HD video glitch I'm having"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by PlaceboMessiah on 2009-05-06
Everything I'm playing with is great so far.  I even fiddled with the terminal enough to remove a bad update (with assistance from the more advanced forums)

I really wanted to try that [video performance hack]("http://ubuntuforums.org/showthread.php?p=7223227#post7223227"), alas I lack the skills.

In fact I'm not even sure that's the problem.   I'm on a toshiba satellite A200-FE0 and whenever I play video files that were sourced from HD (768/1024) the video bogs right down during a high-bandwidth motion sequence.  Basically anything that requires the video codec to work harder...sometimes the cpu load is so high that even the sound gets garbled.

I'm willing to attempt the *intel graphics performance guide* again if someone is willing to walk me through some of the more technical aspects.

thanks

---

### Post by PlaceboMessiah on 2009-05-11
is anyone else experiencing this bug?

---

### Post by PlaceboMessiah on 2009-05-11
here's my info:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

glxgears

808 frames in 5.0 seconds = 161.553 FPS
778 frames in 5.0 seconds = 155.424 FPS
834 frames in 5.0 seconds = 166.762 FPS
806 frames in 5.1 seconds = 159.455 FPS
716 frames in 5.0 seconds = 143.159 FPS
817 frames in 5.0 seconds = 163.304 FPS
806 frames in 5.0 seconds = 161.096 FPS
812 frames in 5.0 seconds = 162.227 FPS
798 frames in 5.0 seconds = 159.561 FPS

seems kinda slow

I'm on a Toshiba Satellite running in high performance mode
model: A200-FE0 1.66ghz, 1.5gig ram

glxinfo | grep "direct rendering"
Yes

---

