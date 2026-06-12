---
title: "New to this"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by broonzyfan on 2010-08-21
Absolute beginner to Ubuntu - & find it opens with a DOS screen wanting username and password.  enter those and still on a DOS screen.  I am sure that is not how it is supposed to be but find it the same whether on the 8.04 thta I have installed or the 10.0 when run from CD.
Anyone tell me where I am going wrong here.  Should add it is on an older  Sony Viao with 256meg ram and it is the only O/S system installed on it.  Hard drive formatted before installation.
I have just a basic knowlege of computers, but over a long time( as I remember DOS when everything was done out of it !!  Long forgotten now.
I want to get properly into this system but a disappointing start.
 
All help welcome.

---

### Post by J V on 2010-08-21
Download 10.0**4**, checksum it, and install it, use the installation procedure to create the partitions.

If this still won't work, set the boot flag VGA=771 (More info on google)

Edit: I see you are using lubuntu, why don't you try crunchbang if lubuntu isn't working...

---

### Post by The Thunder Chimp on 2010-08-21
> **broonzyfan said:**
> Absolute beginner to Ubuntu - & find it opens with a DOS screen wanting username and password.  enter those and still on a DOS screen.  I am sure that is not how it is supposed to be but find it the same whether on the 8.04 thta I have installed or the 10.0 when run from CD.
Anyone tell me where I am going wrong here.  Should add it is on an older  Sony Viao with 256meg ram and it is the only O/S system installed on it.  Hard drive formatted before installation.
I have just a basic knowlege of computers, but over a long time( as I remember DOS when everything was done out of it !!  Long forgotten now.
I want to get properly into this system but a disappointing start.
 
All help welcome.

A DOS screen? Did you install Ubuntu in Command Line Mode? 256 Mb of RAM should allow a GUI, but that would be slow on regular Ubuntu (which runs on a so-called "GNOME" Graphical User Interface), so I would recommend a lighter version such as [Xubuntu](http://en.wikipedia.org/wiki/Xubuntu) or [Lubuntu](http://lubuntu.net/).

Hope this helps!

EDIT: Thanks to J V, I just realized you already were on Lubuntu. You could try Xubuntu then.

---

### Post by jmfal on 2010-08-21
The first reply should do it but if it doesn`t next time you restart and get to that screen

enter username/password and at next command prompt enter

        ```
 startx
```
this should get you to the desktop and maybe you can correct the problem from there

---

### Post by phillw on 2010-08-21
> **J V said:**
> 
Edit: I see you are using lubuntu, why don't you try crunchbang if lubuntu isn't working...

Possibly because he wants a member of the ubuntu family?

If you are on a 256MB ram machine you are pushing what ubiquity can do (that is the standard installer across the ubuntu family). It really starts to struggle if you are on 256MB and have shared graphics (which is usual for such machines). [256 MB RAM and below](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall) has how to install Lubuntu on lower RAM machines. > A Pentium II or Celeron system with 128 Mb RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. is as low as lubuntu can go, you are well above that area, just use the minimal installation as I do think it is Ubiquity that is causing the problem.

Regards,

Phill.
P.S. I'm subscribing to this thread, if you have further questions do just post them.

---

### Post by J V on 2010-08-22
Crunchbang = ubuntu derivative, like the others, and only kubuntu/edubuntu are officially part of the "Ubuntu family"

---

