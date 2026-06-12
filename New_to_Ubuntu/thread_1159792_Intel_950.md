---
title: "Intel 950"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by bluescreenofhope on 2009-05-15
I have intel 950 integrated graphics. I updated the video driver that was just released for ubuntu 9.04. The problem I am having is flash videos are choppy and laggy . Is there anyway to fix this ? or is this just a thing linux users have to deal with?

---

### Post by abeisgreat on 2009-05-15
I fixed this on my friends MINI9, it has to do with the flash software your running, not the driver. 

Go into Synaptic, search for installed packages, with the keyword "flash" there might be a few, including  adobe-flashplugin, flashplugin-nonfree, then search for "swf" and remove the one's like swfdec, swf-player, swf-mozilla, etc. I removed all those, then reinstalled flashplugin-nonfree

BE VERY CAREFUL ABOUT WHAT YOU REMOVE
before you do anything post the packages you found, and I'll tell you if its safe to trash em

---

