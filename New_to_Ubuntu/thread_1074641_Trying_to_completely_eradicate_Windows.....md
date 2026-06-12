---
title: "Trying to completely eradicate Windows...."
date: 2009-02-19
forum: New to Ubuntu
---

### Post by dch528 on 2009-02-19
So I'm completely new to Ubuntu, but loading it up and playing around with it has sealed the deal, making me despise Windows even more for its inferiority. Well, I just downloaded Gnome Partition Editor, and am trying to remove all the Windows components for good. In some instructions I was told to delete /dev/sda partition and create a new one with the freed up space. Will this screw up my Ubuntu OS, or just wipe all the useless windows crap?

Furthermore, when loading Ubuntu, an "activating swapfile swap" line shows up in the black screen and it takes Ubuntu forever to load up, sometimes hours. This can only be solved by ctrl+alt+del, and then it runs fine. Just a nuisance...

If anyone can help with the partition or boot problem, please respond! Thanks!

---

### Post by LowSky on 2009-02-19
yeah just delete the partition and create it as a new partiiton in what ever format you like.

---

### Post by Therion on 2009-02-19
So you're dual-booting and now you want to delete the Windows partition and give that space to your Ubuntu install?

Here's the basic drill:

Boot with your gParted CD.
Click once on the Windows partition to select it.
Right-click on the Windows partition and select "Remove" or "Delete" whatever it is.
Apply the changes.
Now click on the / partition of your Ubuntu install (it'll be the larger portion of your two Ubuntu partitions) and resize it, using the slider if necessary, to use the now "unpartitioned" space on your hard drive.
Apply the changes.
Wait for gParted to do it's groove thaaaaang and reboot.

And just so we're absolutely clear: these steps will *totally and irevocably* WIPE OUT your exisiting Windows install.

---

### Post by dch528 on 2009-02-19
Yeah this seems like it will work, but when i look at the available partitons, only one shows up (the one labeled /dev/sda). It is an ntfs, and seems to have all my stuff on it, windows and ubuntu included.  It does separate into two partitions or anything, so i am skeptical. Is there an alternate way to delete windows, or should I just delete this?

---

### Post by nothingspecial on 2009-02-19
I`m not too sure on this because I don`t dual boot, but please, please, please backup everything you want to keep before you do anything. I`ve seen this end in tears so many times.

Look at my sig. Linux doesn`t have an undo command.

---

### Post by Therion on 2009-02-19
It depends.  Are you willing to do a fresh install of Ubuntu?  It's what I would *suggest* you do, but that's me.  I'd back up my data and just do a complete and total fresh install because that's really how I prefer to do things.  That process will, obviously, totally wipe out Windows.  

If you want to try and salvage your *current* Ubuntu install, and simply resize your partitions, I'm going to have to let someone else walk you through that.  I'm stuck behind a WinXP machine at my office right now so I don't want to try to guide you through this myself.

---

### Post by dch528 on 2009-02-19
Thanks for the help guys! I'm not to sure about what to do, and I didnt boot this from a cd, I got Ubuntu from the site, so reinstalling after a complete wipe might be difficult unless i get a boot cd. And since I dont have any files that I need on this comp since windows sucks and crashed (deleting all my stuff), i have no qualms about doing this fresh, it would just be inconvenient.

---

### Post by hatten on 2009-02-19
If you installed it inside windows with wubi, as i think you have done as you are saying you only have one partition the only thing that can be done is to reinstall.

Be sure to backup every thing important (and more) at least two times for very critical things. CD's can fail you pretty easily!

EDIT: reread your post, it is pretty easy to burn your own CD and install from scratch. Just find a decent burner than can burn images (windows cannot by default)

---

### Post by jerome1232 on 2009-02-19
> **dch528 said:**
> Yeah this seems like it will work, but when i look at the available partitons, only one shows up (the one labeled /dev/sda). It is an ntfs, and seems to have all my stuff on it, windows and ubuntu included.  It does separate into two partitions or anything, so i am skeptical. Is there an alternate way to delete windows, or should I just delete this?

That really sounds like you installed using wubi, if you did that then your going to have to migrate out the virtual partition to a real partition, then delete your Windows partition and then install grub to the mbr. 

This will be a bit more difficult than if you were using a true dual boot.

The Wubi Wiki has steps on how to accomplish this though. [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by nothingspecial on 2009-02-19
Installing ubuntu isn`t incovenient. If you are going to do aq full install it takes about 15-20 mins plus about 20 mins for your updates depending on your internet speed.
Just make sure you back everything up.

---

### Post by dch528 on 2009-02-19
yeah, i did use wubi, sorry i didn't mention that. Well I hope this virtual partion thing works, thanks alot. I'll post again if I have more annoying newbie problems.

---

### Post by arpanaut on 2009-02-19
Hang on there just a second...
If you have just one partition showing, and you didn't burn an installation CD. then I would venture to guess that you installed Ubuntu using WUBI. 

Therefore Ubuntu is installed in windows as a program, so if you manage to delete the ntfs partition then you will lose everything, windows AND Ubuntu.

So to remove windows and get to your stated goal, you will need to Download the iso and burn it as an image (and check integrity of the burn) BEFORE you go wiping your partition. 

Then you can boot from the installation CD and select Install then select "use the whole disk" and have it complete the install.

If you have other questions post back here and many will be able to help.

(sorry I type too slow) aso a complete/new install may improve your boot time issues

---

### Post by dch528 on 2009-02-19
Haha, i just realized that i am dumb. There are two partitions, /dev/sdb, and /dev/sda. So should i just get rid of /dev/sda (the one with windows) ? The /dev/sdb, the one i suspect has ubuntu on it, is "unallocated", and seems to be the one I want according to the amount of space used on it etc.

---

### Post by Therion on 2009-02-19
> **dch528 said:**
> Haha, i just realized that i am dumb. There are two partitions, /dev/sdb, and /dev/sda. So should i just get rid of /dev/sda (the one with windows) ? The /dev/sdb, the one i suspect has ubuntu on it, is "unallocated", and seems to be the one I want according to the amount of space used on it etc.
Take my advice:  Download an Ubuntu LiveCD and perform a clean install.  Seriously.  
Voice of Experience talking here.  Do it the right way, do it once.



/freaking hates Wubi

---

### Post by lkraemer on 2009-02-20
Ditto on what Therion says.....

I have other suggestions for you. Why not export all your Favorites
to a file that you can later view so you don't loose all of your favorite
URL's.  And if there is any specific Windows Software you can't live without, go have a look the Wine site and see if Wine will support that
software,or look at Codeweavers and see if Crossover supports it too!.
If those fail [www.VirtualBox.org](www.VirtualBox.org) has software that will allow installing
VirtualBox as a Guest OS that will run XP.  Then you can install the
specific software and continue to run it.

lkraemer

---

### Post by dch528 on 2009-02-21
> **Therion said:**
> It depends.  Are you willing to do a fresh install of Ubuntu?  It's what I would *suggest* you do, but that's me.  I'd back up my data and just do a complete and total fresh install because that's really how I prefer to do things.  That process will, obviously, totally wipe out Windows.  

If you want to try and salvage your *current* Ubuntu install, and simply resize your partitions, I'm going to have to let someone else walk you through that.  I'm stuck behind a WinXP machine at my office right now so I don't want to try to guide you through this myself.


It seems like trying to salvage the current Ubuntu install would be trivial and pointless, so I am going to do a fresh install, and overwrite Windows

Hopefully, this will take out the XP and Ubuntu installed. So do I just run the disk from start-up and go through the motions? How do I make sure that it is not installed on a separate partition or a virtual one?

---

### Post by hatten on 2009-02-21
> **dch528 said:**
> It seems like trying to salvage the current Ubuntu install would be trivial and pointless, so I am going to do a fresh install, and overwrite Windows

Hopefully, this will take out the XP and Ubuntu installed. So do I just run the disk from start-up and go through the motions? How do I make sure that it is not installed on a separate partition or a virtual one?

you are correct, and ubuntu will help you with partitioning, ubuntu is nice to new users :)

---

