---
title: "brasero destroyed my dvd+rw"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by heyyy on 2009-08-11
i wanted to erase a dvd+rw(8x) so inserted the disk in the drive
the disk and the data inside were recognized
the i opened brasero disk burner to erase it
after some minutes it gave me a message that it was successfully blanked. 
but after i reinserted the disk ,ubuntu wasnt able to recognize it...
ill probably want to erase other disks in the future and im not very comfortable with this
is there any way to check it out?

---

### Post by Cato2 on 2009-08-11
I have sometimes found that a DVD burner can write discs that it later cannot read.  If you can try reading this disc on another computer that would help determine if it's your Ubuntu PC or the disc that is having the problem.

Also, try K3B on Ubuntu (apt-get install k3b) - it pulls in some KDE stuff but works fine in GNOME.  It's like Brasero only with some more features, and I generally use it instead - it might be able to tell you more or fix the problem.

The media and burner must sometimes be matched carefully - each burner is certified for certain DVD media from specific manufacturers.  Google for DVD media codes and your specific burner model.

Finally - have a look at the /var/log/messages file when you are burning or reading discs, or any Brasero error logs.  These can often tell you quite a bit.

---

### Post by DavePlummer on 2009-08-11
I have seen similar a similar situation after doing a quick erase of a DVD that had been formatted with a UDF file system. A full erase of such discs avoids the problem for me, but obviously takes longer.

---

### Post by LewRockwell on 2009-08-11
with the inexpensive solid-state storage options gaining greater market-share each passing day...

it becomes less desirable and still less cost-effective to use rewritable optical media
(although long-term permanent data storage via CD-R and DVD-R is still a very viable option)

.

---

