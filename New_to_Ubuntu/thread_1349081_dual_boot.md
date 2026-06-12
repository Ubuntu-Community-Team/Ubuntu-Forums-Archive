---
title: "dual boot"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-07
How to do i install simply mepis and at the same time keep ubuntu?

---

### Post by The_Pirate_King on 2009-12-07
Step One: 

Install the program GParted using "sudo apt-get gparted" in the terminal. 

Step Two: 

Use GParted to create a "partition".  A partition is a separate part of your hard drive which can run a different OS with a different filesystem. 

Step Three: 

Install your new operating system onto the newly created partition.  Make sure not to overwrite the partition that has Ubuntu on it. 

Should work for any OS.  You may have to tweak GRUB so that you can boot into both of them though.

---

### Post by ranch hand on 2009-12-07
A little more information would be nice (something about your box and what size HDD(s) are on it, how you installed Ubunt).

But, you need to boot to your live CD, do NOT try partitioning from your Ubuntu installation, use the CD.

So boot to the CD (assuming an Ubuntu CD) and go to System>Administration>Gparted (could be Partition Editor) and pull it up.  You will see your drive and how it is partitioned.

If you just turned the Ubuntu installer loose on your drive with the "use the whole drive" option, you should see two partitions.  A large one that takes most of the drive and a small one that is Swap.  the large one is your Ubuntu OS.

You will need to shrink your Ubuntu partition.  It is really best to back up any data before doing this.  It will most likely go with out a hitch, but it is nice to have your data safe.  Burn it to a RW DVD or a few RW CDs or put it on a thumb drive, what ever you prefer.

If you, in gparted, just right click on the partition in the graphic display you will get a menu.  If the partition is mounted there won't be much you can do except click on "unmount".  Do that.  Then right click on the partition again and click on resize/move.

This will give you another graphic display of just that partition which is mavable from either end.  Move the RIGHT end to the left.  Your data will be in the left end of the partition and you do not want to touch it.  You will be able to see, listed below the graphics on the main gparted page what is used in the partition.  Leave it plenty of room for data you may add or new apps, etc.

When you have set the size hit "apply" and sit back and let gparted do its work.  This will take a while.  This is good.

When that is done you will have an empty space on your drive.  You have 2 choices here.  You can leave it "unused" or you can make it into a partition.

I am not familiar with the Mepis installer.  Only had it on my box once and do not remember.

If it has the option to install on the largest unused area you can use that if you leave the area blank.

I think the safest way is to use what ever their "manual" or "advanced" option is.  If you use it  you should have a pre-made partition and make sure that is the only partition their installer is going to use.  It is good to make sure by checking what it wants to do with you Ubuntu partition.

A lot of other Linux distros, besides Ubuntu (which plays nice with others), assume if MS isn't on the drive they can use every thing on there.

Multi booting is a lot of fun.  I have 8 distros on my test drive.  During the 9.10 testing phase I ended up with 18.  I have 4 on my main (320Gb) drive.

Take your time and don't do anything you do not understand.  You can abort install and ask questions and start over.

It is important to remember to breath and have FUN.

---

