---
title: "Error upon compiling VLC for Ubuntu 9.04."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-13
Upon compiling VLC media player from source for Ubuntu 9.04, I got the following error with make:

>  ...
make[6]: Entering directory `/home/jobin/software/vlc-0.9.9a/modules/access/screen'
/bin/bash ../../../libtool --tag=CXX   --mode=link g++ `top_builddir="../../.." ../../../vlc-config --cxxflags plugin libscreen_plugin.la`  -rpath '/usr/local/lib/vlc/access' -avoid-version -module -no-undefined -export-symbol-regex ^vlc_entry -shrext .so `top_builddir="../../.." ../../../vlc-config --ldflags plugin libscreen_plugin.la`  -o libscreen_plugin.la  libscreen_plugin_la-screen.lo libscreen_plugin_la-x11.lo   `top_builddir="../../.." ../../../vlc-config -libs plugin libscreen_plugin.la` ../../../src/libvlccore.la 
libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[6]: *** [libscreen_plugin.la] Error 1
make[6]: Leaving directory `/home/jobin/software/vlc-0.9.9a/modules/access/screen'
make[5]: *** [all] Error 2

When I ran configure, I had to download packages one by one. Any way to find and download all the dependencies at once? And how to solve this VLC make error?

---

### Post by Partyboi2 on 2009-06-13
Hi, you can pull in the dev packages for vlc with
```
sudo apt-get build-dep vlc
```Is there any reason why you don't want to install the vlc that is in the Ubuntu repos?

---

### Post by nandemonai on 2009-06-13
Or even the newer version available here? 

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

