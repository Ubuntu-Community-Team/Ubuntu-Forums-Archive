---
title: "amount of space to partition for ubuntu"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by djyoung4 on 2008-12-03
ok I am finally going to install ubuntu 8.10 onto my comp.  I got everything working and I am sick and tired of waiting for the live cd to load.  How much space should I partition for the Ubuntu install.  I was thinking about 10 GB but I think that may be too much.  I have all of my media on my windows partition so i will only need room for Ubuntu and some extra programs that I add on after.

---

### Post by sportscrazed2 on 2008-12-03
id go more than 10gb ubuntu updates frequently

---

### Post by Miljet on 2008-12-03
10 gigs sounds about right. My complete installation takes up 6.4 gigs.

---

### Post by handydan918 on 2008-12-03
Make it as big as you  can. Make a separate /home partition. as you learn, you'll be able to move all your media files to the Ubu system, or just archive them safely off disk somewhere.

---

### Post by nhasian on 2008-12-04
yeah 10 or 12 gigs for the root filesystem /.  then you will need to have a gig or two for the swap partition and if you want to make a /home partition you can make it as big as you want.

---

### Post by maheshjr2000 on 2008-12-04
What windows version are you using? I dont think grub plays nice with vista. Also double check what backup/restore partitions you have. Im pretty sure you can only have 4 real partitions on a hard drive right? Any more have to be logical. 

Oh and I would suggest as big as possible so you could eventually switch over if you wanted to.

---

### Post by wfp on 2008-12-04
Grub should work fine. Dual booting ubuntu64-bit and vista-premium with no problems.

---

### Post by Shwefty on 2008-12-04
My full 8.10 install right now is 9.75 GB, and that's w/ 5.5 GB of music!

Here's my philosophy, and I may get some naysayers.  Whenever a new Ubuntu release comes around, I'm just going to format my ext3 Linux partition, and install Ubuntu on the space where my old 8.10 was.  I do this so I don't have any dependency problems and quite frankly to purge all of the programs I've downloaded and don't use. I back up all of my "useful" data onto a flash drive (or external hd if you have a lot of useful data).

So, my Linux partition is 40 GB (I had the space so figured why not?).  It's one partition only.  This is a BAD IDEA for many users.  It's safer to keep your data folders on separate partitions so that if you have to reinstall Linux, you can keep all of your old files.  But, I don't care about that, and you don't have to worry about running out of room on a partition this way.

Also, rule of thumb is Swap space = 2x RAM memory.  (2 GB RAM, 4 GB Swap).  But, it's only really useful for hibernating.

---

