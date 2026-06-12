---
title: "can't install MToolsFM in Ubuntu 9.04!"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Jawsman on 2009-05-21
Hi there...
I installed Ubuntu 9.04 a few days ago
and now I can't install MToolsFm... :(

I've been said that there was a package back in 8.10...
But now I can't find it in Synaptics package manager...

I downloaded the source from the internet, and I cant compile it...
I get this error when executing ./config :


checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: MToolsFM needs GTK+ V1.2 or better


I don't now what this means...
I run this command for your information...

$ pkg-config --modversion gtk+-2.0
2.12.9

---

### Post by Jawsman on 2009-05-21
I passed over this mess...
I did a minor tweak on the configure file (shell script)


But now when I execute the "make" command, I get the following:
(among other errors)

mtoolsfm.c:22:21: error: gtk/gtk.h: No existe el fichero ó directorio


Where can I get this header?
any idea about WHY is this mess ocurring?

Thanks a lot if you help me :)

---

