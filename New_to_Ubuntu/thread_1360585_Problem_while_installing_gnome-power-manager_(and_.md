---
title: "Problem while installing gnome-power-manager (and many more!) manually"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by bharaths_jois on 2009-12-21
Hi guys,

I am presently trying to install gnome-power-monitor on my system. I run the ./configure, but it ends because a few dependencies were not found. I am pretty sure that the dependencies are satisfied and guessing something wrong with the PKG_CONFIG_PATH. I have faced this for almost every package I have tried to install. I give up hope of installing it manually, and go with the synaptic instead, and it works smoothly here! This time, I was in no mood for that. So... 

here is a part of the config.log and let me know if some more info is needed on this:

-----------------------------------------------------------------------

configure:14702: checking for DBUS
configure:14712: $PKG_CONFIG --exists --print-errors "
 dbus-glib-1 >= $DBUS_GLIB_REQUIRED
 dbus-1 >= $DBUS_REQUIRED
 gthread-2.0"
Package dbus-glib-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-glib-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-glib-1' found
configure:14718: $? = 1
configure:14737: $PKG_CONFIG --exists --print-errors "
 dbus-glib-1 >= $DBUS_GLIB_REQUIRED
 dbus-1 >= $DBUS_REQUIRED
 gthread-2.0"
Package dbus-glib-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-glib-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-glib-1' found
configure:14743: $? = 1
No package 'dbus-glib-1' found
configure:14792: error: Package requirements (
 dbus-glib-1 >= 0.70
 dbus-1 >= 1.0
 gthread-2.0) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
-----------------------------------------------------------------------

Warm regards,
Bharath

---

### Post by bharaths_jois on 2009-12-21
And yes, it would be good if one could provide me pointers to how the configure works for my read. I went through the ubuntupocketguide but it mentions that this topic is out of scope. 

Warm regards,
Bharath

---

### Post by 3rdalbum on 2009-12-21
> **bharaths_jois said:**
> 

No package 'dbus-glib-1' found

Is the libdbus-glib-1-dev package installed?

When you're compiling, you need the "-dev" package (development headers), not just the regular runtime package.

---

### Post by bharaths_jois on 2009-12-21
That is a good learning, which I will take along... Thank you. I presently dont have the -dev package. I could mark this half solved.

If anybody could address - [http://ubuntuforums.org/showpost.php?p=8535265&postcount=2](http://ubuntuforums.org/showpost.php?p=8535265&postcount=2)

Thank you again

---

