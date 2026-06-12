---
title: "DVD to .Mov?"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by eric2006 on 2011-05-23
I'm working on a video project in Final Cut Express (different computer), and I'm trying to convert some old DVDs I made into .mov or .dv so I can edit them (it's an old version of FCE). I was wondering if there is an easy way to do this. I've found acidrip and handbrake, which seem to make mpegs and avi's but it looks like I would still need another program to do the final conversion. I have Ubuntu 11. Wondering if there is an easy way to do this. Thanks,

Eric

---

### Post by Petrolea on 2011-05-23
Check out ffmpeg. It has tons of formats to convert to.

---

### Post by TeoBigusGeekus on 2011-05-23
After you get the avi, try to convert it to mov with ffmpeg
```
ffmpeg -i video.avi -target pal-dvdvideo video.mov
```
Replace pal with ntsc if applicable.

---

### Post by enjoijesus94 on 2011-05-23
Iv used winff in ubuntu and it helps me convert files

just go to ubuntu software center and type "winff" in the search bar and install it

or in synaptic package manager to install it

---

