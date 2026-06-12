---
title: "install folder with terminal"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by hollowtd on 2009-02-22
This may sound stupid but here it is: I have a folder called rendering downloaded to my desktop. I have extracted the "box" onto by desktop. I now would like to install this "rendering" using terminal. (It's for cairo dock 3d). I just can't figure out how to do it. I am new to this obviously. I've tried the sudo dpkg (etc) command but that doesn't help. Can someone tell me what to do real quick? Cheers in advance.

---

### Post by spiderbatdad on 2009-02-22
It sounds like what you have is a source package. They are not all the same. Does yours end in tar.gz or other tar? There should be a Readme file inside the extracted folder. See here for more: [http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)
If the package is a .deb, simply click on the package. No need to extract it nor run dpkg.

---

### Post by hollowtd on 2009-02-22
It's a zip file. Then, I right clicked and extracted onto my desktop. I'll check out the link you've sent me. I've looked all over. I've not got the package and the extracted file folder called "rendering" on my desktop. I just want to install that but don't know how.

---

### Post by handydan918 on 2009-02-22
Perhaps if you give us the name of this "folder". I imagine you have an application to install and don't know how to do it?

---

### Post by hollowtd on 2009-02-22
Yeah, I just don't know how to install it. The package name is rendering.zip. I extracted it to my desktop and now there is a folder called "rendering".

---

### Post by maybeway36 on 2009-02-22
What is in the folder? That should help a lot.

---

### Post by hollowtd on 2009-02-22
It's for Cairo dock. I am trying to ad some 3d effects so I downloaded this box. I then extracted it to my desktop. The box is called rendering.zip. The extracted folder is called "rendering". They are both sitting on my desktop.

---

### Post by hollowtd on 2009-02-22
I typed sudo make install and got this from the rendering directory in terminal:
terry@terry-laptop:~$ cd ~/Desktop
terry@terry-laptop:~/Desktop$ cd rendering
terry@terry-laptop:~/Desktop/rendering$ sudo make install
[sudo] password for terry: 
Making install in .
make[1]: Entering directory `/home/terry/Desktop/rendering'
make[2]: Entering directory `/home/terry/Desktop/rendering'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/terry/Desktop/rendering'
make[1]: Leaving directory `/home/terry/Desktop/rendering'
Making install in src
make[1]: Entering directory `/home/terry/Desktop/rendering/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -I../src -pthread -I/usr/local/include/cairo-dock -I/usr/local/include/cairo-dock/cairo-dock -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/librsvg-2 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include     -DMY_APPLET_SHARE_DATA_DIR=\""/usr/local/share/cairo-dock/plug-in/rendering"\" -DMY_APPLET_README_FILE=\""readme"\" -DMY_APPLET_VERSION=\""1.2.0"\" -DMY_APPLET_GETTEXT_DOMAIN=\""cd-dustbin"\" -DMY_APPLET_DOCK_VERSION=\""`pkg-config --modversion cairo-dock`"\" -DMY_APPLET_PREVIEW_FILE=\""none"\" -DMY_APPLET_CONF_FILE=\""rendering.conf"\" -DMY_APPLET_USER_DATA_DIR=\""rendering"\" -DMY_APPLET_ICON_FILE=\""icon.png"\" -std=c99 -Werror-implicit-function-declaration -O3 -g -O2 -MT libcd_rendering_la-rendering-init.lo -MD -MP -MF ".deps/libcd_rendering_la-rendering-init.Tpo" -c -o libcd_rendering_la-rendering-init.lo `test -f 'rendering-init.c' || echo './'`rendering-init.c; \
	then mv -f ".deps/libcd_rendering_la-rendering-init.Tpo" ".deps/libcd_rendering_la-rendering-init.Plo"; else rm -f ".deps/libcd_rendering_la-rendering-init.Tpo"; exit 1; fi
Package cairo-dock was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo-dock.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo-dock' found
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../src -pthread -I/usr/local/include/cairo-dock -I/usr/local/include/cairo-dock/cairo-dock -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/librsvg-2 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -DMY_APPLET_SHARE_DATA_DIR=\"/usr/local/share/cairo-dock/plug-in/rendering\" -DMY_APPLET_README_FILE=\"readme\" -DMY_APPLET_VERSION=\"1.2.0\" -DMY_APPLET_GETTEXT_DOMAIN=\"cd-dustbin\" -DMY_APPLET_DOCK_VERSION=\"\" -DMY_APPLET_PREVIEW_FILE=\"none\" -DMY_APPLET_CONF_FILE=\"rendering.conf\" -DMY_APPLET_USER_DATA_DIR=\"rendering\" -DMY_APPLET_ICON_FILE=\"icon.png\" -std=c99 -Werror-implicit-function-declaration -O3 -g -O2 -MT libcd_rendering_la-rendering-init.lo -MD -MP -MF .deps/libcd_rendering_la-rendering-init.Tpo -c rendering-init.c  -fPIC -DPIC -o .libs/libcd_rendering_la-rendering-init.o
In file included from rendering-init.c:11:
rendering-config.h:6:18: error: glib.h: No such file or directory
In file included from rendering-init.c:11:
rendering-config.h:9: error: expected ')' before '*' token
In file included from rendering-init.c:12:
rendering-caroussel.h:5:24: error: cairo-dock.h: No such file or directory
In file included from rendering-init.c:12:
rendering-caroussel.h:13: error: expected ')' before '*' token
rendering-caroussel.h:16: error: expected ')' before '*' token
rendering-caroussel.h:18: error: expected ')' before '*' token
rendering-caroussel.h:20: error: expected ')' before '*' token
rendering-caroussel.h:22: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
In file included from rendering-init.c:13:
rendering-parabole.h:10: error: expected ')' before '*' token
rendering-parabole.h:16: error: expected ')' before '*' token
rendering-parabole.h:19: error: expected ')' before '*' token
rendering-parabole.h:21: error: expected ')' before '*' token
rendering-parabole.h:23: error: expected ')' before '*' token
rendering-parabole.h:25: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
In file included from rendering-init.c:14:
rendering-3D-plane.h:10: error: expected ')' before '*' token
rendering-3D-plane.h:12: error: expected ')' before '*' token
rendering-3D-plane.h:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
rendering-3D-plane.h:17: error: expected ')' before '*' token
rendering-3D-plane.h:20: error: expected ')' before '*' token
rendering-3D-plane.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
In file included from rendering-init.c:15:
rendering-rainbow.h:10: error: expected ')' before '*' token
rendering-rainbow.h:12: error: expected ')' before '*' token
rendering-rainbow.h:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
rendering-rainbow.h:17: error: expected ')' before '*' token
rendering-rainbow.h:20: error: expected ')' before '*' token
rendering-rainbow.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
rendering-init.c:21: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'double'
rendering-init.c:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
rendering-init.c:28: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'my_bRotateIconsOnEllipse'
rendering-init.c:34: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'my_bDrawTextWhileUnfolding'
rendering-init.c:40: error: 'G_PI' undeclared here (not in a function)
rendering-init.c:43: error: expected declaration specifiers or '...' before string constant
rendering-init.c:43: error: expected declaration specifiers or '...' before numeric constant
rendering-init.c:43: error: expected declaration specifiers or '...' before numeric constant
rendering-init.c:43: error: expected declaration specifiers or '...' before numeric constant
rendering-init.c:43: error: expected declaration specifiers or '...' before 'CAIRO_DOCK_CATEGORY_DESKTOP'
rendering-init.c:46: warning: return type defaults to 'int'
rendering-init.c: In function 'CD_APPLET_DEFINITION':
rendering-init.c:46: error: expected ')' before 'bFlatSeparator'
rendering-init.c:62: error: expected ')' before '*' token
rendering-init.c:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before '{' token
rendering-init.c:98: error: expected declaration specifiers before 'gboolean'
rendering-init.c:112: error: expected '{' at end of input
make[1]: *** [libcd_rendering_la-rendering-init.lo] Error 1
make[1]: Leaving directory `/home/terry/Desktop/rendering/src'
make: *** [install-recursive] Error 1
terry@terry-laptop:~/Desktop/rendering$ cd
terry@terry-laptop:~$ cd
terry@terry-laptop:~$

---

### Post by spiderbatdad on 2009-02-22
zip files often contain a filename.sh which you can run anytime you like with the command```
cd foldername
chmod +x filename.sh
./filename.sh
```or you can make a folder called bin in your home directory and run it.

---

### Post by hollowtd on 2009-02-22
It says no such file or directory. I think it's just an applet or something to make cairo dock 3d. I really don't know if I'm using the right terminology but I'm trying. I downloaded it and it's a zip file. I just want to "install" it I suppose.

---

### Post by spiderbatdad on 2009-02-22
please copy/paste this terminal session:
```
cd Desktop/rendering
ls -l
```

---

### Post by hollowtd on 2009-02-22
I just can't get that to work. Who knows if I'm running it right. Here's what I typedterry@terry-laptop:~/Desktop/rendering$ chmod +x rendering.sh
chmod: cannot access `rendering.sh': No such file or directory
terry@terry-laptop:~/Desktop/rendering$ ./rendering.sh
bash: ./rendering.sh: No such file or directory
terry@terry-laptop:~/Desktop/rendering$

---

### Post by hollowtd on 2009-02-22
terry@terry-laptop:~$ cd Desktop/rendering
terry@terry-laptop:~/Desktop/rendering$ ls -l
total 1616
-rw-r--r-- 1 terry terry 294754 2008-03-29 10:22 aclocal.m4
drwxr-xr-x 2 terry terry   4096 2008-03-29 10:22 autom4te.cache
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 compile -> /usr/share/automake-1.9/compile
lrwxrwxrwx 1 terry terry     36 2009-02-19 17:40 config.guess -> /usr/share/automake-1.9/config.guess
-rw-r--r-- 1 terry terry   2504 2008-03-29 10:22 config.h
-rw-r--r-- 1 terry terry   2234 2008-03-29 10:22 config.h.in
-rw-r--r-- 1 terry terry  36798 2008-03-29 10:22 config.log
-rwxr-xr-x 1 terry terry  39276 2008-03-29 10:22 config.status
lrwxrwxrwx 1 terry terry     34 2009-02-19 17:40 config.sub -> /usr/share/automake-1.9/config.sub
-rwxr-xr-x 1 terry terry 781725 2008-03-29 10:22 configure
-rwx------ 1 terry terry   1188 2008-03-18 04:33 configure.ac
drwx------ 3 terry terry   4096 2008-03-29 10:22 data
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 depcomp -> /usr/share/automake-1.9/depcomp
lrwxrwxrwx 1 terry terry     34 2009-02-19 17:40 install-sh -> /usr/share/automake-1.9/install-sh
-rwxr-xr-x 1 terry terry  22491 2008-03-29 10:22 intltool-extract
-rwx------ 1 terry terry  22493 2008-03-18 04:33 intltool-extract.in
-rwxr-xr-x 1 terry terry  35214 2008-03-29 10:22 intltool-merge
-rwx------ 1 terry terry  35219 2008-03-18 04:33 intltool-merge.in
-rwxr-xr-x 1 terry terry  28116 2008-03-29 10:22 intltool-update
-rwx------ 1 terry terry  28061 2008-03-18 04:33 intltool-update.in
-rwxr-xr-x 1 terry terry 219129 2008-03-29 10:22 libtool
lrwxrwxrwx 1 terry terry     28 2009-02-19 17:40 ltmain.sh -> /usr/share/libtool/ltmain.sh
-rw-r--r-- 1 terry terry  24511 2008-03-29 10:22 Makefile
-rwx------ 1 terry terry     85 2008-03-18 04:33 Makefile.am
-rw-r--r-- 1 terry terry  20673 2008-03-29 10:22 Makefile.in
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 missing -> /usr/share/automake-1.9/missing
drwx------ 3 terry terry   4096 2008-03-29 10:22 po
drwx------ 5 terry terry   4096 2009-02-22 11:17 src
-rw-r--r-- 1 terry terry     23 2008-03-29 10:22 stamp-h1
terry@terry-laptop:~/Desktop/rendering$

---

### Post by Old *ix Geek on 2009-02-22
> **hollowtd said:**
> terry@terry-laptop:~$ cd Desktop/rendering
terry@terry-laptop:~/Desktop/rendering$ ls -l
total 1616
-rw-r--r-- 1 terry terry 294754 2008-03-29 10:22 aclocal.m4
drwxr-xr-x 2 terry terry   4096 2008-03-29 10:22 autom4te.cache
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 compile -> /usr/share/automake-1.9/compile
lrwxrwxrwx 1 terry terry     36 2009-02-19 17:40 config.guess -> /usr/share/automake-1.9/config.guess
-rw-r--r-- 1 terry terry   2504 2008-03-29 10:22 config.h
-rw-r--r-- 1 terry terry   2234 2008-03-29 10:22 config.h.in
-rw-r--r-- 1 terry terry  36798 2008-03-29 10:22 config.log
-rwxr-xr-x 1 terry terry  39276 2008-03-29 10:22 config.status
lrwxrwxrwx 1 terry terry     34 2009-02-19 17:40 config.sub -> /usr/share/automake-1.9/config.sub
**-rwxr-xr-x 1 terry terry 781725 2008-03-29 10:22 configure**
-rwx------ 1 terry terry   1188 2008-03-18 04:33 configure.ac
drwx------ 3 terry terry   4096 2008-03-29 10:22 data
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 depcomp -> /usr/share/automake-1.9/depcomp
lrwxrwxrwx 1 terry terry     34 2009-02-19 17:40 install-sh -> /usr/share/automake-1.9/install-sh
-rwxr-xr-x 1 terry terry  22491 2008-03-29 10:22 intltool-extract
-rwx------ 1 terry terry  22493 2008-03-18 04:33 intltool-extract.in
-rwxr-xr-x 1 terry terry  35214 2008-03-29 10:22 intltool-merge
-rwx------ 1 terry terry  35219 2008-03-18 04:33 intltool-merge.in
-rwxr-xr-x 1 terry terry  28116 2008-03-29 10:22 intltool-update
-rwx------ 1 terry terry  28061 2008-03-18 04:33 intltool-update.in
-rwxr-xr-x 1 terry terry 219129 2008-03-29 10:22 libtool
lrwxrwxrwx 1 terry terry     28 2009-02-19 17:40 ltmain.sh -> /usr/share/libtool/ltmain.sh
-rw-r--r-- 1 terry terry  24511 2008-03-29 10:22 Makefile
-rwx------ 1 terry terry     85 2008-03-18 04:33 Makefile.am
-rw-r--r-- 1 terry terry  20673 2008-03-29 10:22 Makefile.in
lrwxrwxrwx 1 terry terry     31 2009-02-19 17:40 missing -> /usr/share/automake-1.9/missing
drwx------ 3 terry terry   4096 2008-03-29 10:22 po
drwx------ 5 terry terry   4096 2009-02-22 11:17 src
-rw-r--r-- 1 terry terry     23 2008-03-29 10:22 stamp-h1
terry@terry-laptop:~/Desktop/rendering$

Stay in that directory (in the UNIX/Linux world, they're called directories...or at least they were originally! now with so many former windoze users, they're also called folders a lot).  Type this:

```
./configure
```

---

### Post by hollowtd on 2009-02-22
terry@terry-laptop:~/Desktop/rendering$ ./configure
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
terry@terry-laptop:~/Desktop/rendering$ 


it says this

---

### Post by hollowtd on 2009-02-22
It's like it can't find the install.sh. It's in there in the rendering folder, but there's a lock icon next to it. Does that mean something?

---

### Post by spiderbatdad on 2009-02-22
**1 terry terry 31 2009-02-19 17:40 missing -> /usr/share/automake-1.9/missing**

sudo apt-get install build-essential && sudo apt-get install automake1.9

---

### Post by hollowtd on 2009-02-22
I'll try that and let you know if it helps. Thanks for your help again!

---

### Post by hollowtd on 2009-02-22
No package 'cairo-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


here's what I got. I got those two things installed successfully and then I typed ./configure and got this message above. Is that the command I use to install the folder "rendering" that is sitting on my desktop. (My cairo dock is already working but no 3d stuff yet still) thanks

---

### Post by spiderbatdad on 2009-02-22
there is a program in synaptic for use with cairo-dock for rendering it is called. "xcompmgr"

---

### Post by hollowtd on 2009-02-22
I've downloaded the different one now. It is an .rpm file. Can anyone tell me how to open this and then install it? The box is sitting on my desktop and it says cairo-doc-rendering-1.6.3.1-1mdv2009.1.i586.rpm THaNKS

---

### Post by hollowtd on 2009-02-22
I'll check that out. How might I access it? Sorry but I am really new to all this and need baby step explanations. Thanks for all your help.

---

### Post by spiderbatdad on 2009-02-22
System>>Adminstration>>Synaptic Package manager
or from your terminal: ```
sudo apt-get install xcompmgr
```
to start it, make sure cairo-dock isnt running then press alt+f2 and type in xcompmgr...do it again and type cairo-dock. To make this easy you will need to make a little script with gedit that goes like: ```
xcompmgr &
sleep 2
cairo-dock &
exit 0
```You will need to make the script executable with the command:
```
chmod +x nameOfScript
```what ever you name the script. Then make a folder in your home directory called "bin" put your script in there. Use System>>Preferences>>Sessions to add your script to start up  if you want it to run when you start up. Or create a panel launcher by right clicking on your panel and add to panel a custom launcher...for the command browse to your script. Good luck.

---

### Post by hollowtd on 2009-02-22
I've done the apt-get for the xcompmgr but now am not sure what to do with excutable files and such you speak of.

---

### Post by spiderbatdad on 2009-02-22
try xcompmgr out by quitting cairo-dock. then run xcompmgr by pressing alt+f2 once xcompmgr is running, run cairo-dock. See previous post for making a script and/or launcher.

---

### Post by hollowtd on 2009-02-22
I got that part. I did alt f2 for both xcompmgr and then cairo-dock so they are both running. There is still nothing under the cairo dock applets menu showing options for carousel and 3d though.

---

### Post by spiderbatdad on 2009-02-22
ok. where did you get cairo-dock? I noticed the one in synaptic isnt offering behaving as expected...I'm trying it now. Previously I have used the version here:
[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624)
Get the cairo-dock deb and the cairo-dock plugins deb. You install these two packages by just clicking on them. The gdebi installer will do the rest. You will still need to launch xcompmgr first. You should remove the existing version of cairo before installing this verision. If you wait a sec I'll tell you how its working.

---

### Post by hollowtd on 2009-02-22
I got them from berlios. I have both of those still. I ran the plug ins and it did it's thing and I closed cairo dock and started it again and still nothing. It says that the plug ins are installed and everything when I double click on the plug ins deb file.

---

### Post by spiderbatdad on 2009-02-22
ok have 3d working with version 1.6.1.2 had to purge other installs:
```
sudo dpkg --purge cairo-dock-plug-ins
sudo dpkg --purge cairo-dock
```
installed the versions above...dock and plugins. Tried to configure withouth much luck. Restarted my system. enabled 3d under views menu, I believe, and then under applets. highlighted redering and chose preferences to set carosel effects...screenshot included. BTW did not start xcompmgr after reboot...

---

### Post by hollowtd on 2009-02-23
Wow, you did a lot in a little bit of time. I'm going to check into that today and then get back with you and tell you how it did. Cheers for your efforts and in helping me so much. (I believe I have the beta 2.X of Cairo Dock Installed.)

---

### Post by hollowtd on 2009-02-23
I am trying to purge the cairo-dock and it is not working, even when I close the cairo dock. It says

terry@terry-laptop:~$ sudo dpkg --purge cairo-dock
dpkg: dependency problems prevent removal of cairo-dock:
 cairo-dock-data depends on cairo-dock (>= 1.6.2.3-0ubuntu1).
 cairo-dock-plug-ins depends on cairo-dock.
dpkg: error processing cairo-dock (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 cairo-dock
terry@terry-laptop:~$ 


I have the version 1.6.1.2 on my deskotp and I got the plug ins to install but it won't install the other deb package as it says "error:  a later version is already installed" (the one I am trying to remove through terminal. Any suggestions how to remove the old (newer version) cairo dock so I can install this earlier version? Cheers

---

### Post by hollowtd on 2009-02-23
Thanks for your help. I purged the newer beta versionso of cairo dock and installed the 1.6.1.2 version and restarted my computer and it all works perfectly now. I've been spending days on this and I thank you so much for helping me a true beginner out. I went through synaptic to uninstall all the older (but newer) versions of cairo dock and now the version I have does what I need and want. Thanks and cheers for all the help!!

---

