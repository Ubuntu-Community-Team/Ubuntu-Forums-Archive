---
title: "problem in installing ATI Radeon HD  3450 Driver"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by konsolelover on 2011-07-06
Hello, 
i just tried to install ati-driver-installer-11-6-x86.x86_64.run(which i download from AMD's official site) file by double clicking it and by selecting run in terminal....then it started executing and as usual asked for password ...i entered the password...then the last thing what i could see was 
Detected Architecture:
i686 32 bit
X Server: 6.9 or later
and then i saw something like removing...........(i couldn't read with that speed)
and it got terminated......
tried to start over and got the same result.....
I'm using Ubuntu 11.04 32 bit on my HP laptop with AMD Turion 2.0 ghz 64 bit  processor.

---

### Post by jtarin on 2011-07-06
Change to the directory the .run file is in using the terminal. Then execute the command ```
./ati-driver-installer-11-6-x86.x86_64.run
```and see if you get something you can read.

---

### Post by konsolelover on 2011-07-06
i did and now i can see a message...

See /usr/share/ati/fglrx-install.log for installation details.
Removing temporary directory: fglrx-install.A1bKCy

i checked the directory but there is no folder of ati in /usr/share..........

---

### Post by jtarin on 2011-07-06
Issue the command ```
cat /usr/share/ati/fglrx-install.log
``` and see if anything shows.

---

### Post by jtarin on 2011-07-06
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html)

---

### Post by konsolelover on 2011-07-06
cat: /usr/share/ati/fglrx-install.log: No such file or directory

---

### Post by jtarin on 2011-07-06
> **konsolelover said:**
> cat: /usr/share/ati/fglrx-install.log: No such file or directoryThen it probably didn't install. Follow the link I gave in the post above.

---

### Post by konsolelover on 2011-07-06
i followed the post and got the error which i couldn't understand.....some part of message was,

dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XOpenDisplay used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetGeometry used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XSetErrorHandler used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XMaxRequestSize used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCreateGC used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeFontInfo used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XEHeadOfExtensionList used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: couldn't find library libQtCore.so.4 needed by debian/xorg-driver-fglrx/usr/share/ati/lib/libQtGui.so.4 (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: dependency on libXcursor.so.1 could be avoided if "debian/xorg-driver-fglrx/usr/sbin/amdnotifyui" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libXxf86vm.so.1 could be avoided if "debian/xorg-driver-fglrx/usr/sbin/amdnotifyui" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: error: Cannot continue due to the error above.
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/xorg-driver-fglrx.substvars debian/xorg-driver-fglrx/usr/bin/atiode debian/xorg-driver-fglrx/usr/bin/fglrxinfo debian/xorg-driver-fglrx/usr/bin/fgl_glxgears debian/xorg-driver-fglrx/usr/bin/atiodcli debian/xorg-driver-fglrx/usr/bin/aticonfig debian/xorg-driver-fglrx/usr/lib/xorg/modules/glesx.so debian/xorg-driver-fglrx/usr/lib/xorg/modules/drivers/fglrx_drv.so debian/xorg-driver-fglrx/usr/lib/xorg/modules/amdxmm.so debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so debian/xorg-driver-fglrx/usr/lib/xorg/modules/extensions/libglx.so debian/xorg-driver-fglrx/usr/lib/libatiadlxx.so debian/xorg-driver-fglrx/usr/lib/libaticalcl.so debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 debian/xorg-driver-fglrx/usr/lib/libatiuki.so.1.0 debian/xorg-driver-fglrx/usr/lib/libaticaldd.so debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 debian/xorg-driver-fglrx/usr/lib/libaticalrt.so debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so debian/xorg-driver-fglrx/usr/share/ati/lib/libQtGui.so.4 debian/xorg-driver-fglrx/usr/share/ati/lib/libQtCore.so.4 debian/xorg-driver-fglrx/usr/sbin/amdnotifyui debian/xorg-driver-fglrx/usr/sbin/atieventsd returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 9
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.OXviac

---

### Post by konsolelover on 2011-07-06
finally installed with 
sudo sh ./ati....run command

---

### Post by jtarin on 2011-07-06
Bravo!! mark as solved.:p

---

