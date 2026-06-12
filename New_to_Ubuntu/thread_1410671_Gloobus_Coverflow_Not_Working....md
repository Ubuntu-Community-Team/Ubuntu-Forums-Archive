---
title: "Gloobus Coverflow Not Working..."
date: 2010-02-19
forum: New to Ubuntu
---

### Post by dirtlamb5 on 2010-02-19
Hey, I've been using Gloobus Preview for a while now and it's really useful. Recently (maybe even today) they released a new part of their project, which allows for a cover-flow effect to view files in Nautilus. Anyway, I followed the instructions I found at _[http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html](http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html)_, and everything was working until I attempted to run ```
./autogen.sh --prefix=/usr
```Here's where it started to go wrong...(this isn't the entire output, just where the error began)
```
checking for ALL... configure: error: Package requirements (
    glib-2.0        >= 2.21.3
    gnome-desktop-2.0    >= 2.25.5
    gthread-2.0
    gio-unix-2.0
    gio-2.0
    pango            >= 1.1.2
    gtk+-2.0        >= 2.16.0
    libxml-2.0        >= 2.4.7
    gail            >= 0.16
    unique-1.0
    dbus-glib-1
) were not met:

No package 'gnome-desktop-2.0' found
No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```I dunno if anybody else has attempted to install this yet, but does anybody have any ideas as to fix this?

---

### Post by stlsaint on 2010-02-19
are you able to install those packages individually?

---

### Post by dirtlamb5 on 2010-02-22
[LEFT]Hm well I waited a couple days and tried everything from the beginning and for some reason it worked this time. I didn't attempt to install any of those packages, though, so I'm not really sure what happened. 
[/LEFT]

---

