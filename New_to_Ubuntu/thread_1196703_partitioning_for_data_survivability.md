---
title: "partitioning for data survivability"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Repus on 2009-06-25
Historically updating Linux (not just Ubuntu) from version to version has been catastrophic for me. 
I would like to partition off a clean install across multiple drives. 
Drive "A" would be the OS essential directories, those that get modified with upgrades. 
Drive "B" would be the directories that usually are not touched during an upgrade (home, var, possibly usr). 
Unfortunately I am not confident which directories should go to which drive. Can anyone help? 
In short I want to make sure that regardless how bad an upgrade goes, with the exception of explosions and fire (which has happened), my day-to-day data will be safe. 

Thanks

---

### Post by pauna on 2009-06-25
I would put all your personal data under /home in a separate partition.

Nearly everything else is potentially touched by the upgrade process. For example, think of all the programs in the /usr/bin directory...

---

### Post by forger on 2009-06-25
> **Repus said:**
> 
In short I want to make sure that regardless how bad an upgrade goes, with the exception of explosions and fire (which has happened), my day-to-day data will be safe. 

Thanks

So you need a **backup tool**, like... [luckybackup]("http://luckybackup.sf.net") ?

The best way to have safe data is:
1. Use drive "A" for all your partitions
2. Use the drive "B" as a backup for the partitions you need
3. Take it to a safe place each time
4. Buy a drive "C" for easier exchange and regular backups

---

### Post by Repus on 2009-06-25
> **forger said:**
> So you need a **backup tool**, like... [luckybackup]("http://luckybackup.sf.net") ?

The best way to have safe data is:
1. Use drive "A" for all your partitions
2. Use the drive "B" as a backup for the partitions you need
3. Take it to a safe place each time
4. Buy a drive "C" for easier exchange and regular backups

I do back up on and off site, and mirror. Inevitably however when I upgrade things go bad. I mean really bad. Comically so at times. Thanks for the link though.

---

### Post by Repus on 2009-06-25
> **pauna said:**
> I would put all your personal data under /home in a separate partition.

Nearly everything else is potentially touched by the upgrade process. For example, think of all the programs in the /usr/bin directory...

thanks

---

### Post by Mark Phelps on 2009-06-25
> **Repus said:**
> I do back up on and off site, and mirror. Inevitably however when I upgrade things go bad. I mean really bad. Comically so at times. Thanks for the link though.

If you're talking about Ubuntu "version" upgrades, I've experienced the same kind of problems, and I have so many customizations in place that it's virtually impossible to keep track of all of them.

So, my "solution" to that problem is to partition my drivers so that I have two working versions of Ubuntu -- the most current and the previous.  When a new version comes out, instead of doing an upgrade, I wipe the oldest version and install the current version into the same partitions.

Then, since I not only still have a working Ubuntu version to use day-to-day, I also have all my config settings and files intact, I can take my time customizing the new version.  When I have it all working, I switch GRUB to boot from the new version from then on.

I know this sounds like a lot of work, but it has saved me again and again when an upgrade resulted in major problems.

---

### Post by aeiah on 2009-06-25
if you've got the spare space, then create a whole disk image of ubuntu before upgrading to a newer version, so you can easily revert. you can do with with the dd command and then restore an exact copy back in place if all goes wrong. this isnt a backup solution though of course, more a restore point for a major system upgrade.

---

### Post by Repus on 2009-08-14
In case anyone is interested I just backed everything up and started from scratch. It's not what I wanted to do but I figured in the long run it was easier to plan it all out rather then do partition gymnastics.

thanks for the suggestions though i did consider them all for a good while

---

### Post by mapes12 on 2009-08-14
> **aeiah said:**
> if you've got the spare space, then create a whole disk image of ubuntu before upgrading to a newer version, so you can easily revert. you can do with with the dd command and then restore an exact copy back in place if all goes wrong. this isnt a backup solution though of course, more a restore point for a major system upgrade.I did this a few days ago and it worked without a hitch. In my case I had got my hands on a bigger dive so I put it in my machine and then did this:

To make an exact copy of a drive install the new drive. Then boot from a Live CD like Gparted or anything else where you can get to a Terminal. Go to Terminal and enter:
```
dd if=/dev/sda of=/dev/sdb
```

#where sda is the old drive and sdb is the new drive. Power down then disconnect sda from its IDE channel, connect sdb into sda's IDE channel (thus making it sda). And vice versa for sdb. Make sure any jumpers are changed for Master and Slave (except if your cables and BIOS support Cable select).  Boot from a GParted Live CD again. Format sdb (the old HDD). Reboot, removing the GParted CD and everything will boot from the new HDD. Perfect! 

The exact same simple CL can be used for backups as well as HDD upgrades.

The other backup tool that works for me every time is Partimage. I have "/" and /home on separate partitions (ignoring swap for this post). So, to keep my filesystem safe I make an image of it and save it to a second HDD in my machine. I can then play around with other versions of Ubu inc Installing other derivatives like Kubuntu (which I've just done), then when I want my original configuration back I just restore the image file. Took 7 mins on the last run. Grub and everything runs just as if I hadn't messed around with anything.

For /home I use Grsync and back up to my second HDD but beware the dreaded hidden file .gvfs, Grsync seems to ignore it in the current version but it didn't used to so I put an --exclude in to keep it out otherwise it screws up my restores.

For FF bookmarks add the addon Xmarks and have them backed up on the Xmarks server. Nothing to worry about after that.

Best.

Mark

---

