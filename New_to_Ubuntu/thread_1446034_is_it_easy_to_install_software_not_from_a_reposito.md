---
title: "is it easy to install software not from a repository_"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by ginestre on 2010-04-03
I have to upgrade my installation of lyx from 1.6.4 to lyx 1.6.5 to cope with a  bug in 1.6.4, the repository version of lyx. 

Is this upgrade an easy process? Is it better to start from source code? How should I start?

---

### Post by kblft on 2010-04-03
You have several options : 

1. check this site [http://www.getdeb.net/app/LyX](http://www.getdeb.net/app/LyX) offering lyx .deb installers for ubuntu - no need to compile code.

2. you can wait for lucid to be released in a few weeks as it seems that lucid will have lyx 1.6.5 ( [http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all))

3. you can wait for lucid to be released and see if it gets backported 

4. you can compile from source ( instructions [http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all) and [http://wiki.lyx.org/Tips/Compiling](http://wiki.lyx.org/Tips/Compiling) )

---

### Post by Naitsirhc Hsem on 2010-04-03
You might be able to download the new version from packages.debian.org.  if it yells at you about dependencies not being avalable, you can add the debian sources into your sources center temporarily.

---

### Post by ginestre on 2010-04-03
> **kblft said:**
> You have several options : 


4. you can compile from source ( instructions [http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=lyx&searchon=names&suite=lucid&section=all) and [http://wiki.lyx.org/Tips/Compiling](http://wiki.lyx.org/Tips/Compiling) )

Thanks for this. I bit the bullet and compiled, following these excellent instructions. It all worked first time!

---

