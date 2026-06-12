---
title: "OpenGL installation"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Shippou on 2009-01-28
Hello...

How do you install this thing? This is required by Aegisub in order to install properly in Linux.

Please help.

---

### Post by skymera on 2009-01-28
What is Aegisub?

Is it not in the repositories?
I'm also sure OpenGL is installed by default, however the program might need an older/newer version.

---

### Post by alienexplorers on 2009-01-28
OPenGL support should be loaded with your restricted graphic driver.

---

### Post by jespdj on 2009-01-28
What video card do you have and which video driver are you using?

Make sure you enable the restricted driver, look at System > Administration > Hardware Drivers if there's a driver available for your video card.

---

### Post by 3rdalbum on 2009-01-28
You may need to install the packages that have "mesa" in their name, but don't have "dev" or "dbg". Mesa is the Linux implementation of OpenGL.

---

### Post by Shippou on 2009-01-31
Hello again...

Aegisub is a free open-source subbing software. (I am subbing an anime right now.) It is not in the repositories.

Also, I think otherwise activating the restricted drivers, because the last time I enabled it, my monitor won't work (i.e. no display).

Sorry also for the very late reply.

---

### Post by Shippou on 2009-01-31
Btw, this is their main site: [http://www.aegisub.net/](http://www.aegisub.net/)

Installation guide: [http://www.malakith.net/aegiwiki/Unix_Instructions](http://www.malakith.net/aegiwiki/Unix_Instructions)

I have Aegisub installed in my Windows XP, but then I would like to stick to Linux as much as possible. :)

---

