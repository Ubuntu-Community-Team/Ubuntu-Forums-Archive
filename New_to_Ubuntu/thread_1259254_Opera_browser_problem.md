---
title: "Opera browser problem"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by nns2006 on 2009-09-06
Hi,
I have installed Opera 10 recently through Terminal. But when i am trying to run it browser is not opening? When i tried to open it from terminal i got this output..


nityanand@nityanand-laptop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/nityanand/lib/opera/10.00/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

how to solve this problem?

---

### Post by Colonel Kilkenny on 2009-09-06
> **nns2006 said:**
> Hi,
I have installed Opera 10 recently through Terminal. But when i am trying to run it browser is not opening? When i tried to open it from terminal i got this output..


nityanand@nityanand-laptop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/nityanand/lib/opera/10.00/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

how to solve this problem?

You didn't give information about your system. Jaunty? 64bit?
Without any more info I'd say go to [ftp://ftp.opera.com/pub/opera/linux/1000/final/en/](ftp://ftp.opera.com/pub/opera/linux/1000/final/en/) and try different packages there. The problem is the last error message about libqt-mt. First two messages you can ignore, it's just Opera warning that it cannot find necessary files for Java to work.

---

### Post by ibutho on 2009-09-06
Do you have libqt3-mt installed?

---

### Post by nns2006 on 2009-09-06
> **ibutho said:**
> Do you have libqt3-mt installed?

nityanand@nityanand-laptop:~$ locate libqt3-mt
/usr/share/doc/libqt3-mt
/usr/share/doc/libqt3-mt/PLATFORMS
/usr/share/doc/libqt3-mt/README
/usr/share/doc/libqt3-mt/README-QT.TXT
/usr/share/doc/libqt3-mt/README.Debian.gz
/usr/share/doc/libqt3-mt/README.immodule
/usr/share/doc/libqt3-mt/changelog.Debian.gz
/usr/share/doc/libqt3-mt/changelog.gz
/usr/share/doc/libqt3-mt/copyright
/var/lib/dpkg/info/libqt3-mt.conffiles
/var/lib/dpkg/info/libqt3-mt.list
/var/lib/dpkg/info/libqt3-mt.md5sums
/var/lib/dpkg/info/libqt3-mt.postinst
/var/lib/dpkg/info/libqt3-mt.postrm
/var/lib/dpkg/info/libqt3-mt.shlibs

---

### Post by nns2006 on 2009-09-06
> **Colonel Kilkenny said:**
> You didn't give information about your system. Jaunty? 64bit?
Without any more info I'd say go to [ftp://ftp.opera.com/pub/opera/linux/1000/final/en/](ftp://ftp.opera.com/pub/opera/linux/1000/final/en/) and try different packages there. The problem is the last error message about libqt-mt. First two messages you can ignore, it's just Opera warning that it cannot find necessary files for Java to work.

It is jaunty 9.04 with 64 bits.

---

### Post by 3rdalbum on 2009-09-06
The Debian package on the Opera website should pull in all dependencies for you.

---

### Post by nns2006 on 2009-09-06
> **3rdalbum said:**
> The Debian package on the Opera website should pull in all dependencies for you.

I have installed opera_10.00.4585.gcc4,qt3_amd64.deb from opera website.Which I am again doing just for sure.

---

### Post by FreewheelinFrank on 2009-09-06
Add the Opera repository and key- you'll always be up to date that way (Opera 10.10 with lots of bug fixes will be here almost as soon as you've installed 10.)

[http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/](http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/)

[http://fileforum.betanews.com/detail/Opera-for-Windows/945720329/1](http://fileforum.betanews.com/detail/Opera-for-Windows/945720329/1)

---

### Post by ibutho on 2009-09-06
> **nns2006 said:**
> nityanand@nityanand-laptop:~$ locate libqt3-mt
/usr/share/doc/libqt3-mt
/usr/share/doc/libqt3-mt/PLATFORMS
/usr/share/doc/libqt3-mt/README
/usr/share/doc/libqt3-mt/README-QT.TXT
/usr/share/doc/libqt3-mt/README.Debian.gz
/usr/share/doc/libqt3-mt/README.immodule
/usr/share/doc/libqt3-mt/changelog.Debian.gz
/usr/share/doc/libqt3-mt/changelog.gz
/usr/share/doc/libqt3-mt/copyright
/var/lib/dpkg/info/libqt3-mt.conffiles
/var/lib/dpkg/info/libqt3-mt.list
/var/lib/dpkg/info/libqt3-mt.md5sums
/var/lib/dpkg/info/libqt3-mt.postinst
/var/lib/dpkg/info/libqt3-mt.postrm
/var/lib/dpkg/info/libqt3-mt.shlibs
That does not show for sure if its installed. Run
```
dpkg -s libqt3-mt
```
Post back the output.

---

### Post by nns2006 on 2009-09-06
> **ibutho said:**
> That does not show for sure if its installed. Run
```
dpkg -s libqt3-mt
```
Post back the output.

nityanand@nityanand-laptop:~$ dpkg -s libqt3-mt
Package: libqt3-mt
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 9476
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: qt-x11-free
Version: 3:3.3.8-b-5ubuntu1
Replaces: libqt3, libqt3-helper, libqt3c102-mt, qt3-tools (<< 2:3.0.2-20020306-1)
Depends: fontconfig, libaudio2, libc6 (>= 2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1, libice6 (>= 1:1.0.0), libjpeg62, libmng1 (>= 1.0.3-1), libpng12-0 (>= 1.2.13-4), libsm6, libstdc++6 (>= 4.1.1-21), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1, libxt6, zlib1g (>= 1:1.2.3.3.dfsg-1)
Recommends: libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libxmu6 (>= 4.3.0.dfsg.1-4)
Suggests: libqt3-mt-mysql, libqt3-mt-odbc, libqt3-mt-psql
Conflicts: libqt3c-mt, libqt3c102-mt, libqui1-emb
Conffiles:
 /etc/qt3/qtrc 734055fdfcf1f375f712f06fa6c3c84a
 /etc/qt3/qt_plugins_3.3rc 1ac11d57643ecbf84a3f3cbf1a6818f1
Description: Qt GUI Library (Threaded runtime version), Version 3
 This is the Trolltech Qt library, version 3. It's necessary for
 applications that link against the libqt-mt.so.3, e.g. all KDE3
 applications.
Homepage: [http://trolltech.com](http://trolltech.com)
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
nityanand@nityanand-laptop:~$

---

### Post by nns2006 on 2009-09-06
I reinstalled the opera_10.00.4585.gcc4,qt3_amd64.deb package and it works for me now. 
Thanks for helping me you guys

---

