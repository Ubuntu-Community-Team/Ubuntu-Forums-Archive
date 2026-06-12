---
title: "integrating gstreamer or qt-gstreamer with qt creator"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by sdsayantan on 2011-02-22
hey , i want to integrate gstreamer with Qt Creator ....so i tried to install gstreamer manully but there is some error

Making install in common
make[1]: Entering directory `/home/sayantan/src/gstreamer-0.10.32/common'
Making install in m4
make[2]: Entering directory `/home/sayantan/src/gstreamer-0.10.32/common/m4'
make[3]: Entering directory `/home/sayantan/src/gstreamer-0.10.32/common/m4'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32/common/m4'
make[2]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32/common/m4'
make[2]: Entering directory `/home/sayantan/src/gstreamer-0.10.32/common'
make[3]: Entering directory `/home/sayantan/src/gstreamer-0.10.32/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32/common'
make[2]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32/common'
make[1]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32/common'
make[1]: Entering directory `/home/sayantan/src/gstreamer-0.10.32'
make[2]: Entering directory `/home/sayantan/src/gstreamer-0.10.32'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/aclocal" || /bin/mkdir -p "/usr/local/share/aclocal"
 /usr/bin/install -c -m 644 gst-element-check-0.10.m4 '/usr/local/share/aclocal'
make[2]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32'
make[1]: Leaving directory `/home/sayantan/src/gstreamer-0.10.32'

so how will i able to fix it???
and how will put gstreamer.pc in pkg_configur_path, so that i can acess it from qt creator

---

