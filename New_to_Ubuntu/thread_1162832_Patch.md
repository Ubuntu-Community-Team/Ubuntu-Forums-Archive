---
title: "Patch"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by yuki_Michiyo on 2009-05-18
I found the patch for a bug but as I'm a n00b I don't know what I should do with it.](*,)

The patch --> [http://bugzilla.gnome.org/attachment.cgi?id=128492&action=view](http://bugzilla.gnome.org/attachment.cgi?id=128492&action=view)
The bug --> [http://bugzilla.gnome.org/show_bug.cgi?id=571347](http://bugzilla.gnome.org/show_bug.cgi?id=571347)

help?

---

### Post by XCan on 2009-05-18
The patch you're referring to is a .diff file. It contains the changes made to the a source file. This means that you would first need the source code, to apply the patch to, and then you would have to recompile the patched version.

Applying the patch can be done using the 'patch' command. Compiling can usually be performed using 'make' and 'make install'.

---

### Post by yuki_Michiyo on 2009-05-18
How do I use the patch command and all?	:???:

---

### Post by loell on 2009-05-18
synopsis of patch is usually
**patch < -p0 name_of_the_patch.any_file_xtension**

---

