---
title: "CD/DVD burnt in Ubuntu will not be read on Vista !"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by meghal on 2010-10-20
Hello Friends,

I burnt a DVD of important documents in Ubuntu with Brasero maker.
Now I have removed Ubuntu completely and using just Vista.

But I can't read any of the DVDs that were burnt with Ubuntu when I use Vista.

So I am not sure what should I do now? Any chances I would be able to see those DVDs in Vista now? 
Please suggest something and help.

Thanks,
regards,
Meghal

---

### Post by yahalimu on 2010-10-20
Hi, I also have the same problem, this time with Windows7.

Before I get chastised, I was only trying to load some data onto a friends windoze setup, I have long since formatted over my win partition.!

All seemed to burn but failed on the checksum..

---

### Post by mastablasta on 2010-10-20
> **meghal said:**
>  
I burnt a DVD of important documents in Ubuntu with Brasero maker.

 
 
did you mount the DVD in Ubuntu and checked if documents are actually burned on the DVD? i am asking because there were some thread where Brasero didn't burn the stuff on the disk.

---

### Post by utilitytrack on 2010-10-20
> **meghal said:**
> Hello Friends,

I burnt a DVD of important documents in Ubuntu with Brasero maker.

Try use k3b instead:

```
$ sudo apt-get install k3b

```

---

### Post by NightwishFan on 2010-10-20
> **yahalimu said:**
> Hi, I also have the same problem, this time with Windows7.

Before I get chastised, I was only trying to load some data onto a friends windoze setup, I have long since formatted over my win partition.!

All seemed to burn but failed on the checksum..

It is ok to use Windows! :) Not use if 'use k3b' is the best solution however it might work for you. Does the data show up in either system? Also try to burn at a slower speed.

---

