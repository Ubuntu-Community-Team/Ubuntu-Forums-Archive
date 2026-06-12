---
title: "Help installing tar.gz file"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-05-06
i have a tar.gz file and i am a bit new to linux.
i need to install it because it holds the driver for my webcam.
there is a text inside the file that says this:


README AND INSTALL

What is it?
===========
This is version 1.00.xx of the "gspca" video for linux (v4l1) driver, providing
support for webcams and digital cameras based on the  range of chips
manufactured by SunPlus Sonix Z-star Vimicro Conexant Etoms Transvision Mars-Semi Pixart
Gspca have a strong history. The project born with spca50x for Sunplus chipset become spca5xx to support a large range of chipset,
and is now set as gspca. GSPCA mean "Generic Software Package for Camera Adaptator".
 
Please address all correspondence to <mxhaard at magic dot fr>, or
make use of the bug/support/patch tracking facilities provided by SourceForge,
at <http://sourceforge.net/projects/spca50x/>.

License:
========
		    GNU GENERAL PUBLIC LICENSE
		       Version 2, June 1991
see the include license document.

Content:
========
gspcav1 :
	 This folder is set with v4l1 support fully functionnal 
gspcav2 :
	This folder is set with v4l2 driver under construction 
gspcagui: 
	A common application for webcaming under construction
	The grabber is implemented for v4l1 with picture adjustement
	 


This list represents those cameras that are specifically supported by the
driver, and should work to some degree 'out of the box'. A full list of the
cameras known to the project maintainers can be found on
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).
How do I use it?
================

Well, first you need to compile the driver (see below), then you need to make
sure that the v4l infrastructure is set up and then load the driver. After
you've done that, any v4l enabled application, such as spcaview, gqcam, xawtv,
gnomemeeting, camE etc should work.

Supported kernel versions
=========================
The driver should compile and run successfully against most stable versions of
the official Linux 2.6.x kernel upto version 2.6.11 (from <http://www.kernel.org/>)

Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build 

if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>.

Trying a v4l app
================
goes to gspcagui directory
be sure to have libsdl installed with the header
then
make
as root
make install
Plug your webcam and run
gspcagui -d /dev/video0
adjust video0 to your hardware
Press the G button and wait for the webcam probe
you can now play, the two windows are active 
mouse can be used to select a Region of Interess within the grabbing windows
then press the center of the pad to zoom:)
Picture and avi are implemented just press the button to start/stop







please help a newbie learn

---

### Post by logos34 on 2009-05-06
Here's the ubuntu community docs page for that driver:  

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

You should have out-of-box support for the device right now:
> 
Since Gutsy the spca5xx driver has been replaced by gspca. If the webcam does not automatically work check that the gspca module has been loaded with

lsmod | grep gspca

If it is not loaded (the command results in no output) run

sudo modprobe gspca

If not, the instructions on the ubuntu page will walk you through compiling from source.

---

### Post by mr.big_gun on 2009-05-07
thanks ill try it out

---

### Post by mr.big_gun on 2009-05-07
i went to the instructions and i got to the part where it says

Step 4:

Enter the spca5xx directory

cd spca5xx-20051212




it says in terminal: 
bash: cd: spca5xx-20051212: No such file or directory


what am i doing wrong?

---

### Post by taurus on 2009-05-07
Are you in the right directory before you try to change to that subdirectory?

What's the output of this command?

```
ls -la
```

---

