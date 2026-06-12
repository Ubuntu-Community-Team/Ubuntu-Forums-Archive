---
title: "Error: no such partition, grub rescue&gt;"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by discoverdean on 2011-08-14
Hi, I'm new to Ubuntu & have the error as stated in the title of this thread.
I'm not sure why or how this could have happened as my laptop was working fine earlier in the day with no boot problems. I switched on to use Sat pm & the error message appeared?!?

I have been reading the solutions in the Ubuntu documentation and have tried to resolve,  the 'Set' command brings back the following: 

prefix=(hd0,msdos7)/boot/grub
root=hd0,msdos7 

but the 'Is' command coming back as an 'Unknown command'. 

So I'm not stuck with how to get my system up & running again.

Pls help.

Thanks

---

### Post by Miljet on 2011-08-14
I believe the command you are looking for is "ls"....that is a small L, not a capitol I. It stands for list.

---

### Post by raja.genupula on 2011-08-14
seems you lost your grub , get it by this . boot your system from  live cd/usb then go for this link .

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by discoverdean on 2011-08-14
Thx, What a silly mistake to make !! the ls command is now working !!

---

### Post by discoverdean on 2011-08-14
Raja,
How do I boot from the error screen?

---

### Post by discoverdean on 2011-08-14
Sorry Raja, I have it now.

---

