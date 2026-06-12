---
title: "New installation"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by pauligit on 2009-01-08
Hi everybody! I've been out of the GNU/Linux world for almost 5 years. I turned to W XP when I entered college. (I'm majoring in humanities and I realized that I had little time to spend a whole day trying to deal with dependencies and compilating software.) However, I've just tried Ubuntu 8.10 Desktop edition's live cd (the 64-bit version) and it surprised me how easily it detected all my hardware and the number of packages ready for installation.
My Windows system has just got infected with a virus and I think I will have to install it all over again. So, that's a great chance to create a new partition and install Ubuntu there.

My questions are:

1) Can it be installed in a primary partition _after_ the 1024 cylinder? Should I use the 1st primary partition for Windows or that doesn't make any difference?

2) I've got a 120 Gb HD, and a 30 Gb one (I use the second one for back up purposes; it's 7 years old and that's where I installed SuSE and then Slackware back in 2002, but it works seemingly well.). I'm gonna set some primary partition of the first HD to be Ubuntu's '/'. I intend to use XP just to run basic Desktop applications for my academic work, and to run specific software due to compatibility issues. Ubuntu will be used to run most of my Internet applications (e.g. p2p software, IM services, Firefox) and to watch videos. How much space should I reserve for it?

3) a) Since I have to install both OS's from scratch, is it recommended to install Ubuntu after Windows or before it? I suppose that if the installation software recognizes the Windows partition just fine, and then properly adds a label to GRUB's config file to boot it by itself, Windows should be installed before Ubuntu...
b) Is it a good idea to backup the first disk's MBR to have a copy of Windows' loader just in case?

4) I've 1-Gb RAM memory. Should SWAP be of an equal size? (The double of it seems to me a lot. I might add more SWAP partitions to fstab if I feel I need it)

Cheers,

Pauligit

---

### Post by blueridgedog on 2009-01-08
1 - Any primary will work
2 - 30 gig plus should be fine, but if you spread things around evenly, you will have a lot more for Ubuntu
3 - I like Windows first then Ubuntu
4 - equal will be fine (in my opinion)

Good luck and welcome back

---

### Post by cozmicharlie on 2009-01-08
Welcome back - I think you will find Linux has improved considerably since you last gave it a shot.  I would agree with everything blueridgedog wrote.  This web site has some great tutorials on partitioning that should help:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Iowan on 2009-01-08
No argument from here on previous suggestions.  Unless something has changed, Windows seems to think it's the only OS worth having, so it overwrites GRUB.  Ubuntu is a bit more polite, and will (usually) try to coexist with other OS's (even Windows :) )

---

### Post by pauligit on 2009-01-08
Hey, I forgot to ask, which filesystem would be the best? Back in 2002, I installed SuSE which came by default with reiserfs. It had a great performance, and I also took the chance to resize the filesystem without problems (resize_reiser or something like that.) But I've read that Hans Reiser is now convicted... Which fs does Ubuntu allow for / during installation? (Note: most of my files will be small ones. I don't edit video nor anything like that.)
Cheers,
PIC

---

### Post by perlluver on 2009-01-08
> **pauligit said:**
> Hey, I forgot to ask, which filesystem would be the best? Back in 2002, I installed SuSE which came by default with reiserfs. It had a great performance, and I also took the chance to resize the filesystem without problems (resize_reiser or something like that.) But I've read that Hans Reiser is now convicted... Which fs does Ubuntu allow for / during installation? (Note: most of my files will be small ones. I don't edit video nor anything like that.)
Cheers,
PIC

Reiser is still around, Ubuntu selects ext3 as the default file system for /, but you can change it to anything you like.  Ext3 and Ext2 are available, as well as reiser and JFS, the choice is yours.

---

### Post by pauligit on 2009-01-08
And what's your prospect for reiserfs?

---

### Post by perlluver on 2009-01-08
I have used it, but nothing to write home about.  I use Ext3 on my main Desktop, and on my server I use JFS.  ReiserFS was at the last I heard working on reiser4, but I don't know if that will be around now.  Ext is also working on a newer system.  

Ext3 does pretty well, reiser was a little slow booting, but other than that pretty decent.

---

### Post by handydan918 on 2009-01-08
I use ext3 pretty much exclusively, FWIW.

Also, recommend installing windows first, to first partition of first hard drive. Ubu anywhere else, and install grub to mbr. Separate /home partition is best, and yo may want to consider running 8.04, as it is the LTS version.

Easy. 

Welcome back to the REAL world.

:popcorn:

---

### Post by pauligit on 2009-01-09
Thanx you all for your replies...

I'm running a 64-bit live version of Ubu 8.04. Is the 64-bit one stable? I have an Athlon-64 micro.

Cheers,

PIC

---

### Post by blueridgedog on 2009-01-09
Well...if you want to get fancy, I usually put windows on first and have a second drive that I use a file system that the two OSs have in common that becomes a common document/file share.

In windows, I repoint "my documents" to this drive and in Ubuntu, I repoint the symbolic lings in /home/myuser/there with things like:

rm -rf /home/myuser/Music
ln -s /documents/Music /home/myuser/Music

(etc for each file...not certain of the syntax as I am at work now).

The end result is that Nautilus is happy and links to my files nicely.

The end result is this spare drive becomes the only thing that I need to worry about and since I back it up, I periodically backup my home directory and any files I tweak in /etc

---

### Post by pauligit on 2009-01-09
Good piece of advice. I used to do the same. So fat32 should be fine, right?

I think I should now backup some of my old My Documents files. Does Ubu live come with a good DVD burner like Nero?

Cheers,

Pauligit

---

### Post by clive littlewood on 2009-01-09
Hi

For burning cd's use Brasero  Apps > sound & Video >brasero

Or I always use K3b which you get from the repo's

Hope that helps      :D

Clive

---

### Post by pauligit on 2009-01-09
I'm thinking of something I can run under the live version. It would be best not to do the backing up under my virus infected Windows.

---

### Post by sadaruwan12 on 2009-01-09
Hi,
It's not necessary to run 64bit OS on a 64bit CPU I also use 64bit processor but I use Ubutnu i386 or a 32bit version if you're planing to go over 3GB of RAM then install 64bit other wise it's ok to use an 32bit one.

---

### Post by sadaruwan12 on 2009-01-09
use brasario

---

### Post by matey3 on 2009-01-09
My friend had viruses in his windows machine and what I did was I booted it in safe mode with networking, then I went to google and searched for free online virus removal, a page (I think Panda A/V?) came up and I took it, ran it , it took more than 2 hours but caught over 240 infected files, and fixed his laptop!

So you dont have to run msconfig to get rid of stuff in the start-up/ services. they always come back any way! :)

---

### Post by blueridgedog on 2009-01-09
> **sadaruwan12 said:**
> use brasario

I think the spelling is "Brasero".

---

