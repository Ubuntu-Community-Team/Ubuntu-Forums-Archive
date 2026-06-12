---
title: "Unity Launcher is missing"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by ai4kn on 2011-07-13
Help.  I performed an Ubuntu update this morning and my UNITY desktop has gone missing.  I have the GNOME desktop right now and would like to restore UNITY.  How can I do this?

---

### Post by Swagman on 2011-07-13
reboot and at the login... click on your name but dont enter a password just yet.. look down on the bottom bar and there is an option to run Classic desktop or other... click on it and select unity then enter your password and login

---

### Post by ai4kn on 2011-07-13
Tried that.  Three times. Doesn't work.  I took windows off my computer because I like Unity.  Looks like it might be a bad decision now.

---

### Post by bapoumba on 2011-07-13
Do you mean there is no launcher at all when you bring the mouse pointer to the left part of your screen or that the launcher bar is present with no icons ?

---

### Post by ai4kn on 2011-07-13
It just the Gnome desktop.  It's got Applications . . places . . system at the top.

---

### Post by bapoumba on 2011-07-13
Please do as Swagman suggested. Logout and at the bottom of the login window choose ubuntu.

---

### Post by ai4kn on 2011-07-13
I've done that four times already. Twice with a reboot.

---

### Post by bapoumba on 2011-07-13
Please make sure unity is installed.
```
apt-cache show unity
```
Version: 3.8.10-0ubuntu2 on my natty install.

---

### Post by ai4kn on 2011-07-13
Here's what I got:

john@john-GT5657E:~$ apt-cache show unity
Package: unity
Priority: optional
Section: gnome
Installed-Size: 1860
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 3.8.10-0ubuntu2
Replaces: netbook-launcher (<< 1:2.1.18-0ubuntu2)
Provides: indicator-renderer, netbook-launcher
Depends: libatk1.0-0 (>= 1.12.4), libbamf0 (>= 0.2.60), libboost-serialization1.42.0 (>= 1.42.0-1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib3 (>= 0.4.2), libdee-1.0-1 (>= 0.5.2), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1, libglew1.5 (>= 1.5.7.is.1.5.2), libglewmx1.5 (>= 1.5.7.is.1.5.2), libglib2.0-0 (>= 2.28.0), libglibmm-2.4-1c2a (>= 2.28.0), libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.23.90), libice6 (>= 1:1.0.0), libindicator3 (>= 0.3.19), libnux-0.9-0 (>= 0.9.42), libpango1.0-0 (>= 1.20.0), libpcre3 (>= 8.10), libpng12-0 (>= 1.2.13-4), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.5), libunity-misc0 (>= 0.2.1), libutouch-geis1 (>= 1.0.8), libwnck22 (>= 1:2.22), libx11-6, libx11-xcb1, libxcb1, libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxslt1.1 (>= 1.1.25), libxxf86vm1, gconf2 (>= 2.28.1-2), unity-common (= 3.8.10-0ubuntu2), compiz-core, compiz-core-abiversion-20110322, compiz-plugins-main, libglib2.0-bin, python, nux-tools, unity-asset-pool (>= 0.8.18)
Recommends: unity-place-applications, unity-place-files, indicator-appmenu, indicator-application, indicator-sound, indicator-datetime, indicator-messages, indicator-me, indicator-session, ubuntuone-control-panel-gtk
Conflicts: netbook-launcher (<< 1:2.1.18-0ubuntu2)
Breaks: bamf (<< 0.2.76), compiz-core (<< 1:0.9.2.1+glibmainloop3)
Filename: pool/main/u/unity/unity_3.8.10-0ubuntu2_i386.deb
Size: 619798
MD5sum: 3b5ee69a2c86f0d560b147865ce31e1d
SHA1: 64f44d9febf7384029d08aadd00a3d4352d81067
SHA256: ac79738493714075c479ed6667e2404fce19037ae71445aec53bd223742bc80e
Description: Interface designed for efficiency of space and interaction.
 Unity is a desktop experience that sings. Designed by Canonical and the Ayatana
 community, Unity is all about the combination of familiarity and the future. We
 bring together visual design, analysis of user experience testing, modern
 graphics technologies and a deep understanding of the free software landscape
 to produce what we hope will be the lightest, most elegant and most delightful
 way to use your PC.
Homepage: [https://launchpad.net/unity](https://launchpad.net/unity)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, edubuntu-desktop, ubuntu-netbook

This happened following today's update.  Suddenly, Unity was gone and Gnome was up. 
I tried rebooting, bringing up Ubuntu Classic, logging off, bringing up Ubuntu.

If there's a problem with today's update, the Ubuntu people should withdraw it or warn users.

---

### Post by ai4kn on 2011-07-13
During REBOOT, from Grub, I selected Previous Version of Linux.  Unity came up on Linux Version 2.6.38-8, but not on 2.6.38-10.  Like I said, I lost unity following a software upgrade.

---

### Post by bapoumba on 2011-07-13
I ran the updates and rebooted a few hours ago. I'm on 2.6.38-10-generic and unity is running fine here. I'll look around.

---

### Post by bapoumba on 2011-07-13
[http://ubuntuforums.org/showthread.php?p=11043250](http://ubuntuforums.org/showthread.php?p=11043250)
Would you happen to have other repos than the standard ones (such as ppas for video or other things) ?

---

### Post by ai4kn on 2011-07-14
I have a PPA for Grub Customizer and one for a weather app.

---

### Post by ai4kn on 2011-07-14
I have a PPA for Grub Customizer, two to handle my remote control, and one for a weather app.

---

### Post by bapoumba on 2011-07-14
In the thread I quoted, the user had a problem with the video drivers and the new kernel. As you are not using any particular repo for video, do you know which video driver you are currently using ?

---

### Post by ai4kn on 2011-07-14
The latest RADEON HD driver from AMD/ATI.  I did a fresh install of Ubuntu and loaded the driver before I used the FGLRX driver.

---

### Post by ai4kn on 2011-07-15
Solved

I reloaded UBUNTU then ran software update, loaded the ATI drivers.  Problem solved.

---

### Post by bapoumba on 2011-07-16
Glad to see you sorted it out :KS

---

### Post by ai4kn on 2011-07-16
Thanks.  That's one of the things I like about Linux.  There are plenty of people on line willing to help out a newbe like me.

---

### Post by sogrey on 2011-08-05
I have a similar issue.  Dell Optiplex 270 with a Geforce 5200 FX card.  I cannot get the NVIDIA dirver, any version to take.  I used the "experimental" open source driver and have most of Unity.  The "Launcher" on the left hand side of the screen is black with no icons.  When I run the mouse pointer down the black bar, the titles of the icons appear.  (Note: I have searched the internet and this forum for a solution over many hours. Please don't tell me that I haven't looked.)  The problem is the video card which works just fine in windows.

In case I didn't make it clear, this is an 11.04 install.

Thanks in advance...

---

### Post by Aitashan on 2011-08-05
try reinstalling unity

---

### Post by Aitashan on 2011-08-05
have you done the updates yet it really matters

---

