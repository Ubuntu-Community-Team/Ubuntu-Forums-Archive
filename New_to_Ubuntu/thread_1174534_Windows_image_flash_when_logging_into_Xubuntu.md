---
title: "Windows image flash when logging into Xubuntu?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by demiliterizedzone on 2009-05-31
Hi all,

Anyone know how to get rid of this?  Has anyone encountered this before?  Whenever I log into Xubuntu, a cut off windows image flashes out of nowhere and quickly disappears.  This happens on both of my machines with Linux.  Maybe Microsoft is just haunting me for leaving Windows...

Much appreciated,
DMZ

---

### Post by nandemonai on 2009-05-31
Is this after you have just restarted after using Windows for a while? Sounds like garbage left in your video RAM.

---

### Post by 3rdalbum on 2009-05-31
The version of the Nvidia driver that shipped with *buntu 8.10 has an odd glitch where it briefly displays the old contents of the video RAM at certain times, like during the allocation of window space.

Nothing to worry about on a single-user machine, but obviously if your computer crashes while viewing porn and then there's someone looking over your shoulder afterwards, that could be embarrasing ("Why did a picture of a naked woman appear for a split second then?"). Upgrading your graphics card driver will fix the problem.

---

