---
title: "DVD Playback"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by CosmicFlux on 2010-08-21
Hi,

I'm using an older system (with only 512RAM) so I've installed 9.04. I've installed all codecs and updates but I still can't play DVD's. I don't know what the problem is. Movie player just says a required DVD Source plugin is not installed. Any ideas?

Cosmic

---

### Post by realzippy on 2010-08-21
Have you installed:

libdvdread3 libdvdnav4 libdvdcss2 ubuntu-restricted-extras ?

---

### Post by jonnywombat on 2010-08-21
All you need to know for playing encrypted (ie commercial) dvd's is in this how to [here]("https://help.ubuntu.com/community/Medibuntu")

Add the repository and then install the "libdvdcss2" package that realzippy mentioned.

hth

---

### Post by mapes12 on 2010-08-21
System>Admin>Synaptic: "ubuntu-restricted-extras" and also "vlc" and install them. 

Then go here and follow the instructions to install the additional codecs:- [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then try the DVD with the vlc player.

---

