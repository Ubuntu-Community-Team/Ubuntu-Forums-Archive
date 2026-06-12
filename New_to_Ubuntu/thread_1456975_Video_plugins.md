---
title: "Video plugins?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by cjneill65 on 2010-04-17
Hey all.

I'm really new to Ubuntu, I just got it today (9.10).  Anyways, my friend sent me a DVD from a vacation she took, and I apparently don't have the right plugins.  She posted the same video on her personal site, and I tried it there with similar results.  I started looking at the various packages to download on here, and I have to say I'm pretty intimidated by the sheer volume of plugins (much more than I ever experienced using Windows, ha.).  I was wondering what the best all-around program would be to view wma, wmv, etc. video files (I've already seen gstreamer and totem, but I don't know which plugins are right for my version of Ubuntu).  Any help would be appreciated.

Regards,

Chris

---

### Post by desnaike on 2010-04-17
If you have not done so, go to medibuntu.org install the the codecs as instructed and also synaptic package manager and install ubuntu restricted extras that should take care of things for you.

---

### Post by cjneill65 on 2010-04-17
Which codecs should I install?  I see non-free-codecs, w32 and w64.  Any additional information about suggested packages would be even more helpful.  Sorry, like I said this is the first day I've had it.  I really hate being "that guy".

---

### Post by sandyd on 2010-04-17
> **cjneill65 said:**
> Which codecs should I install?  I see non-free-codecs, w32 and w64.  Any additional information about suggested packages would be even more helpful.  Sorry, like I said this is the first day I've had it.  I really hate being "that guy".
if your using 64 bit, install w64codecs. If your using 32 bit, install w64codecs.
And if you want to play encrypted dvds, install libdvdcss2 and libdvdread4

---

### Post by desnaike on 2010-04-17
If your running 32 bit ubuntu 32 bit codecs if 64 bit then 64 bit codecs

---

### Post by ubun2warrior on 2010-04-18
Hi
Go to the synaptics package manager and search for vlc and install it. It plays most of the formats.

---

### Post by 3rdalbum on 2010-04-18
In Medibuntu, you activate the repository and then install the "non-free-codecs" package. It brings in w32/w64codecs automatically, as well as all the Gstreamer plugins (the Good, Bad and Ugly ones).

---

