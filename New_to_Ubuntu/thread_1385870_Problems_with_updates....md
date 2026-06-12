---
title: "Problems with updates..."
date: 2010-01-20
forum: New to Ubuntu
---

### Post by jackdale on 2010-01-20
I'm a relative newbie and almost 0 previous experience with linux/unix.

I posted a question on the Installation & Upgrades forum, but I think it was probably the wrong place to post it 'cause I've had no response yet...(that or they think I'm an idiot, or I'm just impatient and should wait a bit longer...;))

Anyway, the problem is that Update Manager tells me I can install a new version of debhelper (going to version 7.4.3~bpo50~1 from 7.3.15ubuntu3)

However, when I click install, I get the message:

> Warning

You are about to install software that can't be authenticated.
Doing this could allow a malicious individual to damage or take control of your system.


Is everyone else getting this and I'm just paranoid or is it something else?

(My original post is [here]("http://ubuntuforums.org/showthread.php?p=8684788#post8684788"))

---

### Post by wilee-nilee on 2010-01-20
Assuming all your repositories are legit you are missing a source verification key.

---

### Post by jackdale on 2010-01-20
> **wilee-nilee said:**
> Assuming all your repositories are legit you are missing a source verification key.


Thanks for the reply!:D

How do I get the missing Key (why would it be missing, btw...I don't generally mess around with software sources and keys...)

Does anyone else have the debhelper version 7.4.3~bpo50~1???  How would I find out if my repos are legit?

In case this might be relevant...
Software Sources:
Ubuntu:
Main Server

Other:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) (not working right now)
[http://pini.free.fr/debian](http://pini.free.fr/debian)
[http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) (the guys need to pay their Domain Name fees...)
[http://nullbound.com](http://nullbound.com)
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)

Updates:
karmic-security
karmic-updates

---

### Post by wilee-nilee on 2010-01-20
If you run a update you should get a error message of the repository missing the key write it down and go to where you got it or search the web.

I doubt your sources are not legit but I didn't install them in my computer. If you fell that you haven't installed any shady package sites then none are installed, they don't appear by magic.

---

### Post by jackdale on 2010-01-20
Thanks for that.

I assume that debhelper is from the main ubuntu repo...
are you saying that this is not the current version?

I'll try to disable my other software sources and see if it is still comming from Ubuntu.  From what you're saying, if it is comming direct from the Ubuntu repo (as no other sources are selected) it should be legit.

Thanks.

Edit To Add (22-01-10)
I found the culprit:
Repo: pini.free.fr/debian
I have now deleted the repo and the program that required it (MuSEscore), which did not work anyway!

---

