---
title: "Effective use of hardrives?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Danno2468 on 2010-01-05
I was wondering about hardrives. I have several drives in my pc, 1 80gb devoted just to ubuntu, never gets fuller than 30 gb and then a 320, 500, 750 which store media.  My 750 actually just died early december.  I ran it right full of movies and Tv shows. How bad is it to run a full drive like that?  Did that possible lead to its death?  I know people say when a drive is slow it runs slower because it spends more time searching, but it never ran so slow that it affected the quality of the movies.  Would i have been better off to try and spread the media out better between the 3 drives?  I was also wondering when I plug this broken drive in now, it spins and i can feel the drive working, but it doesn't show up, not even in bios.  I tried plugging it into different ports, and different power cables, but the mobo doesn't see it.  Anything else i can do with it?  I was able to recover most the data from my brother who has a copy in a different city, so i am not spend $$$ to get it proffensionly recovered. 
With boxing day i bought 2 1.5 tb drives my plan is to put all the data that was on the 750 on to 1 of them, and then put all the same date on to the other, and then remove it and put it in a safe place so i have a back up. 
I was wondering how you would arrange the data?

Sorry for all the questions in 1 post, but any help would be welcome :)

---

### Post by warfacegod on 2010-01-05
What file system are you using? Linux generally doesn't do so well with a drive that's ext and over 90% full. But even if yours was 100%, I doubt that being full had any real contribution to it dying. Drives fail, it's just the nature of the beast. Your arrangement seems fine, just make sure you add any new stuff from the use drive to your backup drive periodically.

---

### Post by Paqman on 2010-01-05
The trouble with filling a drive up too much is that it causes harsh fragmentation. That in turn can lead to the drive working too hard, which could contribute to it failing earlier than it should.

So it might well have been a contributing factor, but I wouldn't say the relationship is as simple as full drive = failure. You could run a heavily fragmented drive for years and never have it fail.

Hard drives are pretty unreliable beasts though. Having a plan for protecting your data is a good idea, having that automated is even better. If you can, then off-site backup is good to have too.

---

### Post by pricetech on 2010-01-05
You have 2 1.5 TB drives, presumably identical.  Sounds like a RAID1 to me.  That's what I'd do.

As far as resurrecting the drive; If you have another drive like it, you might try swapping the onboard controller from the good drive to the dead one to see if the computer sees it then.  Just be careful and guard against ESD.  You won't be opening the drive up, but "clean room" conditions wouldn't hurt anyway.

Good luck with it if you decide to attempt it.

---

### Post by cascade9 on 2010-01-05
> **pricetech said:**
> You have 2 1.5 TB drives, presumably identical.  Sounds like a RAID1 to me.  That's what I'd do.

As far as resurrecting the drive; If you have another drive like it, you might try swapping the onboard controller from the good drive to the dead one to see if the computer sees it then.  Just be careful and guard against ESD.  You won't be opening the drive up, but "clean room" conditions wouldn't hurt anyway.

Good luck with it if you decide to attempt it.

Gah! Try the freezer trick before you go swapping controller. 

[http://ubuntuforums.org/showthread.php?t=1362667&highlight=freezer+trick](http://ubuntuforums.org/showthread.php?t=1362667&highlight=freezer+trick)

I wouldnt go RAID1, myself. Its slower and more of a pain than its worth in my case. ESATA backup would be almost as easy as RAID1, and then if there are even any major power issues, you havent lost all your data.

---

### Post by pricetech on 2010-01-05
> **cascade9 said:**
> Gah! Try the freezer trick before you go swapping controller. 



I'd read about the freezer trick but never used it.  It's worth a try too.

---

### Post by Danno2468 on 2010-01-05
Thanks for the imput! I run ubuntu 9.10. i have been with it since 7, a total noob then and this form has been good to me:P I am slowly learning the ways.  The 2 1.5 tb aren't ran in raid, i have 1 in my tower, and the other is in a external encasement.  I suppose i could have ran them in raid, and i would have had 2 copys of the same.  I will try the freezer thing, i have nothing to loose.
Thanks again!

---

