---
title: "GTK+ make problems"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by GrahamBright on 2008-12-10
Hi, finally managed to get ./configure to complete for gtk+-2.11.0, however, now get the following errors when I run 'make'. Any ideas, anyone?

creating libpixbufloader-bmp.la
/bin/sed: can't read Tutorial/gtk+-2.11.0/gdk-pixbuf/libgdk_pixbuf-2.0.la: No such file or directory
libtool: link: `Tutorial/gtk+-2.11.0/gdk-pixbuf/libgdk_pixbuf-2.0.la' is not a valid libtool archive
make[3]: *** [libpixbufloader-bmp.la] Error 1
make[3]: Leaving directory `/home/graham/Documents/GTK+ Tutorial/gtk+-2.11.0/gdk-pixbuf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/graham/Documents/GTK+ Tutorial/gtk+-2.11.0/gdk-pixbuf'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/graham/Documents/GTK+ Tutorial/gtk+-2.11.0/gdk-pixbuf'
make: *** [install-recursive] Error 1
graham@laptop:~/Documents/GTK+ Tutorial/gtk+-2.11.0$

---

### Post by Michael.Godawski on 2008-12-10
hi GrahamBright, 
why are trying to compile the 2.11 version? The latest release is the 2.14.

[LIST]
[*][http://www.gtk.org/download-linux.html](http://www.gtk.org/download-linux.html)
[/LIST]
Have also a look at the installation guide. Some additional applications and dependencies are required to build gtk+.


[LIST]
[*][http://library.gnome.org/devel/gtk/unstable/gtk-building.html](http://library.gnome.org/devel/gtk/unstable/gtk-building.html)
[/LIST]
Also check in Synaptic what version you already have installed.

---

### Post by GrahamBright on 2008-12-12
Thanks, all dependencies resolved - but still a file creation error as per last post. Synaptic gives no clue whatsoever!

---

### Post by PmDematagoda on 2008-12-12
> **GrahamBright said:**
> Thanks, all dependencies resolved - but still a file creation error as per last post. Synaptic gives no clue whatsoever!

Did you try running:-
```
make clean
```
before make after resolving the dependencies? Also keep in mind that for certain packages, you need their -devel packages as well.

---

### Post by vindzhov on 2008-12-12
edit:
Sorry, I've made a mistake. I have no solution.
/edit;


Solution here:
[http://ubuntuforums.org/showpost.php?p=6349258&postcount=2](http://ubuntuforums.org/showpost.php?p=6349258&postcount=2)

 :)

---

