---
title: "My resolution is messed up!!!"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-24
Yes,my resolution is kinda whacked out,,it wont go past a certain level,and it used to be fine a while ago,i cant remember exactly what i was doing that caused it but i cant fix it now,,its enabled in the hardware drivers setting, im using hardy heron and runing on an nvidia geforce 7 series card..please help!!

---

### Post by cmnorton on 2009-02-14
First, find out what resolutions both your graphics chip and monitor support.

It sounds like you need to boot into recovery mode, enter

dpkg-reconfigure xserver-xorg

and add other resolutions there.

Take all other answers as default.

You might not be doing this all as one shot. It might take a few tries. It did when I needed to get my Thinkpad T61p working in a KVM environment.

---

