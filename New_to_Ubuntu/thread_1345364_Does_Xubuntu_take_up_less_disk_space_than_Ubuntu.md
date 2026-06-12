---
title: "Does Xubuntu take up less disk space than Ubuntu?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by mishathegoat on 2009-12-04
I'm installing a 'buntu distro to a 4G flash drive so disk space is crucial. I know Xubuntu uses fewer resources but does it also take up less disk space?

Thanks for your help

---

### Post by travmanx on 2009-12-04
To install Xubuntu, you need 1.5-2.0 GB of free space on your disk.
You should be fine :)

Bare minimum requirement for Ubuntu - 4 GB
Recommended - 8 GB

So yes it uses less disk space.

---

### Post by mishathegoat on 2009-12-04
Awesome thanks for the quick  response

---

### Post by winotree on 2009-12-04
/dev/sda1             3.5G  1.7G  1.7G   50% /

This is a copy-and-paste of **df** using the default format, including the 227.48MB swap space, plus several additional applications, my bookmarks, images, ubuntu-docs and the xubuntu-restricted-extras -- in other words, what **travmanx **said.  :D

---

### Post by jbrown96 on 2009-12-04
I doubt the difference is significant. XFCE is built on GTK+, which is the same toolkit used for Gnome. It has the same dependencies as Ubuntu, so there's not really any way to save space. 

That being said, Xubuntu may skip some apps that Ubuntu includes. Also maybe the menus, desktop, that kind of stuff is actually smaller on Xubuntu. That's possible, but I doubt the difference would be significant. 

The key to keeping your disk usage low is to
1) Don't mix KDE and Gnome apps. This causes a lot of extra dependencies. 
2) Run ```
sudo apt-get autoclean && sudo apt-get autoremove
``` frequently, so you aren't keeping package files on your system. 
3) Remove old kernels and kernel-headers
4) Remove programs you don't use. Programs like OpenOffice are very large (I think around 500MB installed).

---

### Post by jollysnowman on 2009-12-04
> **jbrown96 said:**
> I doubt the difference is significant. XFCE is built on GTK+, which is the same toolkit used for Gnome. It has the same dependencies as Ubuntu, so there's not really any way to save space.

???? Did you read the other posts?

---

### Post by jbrown96 on 2009-12-04
> **jollysnowman said:**
> ???? Did you read the other posts?

So I download Xubuntu 9.10, and installed it in Virtualbox. I choose the guided partitioning scheme. Immediatelfindy after installation ```
sudo du -hsx /
``` reports > 2.3G / combine that with a swap size of 400MB and that's 2.7GB. I then ran a single round of updates and restarted. Xubuntu balooned to 2.6GB plus swap = 3GB. That's a far cry from the 1.5-2GB that the devs recommend. 

Granted Xubuntu includes Gimp and OpenOffice for some reason. It would be possible to slim this down. The main problem is with a 4GB limit is that you're going to be on it all the time. You will constantly need clear your apt cache, and watch your disk use.

Don't the EEE's have two hard drives? You could create an lvm with at least part of the larger drive. 

4GB is really to small for any decent OS. There's so much stuff that gets added to the hard drive that it would be painful to run a system like this. My firefox profile is 230MB; that's about 25% of the remaining free space.

If I have time tomorrow, I'll try the same process with Ubuntu and Lubuntu. I'd say that Lubuntu will be the lightest by far, but again, the lighter you go, the fewer features there are.

---

### Post by Ylon on 2009-12-04
Other than already suggested you can spare more space:


```
sudo apt-get install deborphan
sudo aptitude purge `deborphan --guess-all`
```
(this remove dependencies that no-one application use)


and


**sudo rm /var/cache/apt/archives/***

(this erase all the *.deb after install/update packages... wich were _always_ keep stored even if no longer used)

---

### Post by winotree on 2009-12-04
> **jbrown96 said:**
> 
....Don't the EEE's have two hard drives? You could create an lvm with at least part of the larger drive.... No -- the original 701 had only one 4GB SSD and the surf model had 2GB.

> ....4GB is really to small for any decent OS. There's so much stuff that gets added to the hard drive that it would be painful to run a system like this.... I really must disagree with you in this respect -- I've tried most of the Gnome-based distributions listed over at Distrowatch with nary a problem -- and** at a minimum** still had 1.2GB left over for myself.  Just saying...  :D

---

### Post by WubiNoob on 2010-02-27
xubuntu is the best!!!!!!! It's very efficent, so you know it will run just fine on a USB drive, so no problems there.

---

### Post by bodhi.zazen on 2010-03-10
> **jbrown96 said:**
> So I download Xubuntu 9.10, and installed it in Virtualbox. I choose the guided partitioning scheme. Immediatelfindy after installation ```
sudo du -hsx /
``` reports  combine that with a swap size of 400MB and that's 2.7GB. I then ran a single round of updates and restarted. Xubuntu balooned to 2.6GB plus swap = 3GB. That's a far cry from the 1.5-2GB that the devs recommend. 

Granted Xubuntu includes Gimp and OpenOffice for some reason. It would be possible to slim this down. The main problem is with a 4GB limit is that you're going to be on it all the time. You will constantly need clear your apt cache, and watch your disk use.

Don't the EEE's have two hard drives? You could create an lvm with at least part of the larger drive. 

4GB is really to small for any decent OS. There's so much stuff that gets added to the hard drive that it would be painful to run a system like this. My firefox profile is 230MB; that's about 25% of the remaining free space.

If I have time tomorrow, I'll try the same process with Ubuntu and Lubuntu. I'd say that Lubuntu will be the lightest by far, but again, the lighter you go, the fewer features there are.

I see this is an old thread, but I have a few comments about your post.

First including Swap space is a tad deceiving, your swap space will be the same size regardless of your OS and if you are tight on RAM that is almost a separate issue (ram is cheap).  If you have 1 Gb or RAM you may not need Swap at all. If you are tight on RAM and HD space swap can be as small as 256-512 Mb.

Yes you need to included this in your installation planning, but it is fixed and not necessarily related to the size of the base file system or root / partition.

The two applications / packages that take up a significant amount of space are the language packs and OpenOffice. On low end machines I advise you avoid OpenOffice if you can.

At any rate, Zenix, which is Ubuntu + security + xfce + Fluxbox takes 1.5 Gb of HD space, add half a Gb for swap and you get 2 Gb , well within the 4 Gb minimum:

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

