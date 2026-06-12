---
title: "Help on manual partitions for fresh install"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by natman on 2010-05-01
Hi,
I am about to install 10.04, i have some HD media files that play on my LCD tv via hdmi out that works perfect in windows. What i would like is the following, when i click make manual partitions, i will give
/ around 12g ext4
/home ext4 the rest bar swap
What do i do to add a fat32 section for the /video folder? that i can ready while in windows or linux?
:
So basicall i want a partition for all my media files thats read/write able in both linux and windows.

Thanks:

---

### Post by nitstorm on 2010-05-01
You can wait for a better answer from the pros, but I usually put my media files on a NTFS partition that I either make from Windows' partition manager or GParted. But then it's just me. Better wait until the pros post. Cheers mate :)

---

### Post by clhsharky on 2010-05-01
HI

/swap ram+a tad
/'root'12GB
/home 24GB
the rest '/video' 
or a separate storage partition fat32 or NTFS.

It separates your storage from OS to give some safety to storage if OS crashes or needs reinstalled. And still available to both OSs.

Sharky

---

### Post by clhsharky on 2010-05-01
HI natman

Lucid is not as friendly as Jaunty with Mobile Intel® GMA video chips. Search the forum for lucid and your card and try alive CD first.

Sharky

---

