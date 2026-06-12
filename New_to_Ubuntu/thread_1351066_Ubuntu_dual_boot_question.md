---
title: "Ubuntu dual boot question"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by GOLDN on 2009-12-10
Hello,

I am wondering if it is possible to remove windows while dual booting it with ubuntu. I am running out of disk space and and windows is using  most of that  space.

I have windows xp if that helps.

---

### Post by vallvi on 2009-12-10
You mean, you want to remove windows & only have ubuntu on your machine?
easy:
1. either do a clean install of ubuntu (with a live-cd), indicating it should use all the discspace on your computer (make sure that, before you do this, you backup your home directory & whatever else you want to save)
2. Or you go to system -> administration --> partition editor (or Gparted), you delete all the windows partitions, and then merge them with the ubuntu partition. 

good luck!

---

### Post by oldfred on 2009-12-10
If you have a Wubi install ubuntu is just a program running inside windows. Then you cannot delete windows.

If you have a true dual boot using grub to boot and select which to use then you can delete windows. I generally suggest to convert the space to a new data partition for use by Ubuntu rather than going thru the resize of existing partitions, but you can do either.

---

### Post by ranch hand on 2009-12-10
You may have to rescue grub after removing Win JerryLewis Pro, and it may work fine.  It is not tough.

The idea of backing up your data and reinstalling has some real advantages as you could reformat your whole drive to be more usable bu creating a Primary partition for your / (root) partition (10 to 25Gb depending on the size of your drive) and then making the rest of the drive on Extended partition with the Swap at the end inside it (1Gb is plenty) and the rest you can create what ever Logical partitions you want including just using all of it for /home.

A separate / partition is a good thing to have if you ever run into a problem where you need to reinstall.  You can just format your / partition and not the /home.  It is still a good idea to back up your data, but I have done this a few times and never lost data.

---

