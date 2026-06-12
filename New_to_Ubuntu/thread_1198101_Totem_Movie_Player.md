---
title: "Totem Movie Player"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-06-27
Is there any way to update to the newest version of Totem in Ubuntu 8.10?

---

### Post by mc4man on 2009-06-27
well you can, why one would want to, I'm not sure.

The safest and most dependable method would be to  install as a package set.
Your choices would be to find a ppa for intrepid that has the newer totem, build your own, or another way that's not worth mentioning. (imo)

Like a lot of other 'apps' totem is split up into various packages - totem, totem-gstreamer, totem-xine, totem-common and several plugin packages. 

If you were to build it's much better to build a 'totem' package set vs. a make install.

In that case you could use the jaunty totem source, apply the jaunty totem diff and build a deb set. It would only require one small edit to the control file and installing python-coherence (the intrepid version is fine), though glancing at the build log suggests a few additional things could be enabled if desired.

while i mainly use hardy I have an intrepid install, went ahead and did, seems fine.
The only thing i haven't tested was the mozilla plugin ( guess i'd have to find a site that uses it.

considering this is posted in the beginner forum I don't know if that's what your up for, and again don't know if there is any point/advantage here.

screen shows package set built

edit
have 2 package sets, one orig., other with the publish and mythtv plugins enabled. Will install easily into any 8.10, can be uploaded to mediafire if requested

---

