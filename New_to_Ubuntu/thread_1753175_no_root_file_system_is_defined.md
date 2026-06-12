---
title: "no root file system is defined"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-05-08
[FONT=Courier New]I installed unetbootin and ubuntu on usb yesterday.  i use HP mini.

I clicked ubuntu installation icon on screen, and followed steps.
"No root file system is defined.  correct this from partition menu." was on step 5 of 8.

I have no clue.
do u know this?
[/FONT]

---

### Post by wolfen69 on 2011-05-08
Are you going to be using the whole drive for ubuntu?

---

### Post by Matrix01 on 2011-05-08
i want to save window 7 starter,,,
so  I clicked Specify partition manually...
list of somethings goes like this; dev/sda1...2, 3, 4

what to do next????

---

### Post by Quackers on 2011-05-08
It's possible on a Dell machine that you already have the maximum number of primary partitions (4) on your hard drive. You need to check that before you install any other operating system.
To create a 5th partition will have serious consequences!
I would recommend that you quit the installer and go to the live desktop and post a screenshot of the gparted screen (System > Admin > gparted).

---

### Post by Prince Valiant on 2011-05-08
I've hit this same problem.  Thing is, you gotta choose 
```
/
```
as the mount point.

Go back to the partition step.  

-Val

---

