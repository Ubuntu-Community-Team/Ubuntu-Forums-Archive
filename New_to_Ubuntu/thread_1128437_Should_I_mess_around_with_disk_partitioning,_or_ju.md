---
title: "Should I mess around with disk partitioning, or just reinstall Ubuntu?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-17
I want Ubuntu's partition to be larger, and to remove the "recovery" partition from Windows. 

I only installed Ubuntu Studio the other day, and I haven't updated or installed anything yet. It's still a default install. 

Would it be easier to just reinstall Ubuntu and repartition that way?

---

### Post by unutbu on 2009-04-17
Yes, reinstalling will be quicker. In general, resizing partitions is a slow process, while destroying and recreating partitions is a quick process.

---

### Post by Therion on 2009-04-17
If you want Ubuntu to be the *sole OS* on the drive, I would say yes; do a fresh install and just let the installer take care of things.

---

### Post by Tim Sharitt on 2009-04-17
Deleting the Windows recovery partition and expanding the Ubuntu partition should not be too painful of a task if. 

However, if the recovery partition is before the Ubuntu partition, then the partition (and all the files) will need to be moved to fill the space created by removing recovery and this could take quite a while. If that is the case, you may find it easier to reinstall if you don't really have anything to lose on either partition.

---

### Post by Noise... on 2009-04-17
> **Therion said:**
> If you want Ubuntu to be the *sole OS* on the drive, I would say yes; do a fresh install and just let the installer take care of things.

It will still be a dual-boot (unfortunately) with Windows. Until I get Wine, my wireless, and my iPod Touch sorted with Ubuntu, I'm stuck using Windows. I'd much prefer to just wipe the drive and use only Ubuntu, but for the time being, I'll need to keep Windows for gaming and iTunes. 

I'd love to just sort these issue out now, and then reinstall Ubuntu as the sole OS, but because I have Mobile broadband (the only option for internet in my area), Downloading a pile of applications and updates (250MB in Updates alone) more than once is a big deal, as I only have 5GB bandwidth usage a month.

---

### Post by Noise... on 2009-04-17
> **Tim Sharitt said:**
> Deleting the Windows recovery partition and expanding the Ubuntu partition should not be too painful of a task if. 

However, if the recovery partition is before the Ubuntu partition, then the partition (and all the files) will need to be moved to fill the space created by removing recovery and this could take quite a while. If that is the case, you may find it easier to reinstall if you don't really have anything to lose on either partition.

Ah...that would be an issue. The Recovery partition is first - even before the 150GB Windows partition, then the / partition for Ubuntu, followed by the swap partition. 

Maybe it would just be better to stick with my current install, sort the issues I have, and delete Windows all together?

---

### Post by Mark Phelps on 2009-04-17
While I certainly admire your desire to do away with MS Windows, I would wait until you get Wine and the iPod working before you do that.

Wine is not the miracle tool some folks make it out to be.  If you need it because of specific apps, you need to check the CodeWeavers site at the link below and make sure your apps (and versions) get high ratings; otherwise, you won't be able to use them.

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Plus, if you have to do some hacking to get the stuff working right now, when you go to reinstall, you'll have an easier process then because you'll already know what to do.

---

### Post by unutbu on 2009-04-17
Sorry -- my original advice was plain wrong.
If the recovery partition is not adjacent to the Ubuntu partition, you would have to delete the recovery partition, *move* the Windows partition, and then resize the Ubuntu partition. Reinstalling would not enable to you avoid the moving and resizing operations.

I think your idea is better: stick with the installation you have, sort out the wine, networking and ipod issues, and then when you know how to solve those problems, consider reinstalling.

Also, in a few weeks, Jaunty will be coming out, and you may want to try that...

---

### Post by Noise... on 2009-04-17
> **Mark Phelps said:**
> While I certainly admire your desire to do away with MS Windows, I would wait until you get Wine and the iPod working before you do that.

Wine is not the miracle tool some folks make it out to be.  If you need it because of specific apps, you need to check the CodeWeavers site at the link below and make sure your apps (and versions) get high ratings; otherwise, you won't be able to use them.

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Plus, if you have to do some hacking to get the stuff working right now, when you go to reinstall, you'll have an easier process then because you'll already know what to do.

I have checked - The things I'll need to run in Wine are; Steam, Early Half-Life games (HL1, Blue-Shift, CS, etc), Half-life 2, Garry's Mod, and TESIII: Morrowind. All of which work well in Wine - some with small tweaks.

Basically, all I need Wine for is games. I can't think of any Windows-Only programs that I really need it for aside from the games listed above.

---

