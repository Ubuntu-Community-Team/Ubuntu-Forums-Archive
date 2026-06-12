---
title: "i386 architecture problem--errors tho not AMD system"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by jweaver28 on 2008-12-07
I'm running Intrepid on a dual boot system with Vista. I downloaded the i386 version of Intrepid (ubuntu 8.10), installed it on a flash drive (where it still shows as i386 architecture) and then on a clean partition. System monitor correctly shows my htpc has having an Intel Pentium D dual core. 

Now I can't install many packages, including skype, because I get an incorrect architecture error message. I did install medibuntu repositories, etc., and the packages download but don't install. The workarounds seem to be for people who have AMD dual core systems. Being a noob, I don't know how to verify that I have only the 32 bit, not 64 bit, Ubuntu version installed (System monitor says linux kernel is 2.6.27-9-generic and GNOME 2.24.1 and Update manager says fully updated). But some of the threads I followed really messed up my sound (no sound) and already forced a reinstall.

I've spent hours on this and am now thoroughly confused, as well as unable to play most multimedia files, etc.

---

### Post by doorknob60 on 2008-12-07
Open a terminal (Applications > Accessories > Terminal) and type this:
```
uname -m
```

What does it say when you type that?

---

