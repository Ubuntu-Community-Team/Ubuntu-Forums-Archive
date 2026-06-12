---
title: "latest intel driver install errors"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by duruttye on 2009-08-21
Hey there.

I have a fresh install of Ubuntu 9.04 on  dell vostro laptop (3 GB ram, 2.0 Ghz processor, and the naughty intel 965 graphics card). I installed xubuntu-desktop package, because I thought using xfce will help the performance, but I was wrong...

So, I wanted to do something to this poor graphics and after a few days of googleing I fond out the there is a new driver for my graphics card.

Here it is:
[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

Downloaded, extracted, cd-ed into the folder, and after doing ./configure I get these errors:

```
checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```


So, is there anybody out there who can walk me through this?

---

### Post by eldragon on 2009-08-21
the only reason your hadrware cant play nice with compiz is because its been blacklisted by ubuntu devs due to some issues with video playback (my guess). if you are still willing to live with it. search the forums, or google it yourself how to enable compiz on a 965. its not that hard.

if you still need to build the source code. read its readme for further instructions.

---

### Post by 3rdalbum on 2009-08-21
Is this your first time compiling software from source?

You will need the development libraries for Xorg - they are in the "xserver-xorg-dev" package. It looks like you might need "x11proto-core-dev". You may also need your Linux headers package (linux-headers-generic if you are on the latest Ubuntu-delivered kernel).

Then run the configure script again. If it complains about any other missing packages, install them, but remember they usually need to have "-dev" at the end of the name.

Fiddling with your Intel drivers might end in tears and leave you with an unrecoverable system. If not, it could leave you with lower performance. At this stage of the driver rewriting process, speeds are similar or worse, according to Phoronix. If you're willing to take the risk, then good luck.

---

### Post by duruttye on 2009-08-21
So, it doesn't look pretty, either way.

Than I think I will leave the compiling, and try to undo that blacklisting of my driver.
I don't care much about compiz or, any effects whatsoever, but even scrolling down a page in firefox makes me dizzy, and the cpu is at all times around 50% thanks to the Xorg. This is my main problem.
Question: taking care of the blacklist problem solves these things too? or will it take the load off the cpu, at least?

Thank you both for your answers!

---

### Post by marcurius on 2009-11-04
> **3rdalbum said:**
> Is this your first time compiling software from source?

You will need the development libraries for Xorg - they are in the "xserver-xorg-dev" package. It looks like you might need "x11proto-core-dev".

Thank you very much for this info!

---

