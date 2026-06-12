---
title: "Hard Drive Won't  Mount After Power Surge"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by mkw87 on 2009-12-26
I have a non-root drive in my linux box that has been showing errors since the computer was surged (wife plugged sweeper into surge protector, for what reason I don't know, but it surged the power and rebooted the computer).

Anyways, the drive mounted fine for a while but now it won't mount at all.  I cannot check it with fsck bc it says it's mounted, but it is not.  I have tried unmounting it but it says it's not mounted.....any suggestions?

I checked the drive with gsmartcontrol and it says it's healthy.

---

### Post by taurus on 2009-12-26
What filesystem is that drive?  You can always run the fsck from the LiveCD.

---

### Post by mkw87 on 2009-12-26
> **taurus said:**
> What filesystem is that drive?  You can always run the fsck from the LiveCD.

It is ext3.  So you are saying boot with liveCD then fsck it?  I'll give it a try.  Any suggestion as to what conditions to apply to the fsck?

---

### Post by lukeiamyourfather on 2009-12-27
S.M.A.R.T. isn't all that smart. Drives can be totally messed up and it'll still say they are fine. Try it in another system and see if that works, or a live CD. If that doesn't work try reformatting the drive. Other than that its possible the disk is actually damaged and will need replacing. Hopefully its backed up!

---

### Post by mkw87 on 2009-12-27
> **lukeiamyourfather said:**
> S.M.A.R.T. isn't all that smart. Drives can be totally messed up and it'll still say they are fine. Try it in another system and see if that works, or a live CD. If that doesn't work try reformatting the drive. Other than that its possible the disk is actually damaged and will need replacing. Hopefully its backed up!

The most important stuff is backed up, pictures of my daughter and wedding, but a lot of my other pictures are not.  Hope I get it fixed here.  It's a shame really, I was planning on replacing the drive soon with a larger one.  

For anyone wondering I managed to use a recovery mode from grub to get to a console where I got fsck working before it mounted the drive.  The drive is 500 gb, any idea how long this should take?  It's been on pass one for about 10 minutes but does not give a status update (I am assuming because it's just a bare console).

---

### Post by lukeiamyourfather on 2009-12-27
> **mkw87 said:**
> The most important stuff is backed up, pictures of my daughter and wedding, but a lot of my other pictures are not.  Hope I get it fixed here.  It's a shame really, I was planning on replacing the drive soon with a larger one.  

For anyone wondering I managed to use a recovery mode from grub to get to a console where I got fsck working before it mounted the drive.  The drive is 500 gb, any idea how long this should take?  It's been on pass one for about 10 minutes but does not give a status update (I am assuming because it's just a bare console).

I would say an hour in a worst case scenario. Usually it takes just a few minutes. Cheers!

---

### Post by mkw87 on 2009-12-27
> **lukeiamyourfather said:**
> I would say an hour in a worst case scenario. Usually it takes just a few minutes. Cheers!

It took about 40-50 minutes, repaired it successfully.  I'm going to replace the drive.  Appreciate the input, thanks.

---

