---
title: "file recovery"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by philipballew on 2010-01-10
i have a friend who wants me to recover files off there camera card(2 gig xD card). they say they transferd the photos off there camera via usb to there windows computer and the photos are now not on the card(well maybe) and the problem is they didnt make it to her computer. can someone help me try to find the photos on her card?

---

### Post by rbc on 2010-01-10
Try testdisk/photorec. It's in the repos

---

### Post by philipballew on 2010-01-10
how would i go about doing this since its command line only?

---

### Post by PRC09 on 2010-01-10
If using a windows machine you can try the following.It has helped me get files back I thought were gone for good....


[http://dmitrybrant.com/diskdigger](http://dmitrybrant.com/diskdigger)

---

### Post by CallumFR on 2010-01-10
> **philipballew said:**
> how would i go about doing this since its command line only?

It's actually quite simple.  Just open up a terminal and type:

sudo photorec

then enter your password when it requests it.  Identify the camera card in the list and hit enter. Select Intel/PC, then No Partition i.e. whole disk and then "other" for the filesystem and you can then choose where to save the recovered files.

If you want to limit the recovery to certain file types, before you select "no partition" you can press the right arrow button to get into the "file options" menu.  Use space bar to de/select the options :)

Just be careful to check what you're doing and what the program's asking.

---

### Post by albert s on 2010-01-10
there is another prog for windows called undeleteplus that I have used fairly successfully in the past.

---

