---
title: "How do I install from an SVN repository"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-08-16
[http://www.freedroid.org/download/](http://www.freedroid.org/download/)

You can also get the latest developer version from our SVN repository. 
 This version sometimes fails to build and can be unstable, but it often   contain new features. Besides, it will enable you to help us by  finding  and fixing bugs.
 You will need a SVN client to be able to download the developer version.
 
 Here is how you can do it using the command line client:
 
 FreedroidRPG:
 svn co [https://freedroid.svn.sourceforge.net/svnroot/freedroid](https://freedroid.svn.sourceforge.net/svnroot/freedroid) freedroid

---

### Post by HalfEmptyHero on 2011-08-16
If you look at [http://freedroid.svn.sourceforge.net/viewvc/freedroid/INSTALL?view=markup](http://freedroid.svn.sourceforge.net/viewvc/freedroid/INSTALL?view=markup) it tells you exactly how to do it. 

```
sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev libogg-dev liblua5.1-dev

  Move to the FreedroidRPG source directory using "cd ./XYZ/" command. XYZ = path to the FreedroidRPG source.

./autogen.sh 

./configure

make

sudo make install

```

---

### Post by theozzlives on 2011-08-16
Then do it. If that don't work read the readme file

---

### Post by TheManno1 on 2011-08-16
By some fluke I installed it. Say I want  to install from this svn [http://mancubus.net/svn/gzdoom/tags/1.5.06/?#a3f6f0464520cceb466bdea9dcbf5b3c6](http://mancubus.net/svn/gzdoom/tags/1.5.06/?#a3f6f0464520cceb466bdea9dcbf5b3c6). What am I suppose to do and finally how do I make a deb file from the thing I compiled.

---

