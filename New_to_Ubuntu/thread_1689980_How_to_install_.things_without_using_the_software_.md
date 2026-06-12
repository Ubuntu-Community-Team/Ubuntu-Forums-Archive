---
title: "How to install .things without using the software center"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Gms9810 on 2011-02-17
Hey, all,
I have a utility that I use a lot on Windows that I would like to use on Linux too. I couldn't find it in the software center so I downloaded the .tgz file, but I can't figure out what to do next. The utility is Xnview, I tried Synaptic but I must not have done something right. Should I even be using synaptic?

Edit: after I posted this I figured it out but couldn't delete this post. Thanks anyway

---

### Post by Paqman on 2011-02-17
A .tar.gz is just an archive file, like .zip. It could contain just about anything, depending on how nice the developers have been to you. You can open it up (right click > open here) and have a look to see what's inside. If you're lucky there will be some instructions about what you're supposed to do with it.

Ideally the developers would have give you a nice .deb file that you could just download and click on to install, but they've decided to only package for .rpm, which is used on Red Hat based Linux systems (Ubuntu is Debian-based, hence .deb). It is possible to convert an .rpm for use on Ubuntu using a program called [alien]("https://help.ubuntu.com/community/RPM/AlienHowto").

---

### Post by llamabr on 2011-02-17
xnview looks a bit like adobe photoshop.  most of the functionality you want to photoshop you can also get with the gimp, which is probably already installed on your system.

---

### Post by berlinblue on 2011-05-06
> **Gms9810 said:**
> Edit: after I posted this I figured it out but couldn't delete this post. Thanks anyway

Hi Gms9810,

Good to hear you've managed to get it working. 
Could you possibly explain how you installed **XnView on Ubuntu**? 
I still haven't figured it out. Thanks!

---

### Post by RoshJay on 2011-08-15
Paqman was very helpful with his post. So, this is how I did it.

1. Downloaded XnView-static-fc4.i386.rpm from the xnview website.
2. Installed Alien through the software center
3. Then went to the Terminal and typed:
sudo alien -i XnView-static-fc4.i386.rpm
4. Voila! It's installed in Applications > Graphics > XnView

---

