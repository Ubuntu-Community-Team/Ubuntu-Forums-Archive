---
title: "how can I install my web cam"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by klabezo on 2009-05-14
plz help me to install my web cam


it's Creative webcam vista usb

---

### Post by albinootje on 2009-05-14
> **klabezo said:**
> plz help me to install my web cam


it's Creative webcam vista usb

Please post the output of the following (in a terminal, after attaching the usb webcam) :
```

lsusb

```

---

### Post by klabezo on 2009-05-14
thank you

---

### Post by albinootje on 2009-05-14
> **klabezo said:**
> thank you

Without knowing the exact type of webcam, we, the other ubuntuforums.org users, can only guess, or try to help you in a more generic way..

If the Creative Webcam Vista webcam you have is a PD1100, then this (somewhat old) page could be useful :

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

But again, please post the output of this :
```

lsusb

```
and this could also be useful :
```

dmesg | tail

```

---

### Post by libra1780 on 2009-07-02
get the id as said before, then check out if it's in that [_list_]("http://moinejf.free.fr/webcam.html").
with status ok, you just need to load the right module (kernel >2.6.27)
```
#sudo modprobe gspca_XXY
```
where XXY is the subdriver name in the list.
progams using v4l instead of v4l2 have to be started with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <application name>
```
to make it work.

[_Here_]("http://moinejf.free.fr/gspca_README.txt") the instructions if you want to compile yourself the latest version of drivers.

PS: Very important, found out that a lot of cams are not working if connected to a usb hub. Connect it directly to be sure

---

