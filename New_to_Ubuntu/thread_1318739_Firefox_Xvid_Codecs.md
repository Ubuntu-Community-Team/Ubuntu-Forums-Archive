---
title: "Firefox Xvid Codecs"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-11-07
Hi, I'm trying to watch some videos encoded in DivX/XviD, but apparently Firefox cannot play them (black screen/play icon displayed, no audio, no video).

Can somebody please tell me where to find the proper codecs?

My Firefox is the official Mozilla version 3.5.5, not the Ubuntu version.

Thanks, 
SPARTAN-118

---

### Post by SPARTAN-118 on 2009-11-09
Okay, here's what I've done so far:

I've compiled the Xvid codec from source (not sure if it's for Firefox) and now I'm stuck on this step: 

Voila, xvidcore is installed on your system, make sure your runtime
linker knows about the xvidcore prefix lib dir where it is
installed. And make also sure that it generates a symlink to its
SONAME. In case it would do not take care of the symlink itself:
  # cd ${prefix}/lib
  # ls libxvidcore.so.*
    ls should list at least one libxvidcore.so.MAJOR.MINOR file
  # ln -s libxvidcore.so.MAJOR.MINOR libxvidcore.so.MAJOR

You may also add a .so link to .so.MAJOR, so that applications linked
against .so are in fact linked to .so.MAJOR and thus ensures better
binary compatibility as we take care not changing the MAJOR number
until there is an incompatible ABI change.
  # ln -s libxvidcore.so.MAJOR libxvidcore.so


I don't understand it at all; is it something I need to do?

Also, I installed a package from Synaptic... "mozilla-plugin-vlc".... and it said that it was for the Divx codec, but I'm still not able to play the Xvid movie.

Help with building the source (if it's for Firefox) would be appreciated, or even if someone can build a Debian package for me (no idea how to do that... tried following the INSTALL file and it didn't work...)

Thanks,
SPARTAN-118

---

