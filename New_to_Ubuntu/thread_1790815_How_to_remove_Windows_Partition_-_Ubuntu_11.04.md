---
title: "How to remove Windows Partition - Ubuntu 11.04?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by scefinos on 2011-06-25
Hello Everyone,

I have installed Ubuntu 11.04 as a partition on a computer running Windows XP. How do i remove Windows from the other partition.

---

### Post by TeoBigusGeekus on 2011-06-25
```
gksu gparted
```
Format the drive.
Don't forget to run
```
sudo update-grub 
```
after you're done.

---

### Post by scefinos on 2011-07-10
Thanx TeoBigusGeekus. I tried the code but it still kept showing I was running out of HD space. I ended up running a full install.

scefinos

---

### Post by arena001 on 2011-07-10
How did you installed Ubuntu? I mean by booting into Ubuntu CD/Flash drive or over xp?

---

### Post by scefinos on 2011-07-10
I installed from the CD. Then upgraded to 11.04 via download.

---

### Post by arena001 on 2011-07-11
Go to ubuntu software Center and install GParted. Then run the GParted. Look for the windows xp partition and delete it/format it what ever you want.(Back up your data before doing that) 

But don't forgot to run ```
sudo update-grub
```

This is the same thing TeoBigusGeekus is telling you.  If you get the error that you are saying running out of HD space then proide more information for the same. A screenshot will defeneatlay help us understand the problem.

---

### Post by Miljet on 2011-07-11
> I ended up running a full install.
So is the problem now solved?

---

