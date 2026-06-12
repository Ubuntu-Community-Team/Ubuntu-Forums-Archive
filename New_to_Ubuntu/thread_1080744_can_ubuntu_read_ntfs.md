---
title: "can ubuntu read ntfs"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by chris200x9 on 2009-02-25
Hi I have a friend her computer died she wants to copy some data from the harddrive to her portable harddrive, I was thinking she could use ubuntu livecd (I know I can just use other specialized live cd for this but I want to get her to see a live enviroment in its prime and warm her up to linux) My question is can the livecd of ubuntu 8.10 read ntfs?

---

### Post by taurus on 2009-02-25
Yes.  You just have to mount it first before you can access it.

---

### Post by futileissue on 2009-02-25
I'm pretty sure ntfs is read/writable out of the box with Ubuntu 8.10.

---

### Post by geirha on 2009-02-25
Reading/writing from/to ntfs is supported out of the box, yes. Just select the drive from the Places menu and start dragging and dropping the files. Ubuntu can not do filesystem checks and fix errors on NTFS filesystems though, you'll need windows if that is the case.

BTW, make sure you check in System -> Preferences -> Appearance -> Visual Effects. If it is set to normal (which means compiz is working with the video card), try setting it to extra. Then, make sure to move some windows around so she sees the wobbly windows. People unfamiliar with linux is always impressed by that (by my experience) ;)

---

### Post by trinidadflores on 2009-02-25
is there a way that you can have it mounted permantly?  Like in my situation i have vista on here as my second os so that i can continue to use dreamweaver cs 4 for designing websites although i use software in ubuntu to do the majority of the work.

---

### Post by taurus on 2009-02-25
> **trinidadflores said:**
> is there a way that you can have it mounted permantly?  Like in my situation i have vista on here as my second os so that i can continue to use dreamweaver cs 4 for designing websites although i use software in ubuntu to do the majority of the work.

If you want to mount your ntfs partition while you are running Ubuntu, then install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

