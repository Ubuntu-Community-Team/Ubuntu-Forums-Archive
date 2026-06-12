---
title: "Dial up modem Not on 9.1 CD"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Richard Nicholson on 2009-11-20
Hi

I loaded Ubuntu onto a friends PC, with a windoze partition. As she only has a dial up modem I couldn't load the Network and Gnome PPP program via the software centre. How do you get around this. It's a catch 22. Though there must be a way I'm sure.
:-k

---

### Post by lkraemer on 2009-11-20
Yes, that is a problem.  You are going to need to go somewhere that
has Internet access so you can download the proper packages for your version.  8.04, 8.10, 9.04, 9.10 etc.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You need to download the following files:
wvdial_1.60.1_i386.deb  (or the latest versions for your distro)

Dependencies:
libuniconf4.4_4.4.1-0ubuntu2_i386.deb
libwvstreams4.4-base_4.4.1-0ubuntu2_i386.deb
libwvstreams4.4-extras_4.4.1-0ubuntu2_i386.deb
libxplc0.3.13_0.3.13-1build1_i386.deb

Then copy them to the computer you are going to be using dialup on, to:
/var/cache/apt/archives

Then install.

There is a good tutorial I wrote at:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4

Good Luck!  Shouldn't take more than 30 minutes with a External Hardware
US Robotics (Serial) Modem.

When you are finished, download and install Gnome-ppp.  It will work
wonderful.

lk

---

### Post by gettinoriginal on 2009-11-20
This site also has an easy to follow solution: 
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

