---
title: "Need guidance to backup"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by aldais on 2010-12-03
Hi,

I would like to ask a few question about data backup.
Is there any ways I can store all the apps as well as ppas, that I have added to my ubuntu installation? 
I am currently dual booting win7 and ubuntu and in about one month I am going to do a clean ubuntu install (no more dual boot), however, there are quite a number of apps and other stuffs like themes that I have installed and configured to my liking.
Is there any way for me to actually reinstall 10.10 and then easily restore all the other apps not shipped with the liveCD, the configurations etc?
Or is there anyways for me to sort of "clone" the partition on which ubuntu is currently sitting on and restore it later?
Or should I just delete win7 partition once I have no more use for it? 

As a side note, ubuntu have been a really enjoyable os for me. With just a 1 gb ram in my netbook, running win7 has not been a smooth business. not too mention all the paranoia with viruses. Thanks for any reply.

---

### Post by asmoore82 on 2010-12-03
I highly recommend Clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

It has a text-based "wizard" interface, but other than that it is the most advanced cloning system on the planet - even capable of capturing and restoring dual-boot setups. Clonezilla is really just the "glue" that holds a slew of open-source tools together, so in a pinch an advanced user can even restore a clonezilla image without using clonezilla.

---

### Post by aldais on 2010-12-03
Hmm. I have heard about this before.
If I havent misheard about it, it is a liveCD software, yeah?
So what do I need to do?
I just need to delete the partition containing windows and then just cut-and-paste the ubuntu partition is it? 
Is it ok to remove the partition known as "System Reserved"?
I believe that this is created with windows.

And one more thing, currently, my ubuntu partition is a part of an extended partition residing with the swap and another partition where i store my files. So, overall I have one partition titled "System reserved", another one with windows installed and one extended partition, comprising of the stuffs i listed above.
Is it ok to just cut-and-paste this ubuntu partition to the empty partition created after deletion of windows?

---

### Post by asmoore82 on 2010-12-03
If all you want to do is delete windows and grow ubuntu to fill the drive,
you can do that with "GParted" on any LiveCD or USB -
preferably a copy of the same version of ubuntu that you use.

You only need clonezilla if you would like to capture a complete backup image of your drive before you make the changes. I highly recommend this approach but you'd need to have another [?external] drive big enough to hold all your data and I know that that's not always available.

---

### Post by aldais on 2010-12-03
Ah, I see. Currently thinking of my options and considering the best one.
I've visited clonezilla's website and it seems to be quite useful in my situation.
How if I want to do a clean reinstall? Is it possible to reinstall ubuntu but with all the apps and configurations of each app on the clean reinstall?

---

### Post by Megaptera on 2010-12-03
I like to make a CD/DVD backup of my setup using Remastersys. Guide here: [http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by aldais on 2010-12-04
Okay thanks dude Megaptera,
I'll look at it soon once I've got time.
I assume I can only copy as much as a dvd can hold?

---

### Post by Megaptera on 2010-12-04
You're welcome and yes it's limited to DVD capacity, but you could always (as you probably do anyway) backup your docs, vids, photos etc to external media.

---

### Post by Quackers on 2010-12-04
It may be worth taking a look at the first post in this thread for another option

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by owiknowi on 2010-12-04
For future fresh installations I highly recommend to create the following partition table (in case of 1 OS):
1. primary partition for /root system
2. linux swap
3. second primary parturition for /home)
 You can use the fore mentioned bootable GParted or PMagic CD's to do so (see [http://distrowatch.com](http://distrowatch.com)).

 Removing all existing partitions in one time can easily be done by choosing the option Create new partition table from the menu bar.

 The - often - hidden system partition is used to restore the default MS OS without a CD/DVD. You can leave it as it is or remove it.

NB: creating a new partition table removes also hidden partitions!

 BTW: I never store sensitive personal data permanently on my computer but rather on an external drive (preferably a HDD or NAS).
 Enjoy!

---

### Post by rewyllys on 2010-12-04
> **owiknowi said:**
> For future fresh installations I highly recommend to create the following partition table (in case of 1 OS):
1. primary partition for /root system
2. linux swap
3. second primary parturition for /home)

I heartily concur in Owiknowi's recommendation of separate partitions for / and for /home (and, of course, for swap).  

With /home on a separate partition, you can do upgrades and reinstallations of your Linux OS without affecting your personal data and settings.  Although a reinstallation of your OS will also require you to reinstall your applications, any settings and customizations of those  applications will have been saved on your /home partition, so that once you have reinstalled an application, it will work just as it did before the reinstallation of the OS.

As to backup, I personally favor LuckyBackup.  I save to an external hard disk, and LuckyBackup makes it easy to run the backup daily at 01:00.

---

### Post by gmenfan83 on 2010-12-04
> **rewyllys said:**
> I heartily concur in Owiknowi's recommendation of separate partitions for / and for /home (and, of course, for swap).  

With /home on a separate partition, you can do upgrades and reinstallations of your Linux OS without affecting your personal data and settings.  Although a reinstallation of your OS will also require you to reinstall your applications, any settings and customizations of those  applications will have been saved on your /home partition, so that once you have reinstalled an application, it will work just as it did before the reinstallation of the OS.

As to backup, I personally favor LuckyBackup.  I save to an external hard disk, and LuckyBackup makes it easy to run the backup daily at 01:00.
so how does this exactly work you just create a home partition and any configurations are auto saved to it?can this home partition be in an extended?

---

