---
title: "Installing xorg-server 1.5.3 (XLIB/X11 problem)"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by ClaytonOT on 2009-03-01
I'm trying to install xorg-server because my intel drivers have a dependency with it. During my ./configure of the xorg-server-1.5.3 I run into this problem.

> checking for XLIB... configure: error: Package requirements (x11) were not met:

No package 'x11' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XLIB_CFLAGS
and XLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I've only been using Linux for about a week now so I'm still noob. Looking through both my /etc and /usr folders there's an X11 directory. I've checked synpatic and everything on their that includes X11 is already installed on this computer. The gibberish at the bottom is just that to me, gibberish. I saw something about that before I passed out last night, but not remember where. So looking for some help to get this installed, thanks!

---

