---
title: "Second Life install on Ubuntu 9.10 64 bit"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by mumpspro on 2009-11-18
I am new to Ubuntu, but am trying it out and wanted to install Second Life.  I was able to find linux versions, and have installed it, but seem to be missing some 32bit libraries.  Could someone please assist?

mumpspro@ubuntu:/host/ProgramData/ubuntu/GreenLife-i686-1.23.5.950$ ./secondlife64-bit Linux detected: Disabling GStreamer (streaming video and music) by default; edit ./secondlife to re-enable.
Running from /host/ProgramData/ubuntu/GreenLife-i686-1.23.5.950
Warning: Did not register secondlife:// handler with KDE: Directory /home/mumpspro/.kde/share/services does not exist.
./secondlife: line 122: bin/do-not-directly-run-secondlife-bin: No such file or directory
*** Bad shutdown. ***

You are running the Second Life Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-secondlife-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl

*******************************************************
This is a BETA release of the Second Life linux client.
Thank you for testing!
Please see README-linux.txt before reporting problems.

mumpspro@ubuntu:/host/ProgramData/ubuntu/GreenLife-i686-1.23.5.950$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
[sudo] password for mumpspro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ia32-libs instead of ia32-libs-gtk
**[COLOR=Red]E: Couldn't find package ia32-libs-kde[/COLOR]**

---

### Post by mumpspro on 2009-11-18
I finally found the library in the following location:

[https://launchpad.net/ubuntu/+source/ia32-libs-kde/7.2/+build/234222](https://launchpad.net/ubuntu/+source/ia32-libs-kde/7.2/+build/234222)

After installation, I was successful in getting the app to run.

---

