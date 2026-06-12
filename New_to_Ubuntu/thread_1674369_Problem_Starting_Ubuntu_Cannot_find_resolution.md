---
title: "Problem Starting Ubuntu Cannot find resolution"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by devinsoles on 2011-01-23
Hi, I don't exactly know what the problem is besides this screen here.

[http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg](http://s1096.photobucket.com/albums/g331/devinsoles/?action=view&current=002.jpg)

I have tried nomodeset, and startx on recovery. I also installed inside windows by walkthrough and nothing is helping. My graphics card specs are Generic PnP Monitor @ 1280x720
NVIDIA GeForce GTS 360M

The install screen worked fine but it comes up with that picture after I click on the first option of ubuntu (generic) 

Please help.

---

### Post by Sleven7 on 2011-01-24
Hi devin

The GeForce GTS 360M was only released Jan 2010, your drivers are probably not up to date. Here is a link to the Linux ported driver for that particular graphics card.

[http://driverscollection.com/?file_cid=424154783581b3b86475c0de3fe](http://driverscollection.com/?file_cid=424154783581b3b86475c0de3fe)

---

### Post by davidmohammed on 2011-01-24
doubt that that will resolve - 

here is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/657736") that sounds like your issue.

however if you want to give the above post a try then try the following

purge the noveau driver:

sudo apt-get --purge remove xserver-xorg-video-nouveau

then install using [these]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") instructions:

---