### Post by Quackers on 2010-12-04
Yes and yes :-)
When you set up your partitions you set "/" as your mount point for /root and you set /home as your mount point for your new /home partition. Then all your personal files and settings go there.

---

### Post by rewyllys on 2010-12-04
> **gmenfan83 said:**
> . . . . you just create a home partition and any configurations are auto saved to it? can this home partition be in an extended?

Yes, and yes.

---

### Post by gmenfan83 on 2010-12-04
> **rewyllys said:**
> Yes, and yes.
ok cool now is there an easy way to backup your apps so that when you do switch to that home partition yhou dont need to go from memory for the reinstallation process?

---

### Post by Quackers on 2010-12-04
This is an option

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by gmenfan83 on 2010-12-04
when i go into g parted i cant access any of my partitions ...they have the little key icon next to them and i am using root permissions?

---

### Post by rewyllys on 2010-12-04
> **gmenfan83 said:**
> ok cool now is there an easy way to backup your apps so that when you do switch to that home partition yhou dont need to go from memory for the reinstallation process?

I'm not sure I understand your question, so let me respond this way.

Case 1:  When you upgrade to a new version of Ubuntu, your applications will be taken care of as part of the upgrade process.  Hence, you won't have to reinstall them.

Case 2:  When you reinstall an existing version of Ubuntu (or return to an older version), you will, in effect, be making a fresh start with installing that version of Ubuntu--presumably because something went wrong with the existing version.  In this case, you will need to reinstall the applications.  This takes only a few minutes when you use the Synaptic Package Manager and the Ubuntu Software Center.  What I do is keep a list of my applications, which I print out before doing this kind of reinstallation or return to an older version.  (The list is necessary for me because I've learned not to trust my memory.;))

---

### Post by gmenfan83 on 2010-12-04
> **rewyllys said:**
> I'm not sure I understand your question, so let me respond this way.

Case 1:  When you upgrade to a new version of Ubuntu, your applications will be taken care of as part of the upgrade process.  Hence, you won't have to reinstall them.

Case 2:  When you reinstall an existing version of Ubuntu (or return to an older version), you will, in effect, be making a fresh start with installing that version of Ubuntu--presumably because something went wrong with the existing version.  In this case, you will need to reinstall the applications.  This takes only a few minutes when you use the Synaptic Package Manager and the Ubuntu Software Center.  What I do is keep a list of my applications, which I print out before doing this kind of reinstallation or return to an older version.  (The list is necessary for me because I've learned not to trust my memory.;))
ok so the best thing to do is to create a home partition ....configuration etc will get saved there as well ....then when i need to reinstall a version of ubuntu i do it in my home partition and threinstall my apps and the configs will already be there since they were in fact saved in this home partition?.....sorry for the questions i just want to fully understand this

---

### Post by rewyllys on 2010-12-04
> **gmenfan83 said:**
> ok so the best thing to do is to create a home partition ....configuration etc will get saved there as well ....then when i need to reinstall a version of ubuntu i do it in my home partition and threinstall my apps and the configs will already be there since they were in fact saved in this home partition?.....sorry for the questions i just want to fully understand this

You will reinstall the version of Ubuntu in the / partition, viz., the root partition, _not_ in the /home partition.  The point is that having _separate_ partitions for / and for /home makes it possible to change the OS without changing your data and configuration settings.

---

### Post by gmenfan83 on 2010-12-04
> **rewyllys said:**
> You will reinstall the version of Ubuntu in the / partition, viz., the root partition, _not_ in the /home partition.  The point is that having _separate_ partitions for / and for /home makes it possible to change the OS without changing your data and configuration settings.
ok thank you i think i understand this now

---

### Post by rewyllys on 2010-12-04
> **gmenfan83 said:**
> ok thank you i think i understand this now

You're most welcome.  Enjoy using Ubuntu!  I do.:p About all I use MS Windows (in VirtualBox) for these days is to do my income-tax return.

---

### Post by gmenfan83 on 2010-12-04
> **rewyllys said:**
> You're most welcome.  Enjoy using Ubuntu!  I do.:p About all I use MS Windows (in VirtualBox) for these days is to do my income-tax return.
can you access and use windows through virtual box without having a windows partition?i doubt it but its worth asking

---

### Post by cosine352 on 2010-12-04
Have look at the Remastersys. 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

This will allow you make your own live CD with all the installed applications. It is very easy to use.

---

### Post by gmenfan83 on 2010-12-04
> **cosine352 said:**
> Have look at the Remastersys. 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

This will allow you make your own live CD with all the installed applications. It is very easy to use.
i did and got almost done with my backup but it says my file system is too large for the iso so i am going about figuring how to exclude the files to lessen the file system

---

### Post by aldais on 2010-12-04
I am torn between choices now. But thanks for all the input folks. 
I shall take all advices into consideration, as there is still few months until I am ready to kick that windows out of my box.

As a sidenote, how do you create separate home and root folder (was it root?)
What are other advantages of it besides ease of distro upgrade and what are possible issues that may happen?

Thanks and truly sorry for spawning so many questions, I myself am a now user, not too familiar with GNU/Linux os.

---

### Post by owiknowi on 2010-12-05
> **gmenfan83 said:**
> when i go into g parted i cant access any of my partitions ...they have the little key icon next to them and i am using root permissions?

Is this problem already solved?
Just in case: choose Create new partition table from the menu and every partition is deleted.
Now choose the one and only item and create a primary partition and so on.

---

