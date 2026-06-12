---
title: "Deleting old OS + Track Pad Skipping Problem"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Unethical on 2009-08-21
Hi there,

I just upgraded to Jaunty, and I'm wondering how to delete my old OS('s).
Also, just after the upgrade, my trackpad starting going funny. I'm using a Dell mini 10v. When I try to drag & drop, it skips. It usually didn't do this as long as I was holding down the mouse button. 

Many thanks,

---

### Post by xPr0star on 2009-08-21
You can delete them with gParted which is a partition editor. You can run 
```
sudo apt-get install gparted
```
in a terminal to get it. It should now be under System>Administration.

---

### Post by wil08son on 2009-08-21
You need to be more specific about deleting your old operating systems. If you just want Jaunty, you can install it over your entire HD.

I'm not sure why your trackpad would be skipping; maybe someone else can help you with that.

---

### Post by Unethical on 2009-08-21
I've opened gParted, but can't tell what is what. D=

---

### Post by xPr0star on 2009-08-21
The white and colored boxes are your partitions. All the writing at the bottom tells information about it like the file system type, size, mount point etc. To delete an oS we would first make sure(if we have more than one hd) that we are on the right HD by looking at the top right will say something like /dev/xXxx(sda, hda, sdb1 etc). We want to find our partition we want to delete right click it and hit unmount. Right click once again for the format to > option and off you go!

---

