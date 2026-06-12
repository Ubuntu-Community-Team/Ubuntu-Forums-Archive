---
title: "How do I install a tar.gz file?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-06-25
Hello,

I'm trying to install [gnomenu]("https://launchpad.net/gnomenu"), but I don't know what to do with tar.gz files, which is what it comes as.  Any help?  A step-by-step guide would be great, since I'm pretty new.  Thanks!

-Val

---

### Post by TheForumTroll on 2009-06-25
It's a compressed file like zip files. You have to uncompress it. Double clicking it should open the archive manager letting you chose where to place the files.

---

### Post by oldos2er on 2009-06-25
Install it from a *.deb file: [http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu_1.9.6-6_all.deb](http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu_1.9.6-6_all.deb)

---

### Post by Prince Valiant on 2009-06-25
Thanks...but how can I *install* it?

I know how to extract, install .deb files, etc.  But tar.gz have always stumped me.  For this particular file, Google gave me no success. I've heard of cd-ing tarballs, and "sudo make something-or-other," but I don't know how to do it.  

-Val

---

### Post by Celauran on 2009-06-25
Compiling from source typically involves ./configure, ./make, and ./make install. There should be a readme in the tarball, though.

---

### Post by Prince Valiant on 2009-06-25
Oldos2er:

Thanks for the file; I tried it and the installation failed. :(

-Val

---

### Post by halitech on 2009-06-25
are you using the 64bit version or 32bit?

---

### Post by Prince Valiant on 2009-06-25
> are you using the 64bit version or 32bit?Of the .deb file?   I'm not sure.  The computer I use is 32 bit.

I looked in other forum threads and found instructions to do the following:
```

./configure
make
sudo make install 
```However, I know I can't paste that into the terminal, since the computer doesn't know what file I'm talking about.  I've copied the tar.gz file to my desktop, and It's called "gnomenu-1.9.9.tar.gz."  What can I type into the terminal in order to install this?  Thanks a whole lot for helping me.

-Val

---

### Post by sisco311 on 2009-06-25
> **Prince Valiant said:**
> Oldos2er:

Thanks for the file; I tried it and the installation failed. :(

-Val

Any error message?


if you want to compile it, then open a terminal.

download the archive and extract it:
```

wget http://launchpad.net/gnomenu/trunk/1.9-final/+download/gnomenu-1.9.9.tar.gz
tar xzvf ./gnomenu-1.9.9.tar.gz

```

install the dependencies:  
```

sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet build-essential

```

install gnomenu: 
```

cd ./gnomenu
sudo make install

```

---

### Post by Prince Valiant on 2009-06-25
Thank you sisco311!  That's exactly what I needed!  Problem solved.

-Val__

---

### Post by SunnyRabbiera on 2009-06-25
I would kind of ignore gnomenu, I mean yes I understand the want to have a vista like menu for familiarity purposes but gnomenu in my experience has not been all that stable.

---

