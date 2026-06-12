---
title: "messed up video playback"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by libihero on 2011-02-17
for some reason the past couple days my video playback has been messed up.  i thougt it might be graphics driver edgers i've been using, and i returned to default, but it stayed the same

---

### Post by libihero on 2011-02-17
sorry my thumbnail messed up

---

### Post by libihero on 2011-02-18
bump

---

### Post by Keiran230 on 2011-02-18
I don't know what the issue could be, but if you mention the exact model of graphics card you have, someone else may stumble on this thread and be able to help.

Last time I had an issue similar to this, disabling Compiz-Fusion fixed the problem. It was a driver issue, but disabling desktop effects was a workaround. See if this works for you too.

---

### Post by libihero on 2011-02-22
i dont think its a graphic card problem, i think its a video output problem... how can i get it to default? and my video card is a Radeon X1200

---

### Post by Ben Page on 2011-02-22
Have you tried changing the video output in media players  preferences? Is this issue appearing across all media players? Try downloading VLC and see if this issue appears there. Try reinstalling/updating ubuntu-restricted-extras.

---

### Post by libihero on 2011-02-22
so i decided to downgrade to 10.04.2 from 10.10 since i was having other issues, and it was fixed. then it happened again :| i dunno if its a setting i have... i did what you said but it didnt fix it

---

### Post by Ben Page on 2011-02-23
Are you using fglrx or proprietary ATI drivers? Try switching them around. If you boot from the Live CD and play video, does this happen then too? (download the codecs needed)

---

### Post by clhsharky on 2011-02-23
libihero

Had same problem with latest edgers on ATI Radeon X1xxx chip.
Changing plugin fixed it for now.

System>Preference>Multimedia Systems Selector>Video>Plugin
Select 
X Window System (No Xv)

May have to change plugin in Mplayer or VLC if you use them.
Hopefully edgers drivers will be corrected or not, will see.


Sharky

---

### Post by libihero on 2011-02-23
thanks!!!

---

### Post by libihero on 2011-02-26
ok this worked for videoplayers like totem, but my screensaver and skype still have messed up video output

---

### Post by libihero on 2011-02-27
bump :(

---

### Post by libihero on 2011-03-01
bump

---

### Post by TechWiz2100 on 2011-03-01
Try checking your OpenGL setup/settings

---

### Post by libihero on 2011-03-01
how do i do that?

---

### Post by TechWiz2100 on 2011-03-01
> **libihero said:**
> how do i do that?

Settings are managed by your graphics driver control center usually

As for libraries and what not uhh you can try:
libglew1.5
libglewmx1.5
libglu1-mesa
libglu1-meda-glx
libglee0d1

just to name a few OpenGL related packages I have installed

Also check skype's and what not's dependencies

---

### Post by libihero on 2011-03-04
there is no graphic control center for my card :( is there anyway i can change all the video settings to default???

---

