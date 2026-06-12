---
title: "partitioning hdd to have separate partition for data"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by tengteng on 2009-06-20
hi everybody,

Im new to linux and i installed xubuntu 9.04 to an 80 gig harddisk using all the disk. xubuntu automatically made a 3 gig partition for swap.  By the way the pc is a pentium 3 866mhz with 640 mb ram.

Please help me make another partition on the hard drive for my files like avi's, mp3's, documents and etc..  I tried a puppy linux live cd and used its gparted app to make a 50 gig partition but afterwards I found out I could not mount the new partition so I deleted the new partition.  I'm thinking I probably made a mistake with the new partition because it would not mount.  I don't understand very much the primary, extended, logical etc partitions yet.  If I try to make a new partition again for my data, how should it be?

Thanks in advance for your suggestions.

---

### Post by k3lt01 on 2009-06-20
/ 10 GB, SWAP 2 GB, /home the rest.

I just do primary partitions, there are alot of for's and against's for each type so I wont go into that here because I haven't made up my mind about it either.

---

### Post by tengteng on 2009-06-20
ok.. but how do I make a /home partition? Will my data be safe there in case xubuntu gets corrupted? I'm thinking of making something like a drive d partition in windows for my xubuntu install then i'll just mount it anytime I need to access my data.  Its possible to do it, right?Thanks! :)

---

### Post by zvacet on 2009-06-20
> Will my data be safe there in case xubuntu gets corrupted?

Yes,that is the reason to make separate home partition.You can follow [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide to make one.

---

### Post by k3lt01 on 2009-06-20
So you want to Dual Boot? Check [this]("https://help.ubuntu.com/community/WindowsDualBoot") out.

NB. Be very sure you back up your data. Things can and do go wrong.

EDIT: I think I may have misunderstood your intentions when you mentioned a drive d:

If you don't want to dual boot just follow [this]("http://www.psychocats.net/ubuntu/separatehome") guide.

---

### Post by tengteng on 2009-06-20
Thanks I'll check out the guides.. I don't want to dual boot I just want to make a separate partition for my data.:) I still got my windows mentality from years of using it hehe.  
In windows I always have a drive d for my data to keep it safe in case of a virus attack or something.. I just want to do the same thing in linux to keep my data safe in case i mess up my OS.. 
Curiosity can be very bad to the OS and i'm a curious person. :)

---

