---
title: "How do I install swscanner from SVN?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by Apex-jb on 2007-08-10
I have heard that swscanner works if you install from SVN but I dont know what SVN is or how to do it. Can anyone help me out?

---

### Post by Apex-jb on 2007-08-11
*bumb*

---

### Post by kevdog on 2007-08-11
I never got swscanner to work for me on Ubunut -- the version is very old, but if you get it working let me know.

To install svn
sudo aptitude install subversion

Do you have the URL for the subversion repository??? I couldnt find it.  If you do the basic format for checking out the version is:

svn co <URL>

---

### Post by Rockman4140 on 2007-09-22
Sorry to revive the thread, but I am attempting to get SWScanner installed from the SVN as well. My issue is that I am compiling it from the tarball, and I've come across a small error. After attempting a make command, it errors out near the end with ```
configure: error: iwlib.h not found. Missing wireless-tools??
```

I've got wireless-tools installed, I made sure to apt-get it, and it says it's at the latest version, so what else could that mean?

---

### Post by kevdog on 2007-09-22
Just an FYI

Any time you compile things you need the developmental files.  These contain the headers and libraries.

Go to the command line and type

sudo apt-cache search libiw

You need to install the libiw-dev package for sure.  You may need the libiw28 package as well, I cant be sure of that.

sudo apt-get install libiw-dev

You should then be able to compile swscanner.

---

### Post by calraith on 2008-05-22
How to build in Hardy (how I did it in my Gnome environment, anyway):

```
sudo aptitude install subversion[FONT=monospace]
[/FONT]svn co https://svn.swscanner.org/swscanner/trunk swscanner
sudo aptitude install build-essential xorg-dev libpng12-dev libjpeg62-dev libqt3-mt-dev libqt3-mt-sqlite libshp-dev kdelibs4-dev libiw-dev autoconf automake1.9 checkinstall
make -f Makefile.cvs
./configure --prefix=/usr
sudo checkinstall
```

---

### Post by kevdog on 2008-05-22
Was there a reason for reviving this old thread?

---

### Post by calraith on 2008-05-23
It was a top result in a Google search.  I figured it would be again the next time I looked for this information.  :P

For what it's worth, I built a .deb for swscanner from SVN since my last posting.  [http://headcandy.org/rojo/swscanner](http://headcandy.org/rojo/swscanner)

---

### Post by jschall on 2008-06-09
> **calraith said:**
> 
For what it's worth, I built a .deb for swscanner from SVN since my last posting.  [http://headcandy.org/rojo/swscanner](http://headcandy.org/rojo/swscanner)

Thanks, Calraith! I FINALLY was able to install SWScanner using your package!

- Jeff

---

