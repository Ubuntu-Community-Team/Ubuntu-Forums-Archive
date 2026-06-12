---
title: "Issues installing THC Hydra"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Sensayshun on 2010-02-04
I've worked through alot of the issues but I'm not sure what this message is telling me. Hope someone could give me a shove in the right direction.

> sens@Safe:~/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk$ make
make  all-recursive
make[1]: Entering directory `/home/sens/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk'
Making all in src
make[2]: Entering directory `/home/sens/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" 	-DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" 	-D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c callbacks.c
callbacks.c: In function &#8216;popen_re_unbuffered&#8217;:
callbacks.c:532: warning: format not a string literal and no format arguments
callbacks.c: In function &#8216;on_btnSave_clicked&#8217;:
callbacks.c:668: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
In file included from /usr/include/fcntl.h:217,
                 from callbacks.c:27:
In function &#8216;open&#8217;,
    inlined from &#8216;on_btnSave_clicked&#8217; at callbacks.c:666:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
In file included from /usr/include/stdio.h:910,
                 from /usr/include/pango-1.0/pango/pango-utils.h:25,
                 from /usr/include/pango-1.0/pango/pango.h:46,
                 from /usr/include/gtk-2.0/gdk/gdktypes.h:37,
                 from /usr/include/gtk-2.0/gdk/gdkscreen.h:32,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:31,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from callbacks.c:11:
In function &#8216;snprintf&#8217;,
    inlined from &#8216;hydra_get_options&#8217; at callbacks.c:247:
/usr/include/bits/stdio2.h:65: warning: call to __builtin___snprintf_chk will always overflow destination buffer
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/sens/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sens/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk'
make: *** [all-recursive-am] Error 2
sens@Safe:~/Cracking/THC Hydra/hydra-5.4-src/hydra-gtk$ 


Thanks for any help.

---

