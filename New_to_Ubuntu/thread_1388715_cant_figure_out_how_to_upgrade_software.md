---
title: "cant figure out how to upgrade software"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by ave2 on 2010-01-23
Im trying to upgrade the following software- Kid3 Id3 tagger from version 1.2.1 to the latest version

so I went to the website 
[http://kid3.sourceforge.net/#download](http://kid3.sourceforge.net/#download)
and there were two options: 

1) add a package to software sources- I followed the instructions on the following page:
[https://edge.launchpad.net/~neversfelde/+archive/ppa](https://edge.launchpad.net/~neversfelde/+archive/ppa)

(add ppa:neversfelde/ppa  to your system's Software Sources.)

I did that, but the software center still only displayed the older version

so I went for the second option- downloaded the .deb file

it told me that its the wrong architecture (im running a 64 bit version of ubuntu)

so I used the following command:

sudo dpkg -i --force-all <package_name.deb>

that installed it, but now I have got no idea how to access it- in fact all it did was corrupt my current version, so now I cant access either? 

what am I doing wrong? why does this have to be so complicated???

---

### Post by cariboo on 2010-01-23
After adding the ppa did you update the sources.list?

---

