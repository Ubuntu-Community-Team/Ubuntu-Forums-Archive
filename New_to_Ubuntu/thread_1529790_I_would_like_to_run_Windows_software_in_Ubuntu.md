---
title: "I would like to run Windows software in Ubuntu"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by RM33 on 2010-07-12
I am using Ubuntu 9.04.

I wanted to know, can I run Windows software like computer games and .Net from within Ubuntu?

If so, what do I need to do to make this happen?

---

### Post by Mr. Gnome on 2010-07-12
You'll need Wine ( Win32 ) and Mono ( .NET ).

---

### Post by roger_1960 on 2010-07-12
Hi

Basically, no you cannot.  Linux and Ubuntu does not run windows software - .exe files.  BUT, have a look at [www.winehq.org](www.winehq.org) - wine is a package which allows some windows programs to run on linux machines.  An alternative is to set up a virtual machine whereby you can install windows inside linux and then run windows programs.  Have a look at [www.virtualbox.org](www.virtualbox.org)

---

### Post by Paqman on 2010-07-12
You can run *some* Windows apps, with *some* degree of success. This is done through a compatibility layer called Wine.

If you want to try out some Windows games under Wine, the best way is to install Play on Linux, which is a front end for Wine. It has a list of games which it can install and run really well. Installing other Windows software without using Play on Linux is possible, but very hit and miss. You can check the [Wine App DB]("http://appdb.winehq.org/") to see how well any particular Windows app runs under Wine.

---

### Post by Paqman on 2010-07-12
> **roger_1960 said:**
> An alternative is to set up a virtual machine whereby you can install windows inside linux and then run windows programs.  Have a look at [www.virtualbox.org](www.virtualbox.org)

Just one point: virtual machines created in Virtualbox won't be able to do 3D graphics, so it's not a great option for gaming.

---

### Post by WRDN on 2010-07-12
> **Paqman said:**
> Just one point: virtual machines created in Virtualbox won't be able to do 3D graphics, so it's not a great option for gaming.

VirtualBox has experimental 3D acceleration (OpenGL and DirectX 8/9). This will attempt to use the host GPU rather than emulating it.

For more info: [http://www.virtualbox.org/manual/ch04.html#id2623021](http://www.virtualbox.org/manual/ch04.html#id2623021)

---

### Post by wrix on 2010-07-12
You can have a look at [http://www.codeweavers.com]("http://www.codeweavers.com") and [http://www.cedega.com]("http://www.cedega.com")

---

### Post by Paqman on 2010-07-13
> **WRDN said:**
> VirtualBox has experimental 3D acceleration (OpenGL and DirectX 8/9). This will attempt to use the host GPU rather than emulating it.


Sure, it just doesn't really work very well. You're not going to get anywhere near enough performance for 3D gaming.

---

### Post by 3rdalbum on 2010-07-13
> **paqman said:**
> sure, it just doesn't really work very well. You're not going to get anywhere near enough performance for 3d gaming.

+1.

---

