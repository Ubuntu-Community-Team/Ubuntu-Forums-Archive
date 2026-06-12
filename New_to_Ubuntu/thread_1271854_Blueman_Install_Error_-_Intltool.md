---
title: "Blueman Install Error - Intltool"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by haze90 on 2009-09-21
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
./configure: line 12873: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.


Any help? :)

---

### Post by haze90 on 2009-09-21
Problem solved. Nevermind. :D

---

### Post by haze90 on 2009-09-21
Okay new problem:

> checking for python module dbus... yes
checking for python module gobject... yes
checking for BLUEZ... configure: error: Package requirements (bluez    >= 4.21
        libstartup-notification-1.0 >= 0.9
        gdk-2.0 >= 2.12
        pygobject-2.0 >= 2.12
        gobject-2.0 >= 2.12
        glib-2.0 >= 2.16
        gthread-2.0 >= 2.16
) were not met:

No package 'bluez' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BLUEZ_CFLAGS
and BLUEZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
But I have bluez installed, as well as all the other packages listed and I made sure they were up to date.

---

