---
title: "Making an image"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Doug11 on 2009-02-06
I now have my Hardy Heron LTS the way I want it. Is there a way I can make an image of this,,burn it to a cd or dvd,,reformat my HD and get rid of my MS partitions and reinstall my Hardy with the disc I made and have it the way it was?

---

### Post by Hospadar on 2009-02-06
It is possible to export what packages you have installed and whatnot, you'd probably loose some configuration, among other things.

If you just want to wipe out windows, you can use gparted of any livecd to change your partitions (i.e. delete your windows partition and resize your linux partition to fill the free space).

---

### Post by hyper_ch on 2009-02-06
have a look at partimage

---

### Post by Paqman on 2009-02-06
If all you're looking at doing is deleting your Windows partitions you don't technically need to take an image. Just delete the partitions in Gparted and resize your Ubuntu ones to take up the space.

However, when you're messing about with partitions it's a good idea to take a backup anyway. As mentioned, partimage will do the job. You can get a Clonezilla-Gparted LiveCD if you want a one-stop-shop.

---

### Post by stchman on 2009-02-06
> **Doug11 said:**
> I now have my Hardy Heron LTS the way I want it. Is there a way I can make an image of this,,burn it to a cd or dvd,,reformat my HD and get rid of my MS partitions and reinstall my Hardy with the disc I made and have it the way it was?

I think AptonCD will do what you want.

---

### Post by Doug11 on 2009-02-06
> **Paqman said:**
> If all you're looking at doing is deleting your Windows partitions you don't technically need to take an image. Just delete the partitions in Gparted and resize your Ubuntu ones to take up the space.

However, when you're messing about with partitions it's a good idea to take a backup anyway. As mentioned, partimage will do the job. You can get a Clonezilla-Gparted LiveCD if you want a one-stop-shop.
Thanks,,I do have a GParted CD which i was thinking of using. But liek you say, a back up is always nice to have.

---

### Post by Michael Dooley on 2009-02-06
> **Doug11 said:**
> I now have my Hardy Heron LTS the way I want it. Is there a way I can make an image of this,,burn it to a cd or dvd,,reformat my HD and get rid of my MS partitions and reinstall my Hardy with the disc I made and have it the way it was?

You might take a look at [Remastersys]("http://www.remastersys.klikit-linux.com/"). It can make a full system back-up or a distributable copy of your set-up for friends.

---

### Post by Doug11 on 2009-02-06
> **Michael Dooley said:**
> You might take a look at [Remastersys]("http://www.remastersys.klikit-linux.com/"). It can make a full system back-up or a distributable copy of your set-up for friends.
Ok, i tried the remastersys and it seemed to work pretty decent. The only snag i run inot was the image it created was just over 700mb's. What should I try to get it down to under 700 so it will fit on a cd. I realize i will have to make another image.

---

### Post by Paqman on 2009-02-07
> **Doug11 said:**
> Ok, i tried the remastersys and it seemed to work pretty decent. The only snag i run inot was the image it created was just over 700mb's. What should I try to get it down to under 700 so it will fit on a cd. I realize i will have to make another image.

You'll have to either uninstall some packages or compress the image. I believe Open Office takes up a pretty big chunk of disk space, and if you leave your home folder intact you'll keep your settings untouched. Just reinstall OO on the new system and you're good to go.

---

