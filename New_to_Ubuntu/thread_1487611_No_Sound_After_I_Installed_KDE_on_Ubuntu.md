---
title: "No Sound After I Installed KDE on Ubuntu"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by dkc.com on 2010-05-19
Hi Friends,

Recently I installed Ubuntu 10.04 LTS on my Dell Inspiron 1520 using WUBI. Everything was pefect but I missed the glossy desktop of Vista so I decided to install KDE latest release. I did using the following sudo command by the help of howtogeek.com's help:

sudo apt-get install kubuntu-desktop

It has been installed and I am enjoying it but there is no sound coming out of my system. Video is there. 

Can please any body help me solving that?

Regards to all.

---

### Post by julio_cortez on 2010-05-19
Maybe it is the case, maybe it's not (it looked weird to me when I saw it): in Kubuntu 10.04 I had no audio in movies and I figured I had to manually "raise the volume" for PCM from the volume settings, so you might want to check the volume settings before doing anything else.

Indeed, after upgrading from 9.10 PCM was muted (volume slider set to 0) and so it was when I did a fresh install (again, PCM volume slider was back to zero).
if this is the case, just changing PCM volume would do the trick ;)

---

### Post by dkc.com on 2010-05-19
Thanks dear.

That was the case indeed. There is sound there.

But it is indeed very low even at 100% volume.

Regards.

---

### Post by julio_cortez on 2010-05-19
> **dkc.com said:**
> That was the case indeed. There is sound there.
But it is indeed very low even at 100% volume.
Happy it's solved. :)

For the volume being too low, well, is also the "Master" slider set to its maximum?
If not, I think you can increase the general volume by moving it upwards.

If it's already at its maximum value, well.. Do you have a monitor with built-in speakers?
Maybe volume can be further increased using the monitor OSD then ;)

Other than that, I suppose something can be done by editing ALSA or JACK files, but I'm not the one that can guide you in that process unfortunately.
I've too little experience at the moment to try modifying system files manually :P

---

### Post by dkc.com on 2010-05-19
Thanks for your help very much.

What you have described is too technical for me to do but I am happy with what I have got at the moment and enjoying my Kubuntu so will seek that type of help later on.

Regards.

---

### Post by dkc.com on 2010-05-19
Thanks for your help very much.

What you have described is too technical for me to do but I am happy with what I have got at the moment and enjoying my Kubuntu so will seek that type of help later on.

Regards.

---

### Post by julio_cortez on 2010-05-19
You're welcome.
I couldn't help you further anyway, so I'm kind of happy you consider it solved.

Maybe you can mark the thread as [solved] so everyone knows there's a solution to try in it ;)

---

