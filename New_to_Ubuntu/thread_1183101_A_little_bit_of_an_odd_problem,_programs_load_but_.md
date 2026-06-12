---
title: "A little bit of an odd problem, programs load but crash immediately"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by GermanMafia on 2009-06-09
Okay, I'm setting up an Ubuntu box for my nephew (almost 3, it's time!). I have Edubuntu installed, and whenever I try to run it from Applications>Education>Educational Suite Gcompris, I can see it loading at the bottom, but then it just exits. XBMC does nearly the same thing as well, except it opens a terminal windows and quickly exits. Any ideas?

Ah I should probably give some more information.

Running Ubuntu 9.04, Edu 9.04, I restarted and it said 'XFCE script not installed, would you like to make this your default?' (The edubuntu logo was present at login).

---

### Post by glennric on 2009-06-09
Try running "gcompris" from a terminal and see what errors are reported in the terminal.

---

### Post by GermanMafia on 2009-06-11
Alright, here is what is spat out when gcompris is run in terminal.


exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:14691): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
/usr/share/themes/EdubuntuColors/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Infos:
   Config dir '/home/diego/.config/gcompris'
   Users dir '/home/diego/My GCompris'
   Database '/home/diego/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted


I tried to reinstall it and that didn't work, and the administrative edubuntu doesn't run either.

---

