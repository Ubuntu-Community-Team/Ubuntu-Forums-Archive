---
title: "Problems with nVIDIA drivers"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by titofernandez on 2009-05-06
Hi!

I have a NV Crush11 (GeForce2 MX Integrated Graphics), but I can't find a compatible driver tu use it with the 9.04 Ubuntu version, so I'm stuck with an 800x600 resolution.

How can I fix this?

Thanx!!

---

### Post by cariboo on 2009-05-06
What have you tried? Did you go to System-->Administration-->Hardware Drivers and install the restricted driver? Have you tried the open source nv driver?

---

### Post by titofernandez on 2009-05-06
I have tried de first option, but it doesn't work correctly.

About the second... I have tried to install the driver, but while doing it an error occurs because it says I'm using an "X server" and that I have to shut it down and then install... but I don't know what it is and how to do it

---

### Post by titofernandez on 2009-05-06
Anyone? 

I really need to get this fixed

---

### Post by freak42 on 2009-05-06
> **titofernandez said:**
> I have tried de first option, but it doesn't work correctly.

About the second... I have tried to install the driver, but while doing it an error occurs because it says I'm using an "X server" and that I have to shut it down and then install... but I don't know what it is and how to do it

Xserver is the software that manages the graphical stuff on your system. to install the nvidia-driver it must be shut-down (you have to do it on a non-x command line (ctrl-alt-2 will switch to such a command line ctrl-alt-7 will switch back to your Xserver (the gui you see now).

there are many tutorials on how to install nvidia-drivers.. best thing is to probably print it out, because you can't really read them while on the command line:
here's one: [http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/)

but there are probably newer/better/whatever ones.. if you search yourself.

hth

---

### Post by freak42 on 2009-05-06
btw. your gpu is really old, it is not supported in the newest nvidia drivers.

you need a 'legacy' driver from nvidia for your card.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by titofernandez on 2009-05-07
I did all those things... but it still doesn`t work... I think I'm going back to Windows

---

### Post by achase79 on 2009-05-07
You don't need to go to windows, just go to Hardy 8.04 LTS  It supports GeForce 2 MX.  That is what I have and what I use.

---

