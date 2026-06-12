---
title: "Guayadeque In Sound Tab"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by TheAlexCole on 2011-05-05
I've been reading and I hear Guayadeque is better than Banshee. I have installed Guayadeque and I was wondering if it is possible to make it appear in the sound tab at the top right (like banshee did).

Thanks in Advance,
-Cole

---

### Post by TheAlexCole on 2011-05-07
**Bump**ity? :(

---

### Post by Hreinsi on 2011-05-07
:)

---

### Post by Hreinsi on 2011-05-07
you can in svn version 
[http://guayadeque.org/forums/index.php?p=/page/installing](http://guayadeque.org/forums/index.php?p=/page/installing)

i have used Guayadeque over a year now and LOVE IT much better than Banshee anr rythbox sonbird and others ligther faster more options

---

### Post by Hreinsi on 2011-05-07
Install (ubuntu-restricted-extras)  for codecs and stuff
If you have ppa or from repos you should do sudo apt-get remove guayadeque and

Installing from SVN
Why would you want to install from svn? Because the SVN provides the most up to date
version with the latest bug fixes and improvements. A typical example would be when you
report a bug, this is fixed and the fix is then incorporated into the last SVN version: you will
need to update to this version if you want that fix.
The first step is to install the development tools that you will need to build the executable.
To do so open a terminal and type:

sudo apt-get install subversion build-essential cmake gettext

Next you will install the development dependencies needed by Guayadeque:

sudo apt-get install libwxgtk2.8-dev libtagc0-dev libsqlite3-dev libcurl4-gnutls-devlibdbus-1-dev libgstreamer0.10-dev libflac-dev

If you want iPod support then:

sudo apt-get install libgpod-dev

Now we can grab the source code and start building the project:

cd

svn co [http://guayadeque.svn.sourceforge.net/svnroot](http://guayadeque.svn.sourceforge.net/svnroot)/guayadeque/Trunkguayadeque

cd guayadeque

./build

sudo make install

If there is a new svn version and you wan to update to it you have to do this manualy. In a
terminal (one line at a time):

cd guayadeque

svn update

./build

sudo make install

---

### Post by Hreinsi on 2011-05-07
:)

---

