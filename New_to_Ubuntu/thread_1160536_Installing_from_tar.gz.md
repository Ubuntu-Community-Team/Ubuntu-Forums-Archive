---
title: "Installing from tar.gz"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by darrelljon on 2009-05-15
Okay twice I've downloaded and extracted tar.gz packages because I cannot get my preferred deb packages. One for Smile (Slideshow Maker in Linux Environment) and one for the latest Firefox 3.0.10 (had to get from Mozilla official site) which Kubuntu 8.04 was insisting the latest was 3.0.8 when I tried to update it with a sudo apt-get install firefox (says I already have the latest version!). I've tried to ./configure and make in both directories where I extracted the files but to no avail. Neither directories have configure files or even make files! What am I missing? I've never compiled from source but what I am doing wrong?

---

### Post by spiderbatdad on 2009-05-15
smile for instance, as you noticed, isn't a standard linux source package with configure and make. I didn't find any instructions for compiling it either...so dependencies may be an issue for you. Looks like it is built with qmake like
/usr/bin/qmake-qt4 smile.pro
make
See this posting for more information and a list of possible dependencies...good luck.
[http://ubuntuforums.org/archive/index.php/t-885201.html](http://ubuntuforums.org/archive/index.php/t-885201.html)

---

### Post by darrelljon on 2009-05-16
Thanks but what about Firefox? Can I just enable more repositories perhaps?

---

### Post by Sir Jasper on 2009-05-16
Hi,

Re Firefox settings - Edit>Preferences>Advanced>Upgrade
may be worth a look. I didn't need tar to upgrade to 3.0.10.

My regards

---

### Post by Bölvaður on 2009-05-16
firefox comes precompiled in the .tar you just need to untar it and place into desirable location

---

### Post by Sir Jasper on 2009-05-16
Hi,

"firefox comes precompiled in the .tar you just need to untar it and place into desirable location"

My Firefox is entirely contained in .mozilla in Home.
Presumably it is a good idea to backup bookmarks before the tar install?

Also, I would be interested to learn how you know it's precompiled after it's extracted?

My regards

---