### Post by mr.big_gun on 2009-05-07
total 1204
drwxr-xr-x 43 steveo steveo   4096 2009-05-07 17:27 .
drwxr-xr-x  5 root   root     4096 2009-05-06 21:20 ..
drwx------  3 steveo steveo   4096 2009-05-06 20:46 .adobe
-rw-------  1 steveo steveo   1775 2009-05-07 18:14 .bash_history
-rw-r--r--  1 steveo steveo    220 2009-05-05 21:57 .bash_logout
-rw-r--r--  1 steveo steveo   3115 2009-05-05 21:57 .bashrc
-rw-r--r--  1 steveo steveo    889 2009-05-06 20:15 bookmarks.html
drwxr-xr-x  6 steveo steveo   4096 2009-05-06 09:08 .cache
drwx------  3 steveo steveo   4096 2009-05-06 09:57 .compiz
drwxr-xr-x 10 steveo steveo   4096 2009-05-06 09:06 .config
drwx------  3 steveo steveo   4096 2009-05-05 22:39 .dbus
drwxr-xr-x  2 steveo steveo   4096 2009-05-07 13:45 Desktop
-rw-------  1 steveo steveo     28 2009-05-07 17:15 .dmrc
drwxr-xr-x  5 steveo steveo   4096 2009-05-07 15:10 Documents
drwxr-xr-x  4 steveo steveo   4096 2009-05-06 20:55 .emerald
-rw-------  1 steveo steveo     16 2009-05-05 22:39 .esd_auth
-rw-r--r--  1 steveo steveo  10037 2009-05-05 21:57 .face
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 20:46 .fontconfig
drwxr-xr-x  2 root   root     4096 2009-05-07 13:43 Frostwire
drwx------  5 steveo steveo   4096 2009-05-07 17:16 .gconf
drwx------  2 steveo steveo   4096 2009-05-07 18:25 .gconfd
-rw-r-----  1 steveo steveo      0 2009-05-07 14:55 .gksu.lock
drwx------ 10 steveo steveo   4096 2009-05-07 13:46 .gnome2
drwx------  2 steveo steveo   4096 2009-05-05 22:39 .gnome2_private
drwx------  2 steveo steveo   4096 2009-05-05 22:39 .gnupg
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 10:00 .gstreamer-0.10
-rw-r--r--  1 steveo steveo    112 2009-05-07 17:27 .gtk-bookmarks
drwxr-xr-x  3 steveo steveo   4096 2009-05-06 21:08 .gtkpod
dr-x------  2 steveo steveo      0 2009-05-07 17:16 .gvfs
-rw-------  1 steveo steveo   2226 2009-05-07 17:16 .ICEauthority
drwx------  2 steveo steveo   4096 2009-05-06 08:51 .icedteaplugin
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 07:28 .icons
drwxr-xr-x  2 root   root     4096 2009-05-07 13:43 Incomplete
drwx------  3 steveo steveo   4096 2009-05-06 22:40 .kde
-rw-r--r--  1 steveo steveo 976970 2009-05-07 17:27 ljkdbhghkldbagkh
drwx------  3 steveo steveo   4096 2009-05-05 22:39 .local
drwx------  3 steveo steveo   4096 2009-05-06 20:46 .macromedia
drwx------  4 steveo steveo   4096 2009-05-06 07:32 .mozilla
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 08:55 .mplayer
drwxr-xr-x  8 steveo steveo   4096 2009-05-06 20:07 Music
drwxr-xr-x  3 steveo steveo   4096 2009-05-07 13:46 .nautilus
drwxr-xr-x  7 steveo steveo   4096 2009-05-06 20:07 Pictures
-rw-r--r--  1 steveo steveo    675 2009-05-05 21:57 .profile
drwxr-xr-x  2 steveo steveo   4096 2009-05-05 22:39 Public
drwxr-xr-x  2 steveo steveo   4096 2009-05-05 22:39 .pulse
-rw-------  1 steveo steveo    256 2009-05-05 22:39 .pulse-cookie
drwx------  5 steveo steveo   4096 2009-05-06 07:24 .purple
-rw-------  1 steveo steveo   6540 2009-05-07 17:27 .recently-used.xbel
-rw-r--r--  1 steveo steveo      0 2009-05-05 22:43 .sudo_as_admin_successful
drwxr-xr-x  2 steveo steveo   4096 2009-05-05 22:39 Templates
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 07:27 .themes
drwx------  3 steveo steveo   4096 2009-05-06 07:28 .thumbnails
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 09:05 .update-manager-core
drwx------  2 steveo steveo   4096 2009-05-05 22:39 .update-notifier
drwxr-xr-x  7 steveo steveo   4096 2009-05-06 20:07 Videos
drwxr-xr-x  4 steveo steveo   4096 2009-05-06 22:53 .VirtualBox
drwxr-xr-x  2 steveo steveo   4096 2009-05-06 21:05 .wapi
drwxr-xr-x  9 steveo steveo   4096 2009-05-06 20:06 Windows Programs
-rw-------  1 steveo steveo    117 2009-05-07 17:15 .Xauthority
-rw-r--r--  1 steveo steveo   1116 2009-05-06 21:04 .xscreensaver-getimage.cache
-rw-r--r--  1 steveo steveo   6763 2009-05-07 18:26 .xsession-errors








i went to this site:

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

---

### Post by jacksinn on 2009-05-07
You are currently in your home directory (in the terminal). It is likely that you have the driver extracted on your desktop so you'll want to:
cd Desktop
then cd into the folder that has the driver. If you aren't sure where it is, do the following:

cd ~; find . -name spca5xx-20051212;

Then cd to the directory when the result is returned.

---

