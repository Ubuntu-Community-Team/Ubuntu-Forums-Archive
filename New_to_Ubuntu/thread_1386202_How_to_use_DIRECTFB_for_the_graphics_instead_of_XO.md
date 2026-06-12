---
title: "How to use DIRECTFB for the graphics instead of XORG ?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-20
How to use DIRECTFB for the graphics instead of XORG ?

here a [screenshot]("http://omploader.org/vMnQ4bw"). It is one of the moderator of this forum that does such things. It has particularly advantages, for poor hardware. 
[http://omploader.org/vMnQ4bw](http://omploader.org/vMnQ4bw)

Directfb is in the repos, but how can it be configured? 

```
# apt-cache search libdirectfb
libdirectfb-1.2-0-dbg - direct frame buffer graphics - shared libraries debug symbols
libdirectfb-1.2-0 - direct frame buffer graphics - shared libraries
libdirectfb-bin-dbg - direct frame buffer graphics - binaries debug symbols
libdirectfb-bin - direct frame buffer graphics - binaries
libdirectfb-dev - direct frame buffer graphics library - development files
libdirectfb-extra-dbg - direct frame buffer graphics - extra provider debug symbols
libdirectfb-extra - direct frame buffer graphics - extra providers
libggi-target-fbdev - General Graphics Interface direct access framebuffer target
splashy - A complete user-space boot splash system
```


Here is a screenshot running : [http://www.directfb.org/screenshots/DirectFB_3D_Windows3.png](http://www.directfb.org/screenshots/DirectFB_3D_Windows3.png)

---

### Post by frenchn00b on 2010-01-20
you need the libdirectfb-bin in the repos.

OK, I made a deb of linux-fusion:
[http://depositfiles.com/files/pmjgy36wg](http://depositfiles.com/files/pmjgy36wg)
```
# md5sum linux-fusion_8.1.1-1_i386.deb
b19677d29bf643f0242d4297391a1266  linux-fusion_8.1.1-1_i386.deb
```


here is the howto
[http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/](http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/)

still compiling ... [COLOR="Red"]EDIT: DONE [/COLOR]
Here is the DEB for Ubuntu:

> [COLOR="Red"]# md5sum directfb_1.2.8-1_i386.deb
6dc464107d3b622c160b0ed74fa1a874  directfb_1.2.8-1_i386.deb[/COLOR]
[http://depositfiles.com/files/uphu3m095](http://depositfiles.com/files/uphu3m095)

Enjoy!! [COLOR="Red"]So guys, is this fast DIRECTFB (instead of XORG) working? 
Is it impressive for you this directfb? [/COLOR]


tslib
> md5sum lite_0.8.10-1_i386.deb 
343e4ca8e0065d0d294bbc361b9b82b9  lite_0.8.10-1_i386.deb
[http://depositfiles.com/files/xvf9yek66](http://depositfiles.com/files/xvf9yek66)

---

### Post by frenchn00b on 2010-01-20
Also :

dont forget to do : 

```
modprobe fusion
```

---

### Post by frenchn00b on 2010-01-20
here it is ! tada!

wow. it is very very fast!! it is very fluid. 
here I just made a [quick screenshot]("http://img683.imageshack.us/img683/9576/directfbfrenchn00b.jpg") of directfb

directfb example:[http://depositfiles.com/files/gs6jq5y06](http://depositfiles.com/files/gs6jq5y06)

---

