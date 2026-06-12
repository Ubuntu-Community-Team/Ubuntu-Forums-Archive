---
title: "Help required in installing panflute"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by kratos_prakhar on 2010-08-05
Hey Everyone

I just downloaded(tar.gz) panflute  music applet to install on my ubuntu 10.04. I read the README but it has no installation instructions. I searched this forum for some other posts regarding the same and tried to do exactly as it was mentioned but it was to no avail.

After typing ./configure this is what i get: 
[FONT="Courier New"]
checking pkg-config is at least version 0.9.0... yes
checking for DBUS... configure: error: Package requirements (dbus-python >= 0.80) were not met:

Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
Package 'dbus-1', required by 'dbus-python', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/FONT]

Any help in installing this would be greatly appreciated. This happens to be my first attempt at installing an application by compiling it. I really want to learn how to do us.
Thanks

---

### Post by themusicalduck on 2010-08-05
I'm not sure how to fix your compiling problem, but you can install Panflute by adding the Panflute repository.

Use these commands to install it:

```
sudo add-apt-repository ppa:kuliniew/ppa
sudo apt-get update
sudo apt-get install panflute-applet

```

---

