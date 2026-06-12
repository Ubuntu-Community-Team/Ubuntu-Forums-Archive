---
title: "upgraded to grub2"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Norm24 on 2009-01-11
Big mistake and need major help.

I've now upgraded to grub 2 on a dual boot Vista/Ubuntu system.When I restarted everything looked fine except no Vista in the boot menu and no matter what I do or click on I get this error message:

Error 11:Unrecognized Device String.

I had Ubuntu perfect and now I have no computer at all.Please help!

---

### Post by Norm24 on 2009-01-11
Bump.

Not trying to sound impatient but this is really that important.I can't run my life off of the Live CD.

The last thing I want to do is completely remove Ubuntu and start from scratch after I had it perfect.

---

### Post by igknighted on 2009-01-11
please try to be more patient in the future... both with bumping posts after less than a half hour, and with trying experimental software on critical systems.  In the very least, make sure you have a backup plan for when something goes wrong (and assume it will)

See here to reinstall grub via the liveCD: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> please try to be more patient in the future... both with bumping posts after less than a half hour, and with trying experimental software on critical systems.  In the very least, make sure you have a backup plan for when something goes wrong (and assume it will)

See here to reinstall grub via the liveCD: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Impatient that I am but Grub2 is far from experimental.

The link you provided does nothing for me.Doesn't even deal with Ubuntu its so old.

Thanks for the try anyways.

---

### Post by igknighted on 2009-01-11
> **Norm24 said:**
> Impatient that I am but Grub2 is far from experimental.

The link you provided does nothing for me.Doesn't even deal with Ubuntu its so old.

Thanks for the try anyways.

The grub commands are the same, I could have linked to the exact same set of instructions from the Ubuntu wiki, but that would have taken longer to find.

How did you install grub2?  Do you still also have the original grub installed in Ubuntu?

EDIT: From the ubuntu wiki: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Bölvaður on 2009-01-11
Not to sound elitist or anything (as I am soooo far from knowing anything) but could you post your grub's menu.lst ?
and did you back up the previous one that worked so if then new one would fail you could correct the problem?

You probably should also post details on your partitions like "ls -R /dev/disk/"

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> The grub commands are the same, I could have linked to the exact same set of instructions from the Ubuntu wiki, but that would have taken longer to find.

How did you install grub2?  Do you still also have the original grub installed in Ubuntu?

EDIT: From the ubuntu wiki: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I installed Grub2 through synaptic.I'm assuming I still have original Grub installed?

---

### Post by Norm24 on 2009-01-11
> **Bölvaður said:**
> Not to sound elitist or anything (as I am soooo far from knowing anything) but could you post your grub's menu.lst ?
and did you back up the previous one that worked so if then new one would fail you could correct the problem?

You probably should also post details on your partitions like "ls -R /dev/disk/"

Can't get past the grub list.No matter what I click on I end up with error 11.

---

### Post by Bölvaður on 2009-01-11
ok you can do 2 things. use your live cd to retrieve the data (both grub list and the file names under /dev/disk/
or you can use the [super grub disk]("http://www.supergrubdisk.org/")

report if you need further info but I think this should be enough.

---

### Post by igknighted on 2009-01-11
> **Norm24 said:**
> I installed Grub2 through synaptic.I'm assuming I still have original Grub installed?

no, it looks like that removes grub in the process, unfortunately.

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> no, it looks like that removes grub in the process, unfortunately.

So that means complete removal of Ubuntu and start fresh?

---

### Post by adult swim on 2009-01-11
no it means to reinstall grub with a live cd 
the guy linked it earlier.
EDIT igknighted wrote
> From the ubuntu wiki: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
the part you are looking for is


   1. Boot your computer up with Ubuntu CD
   2. Open a terminal window or switch to a tty.
   3.

      Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD.

---

### Post by igknighted on 2009-01-11
you could always install another system, it will automatically set up grub entry for its grub for your current install, which you could then boot to.  You could also do it with a liveCD's grub, if you know grub well.

---

### Post by igknighted on 2009-01-11
> **adult swim said:**
> no it means to reinstall grub with a live cd 
the guy linked it earlier.
EDIT igknighted wrote

the part you are looking for is


   1. Boot your computer up with Ubuntu CD
   2. Open a terminal window or switch to a tty.
   3.

      Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD.

grub isn't installed, I dont think the command 'grub' will do anything.

---

### Post by adult swim on 2009-01-11
when you boot off of a live cd your computer does not matter.  all of the stuff needed to run an ubuntu environment is on the cd.  once you do that, the command grub will open the grub console and let you reinstall it to your mbr and it will overwrite grub2

---

### Post by Norm24 on 2009-01-11
> **adult swim said:**
> when you boot off of a live cd your computer does not matter.  all of the stuff needed to run an ubuntu environment is on the cd.  once you do that, the command grub will open the grub console and let you reinstall it to your mbr and it will overwrite grub2

Grub2 has really screwed my machine.How do I do what you just stated and have my machine back to the way it was before I installed grub2?

---

### Post by Bölvaður on 2009-01-11
> **Norm24 said:**
> Grub2 has really screwed my machine.How do I do what you just stated and have my machine back to the way it was before I installed grub2?

he made a simple list to follow. but please read what it says because a little understanding on the matter makes the gold shine brighter (I know it doesnt make sense but I wanted to add a little bright touch at the end of the sentence).

btw I dreamed I was worried about overwriting grub when I go to 9.04 as it is currently on my opensuse partition.... perhaps I should make /boot partition soon

---

### Post by Norm24 on 2009-01-11
I'm given the usual kernal choices to boot from minus the Vista Longhorn loader in the list.But no matter what I click on I get that damn error 11:
Unrecognized Device String.

If this helps I do have the ability to open a command line after startup with this "grub>" being the prompt if I choose this by pressing "C".

---

### Post by Norm24 on 2009-01-11
> **Bölvaður said:**
> he made a simple list to follow. but please read what it says because a little understanding on the matter makes the gold shine brighter (I know it doesnt make sense but I wanted to add a little bright touch at the end of the sentence).

btw I dreamed I was worried about overwriting grub when I go to 9.04 as it is currently on my opensuse partition.... perhaps I should make /boot partition soon

I followed that list precisely several times.I get a boot list minus Vista but regardless of what I click on I still get error 11.

---

### Post by adult swim on 2009-01-11
put in your ubuntu live cd.  turn on your computer and make it so that it boots from the cd drive and not your hard drive (you will have to hit a button when you first turn your computer on.  its different on different computers but it should tell you.)  once you have the cd running, select try ubuntu without making changes.  once the desktop is up go to a terminal, applications>accessories>terminal
when you get there enter in ```
sudo grub
``` for the next part youll need to know what partition of your hard drive you have ubuntu installed on.  
if it installed on partition 1 run ```
root (hd0,0)
```
if it installed on parattion 2 run ```
root (hd0,1)
```
if it installed on parattion 3 run ```
root (hd0,2)
```

now run ```
setup (hd0)

exit
``` and reboot

---

### Post by adult swim on 2009-01-11
norm24, you may have to do a little bit extra if the above doesnt work for you.  unfortunately i dont know if it is neccessary to chroot to fix grub or how to do it!  fortunately i do know the perfect place for you to ask
[http://ubuntuforums.org/showthread.php?t=969368](http://ubuntuforums.org/showthread.php?t=969368)
even though your post doesnt have to do with jaunty, these guys have probably installed grub2 and went back and installed grub a couple of times.

---

### Post by igknighted on 2009-01-11
I'm pretty sure grub needs files on the hard drive, not just the mbr.  Running the update grub command /might/ work, although it doesn't sound like it is, but I think you would have much better luck chrooting into your current install and completely removing grub2, and reinstalling the default grub.

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> but I think you would have much better luck chrooting into your current install and completely removing grub2, and reinstalling the default grub.

How do I do that?

That's what I've wanted from the very 1st post!

Please tell me how to do this!

---

### Post by Norm24 on 2009-01-11
Thanks to all for your suggestions but there apparently is no way to remove Grub2 and restore the older version and have a boot list that works.

Gonna completely wipe Ubuntu and start brand new.

What a waste.

---

### Post by igknighted on 2009-01-11
See instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1034523&highlight=chroot](http://ubuntuforums.org/showthread.php?t=1034523&highlight=chroot)

Don't use synaptic, do it via the CLI.  Use the command 'sudo apt-get remove --purge grub*' to remove grub2, then 'sudo apt-get install grub' to install the new grub.  It should reconfigure for you.

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> See instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1034523&highlight=chroot](http://ubuntuforums.org/showthread.php?t=1034523&highlight=chroot)

Don't use synaptic, do it via the CLI.  Use the command 'sudo apt-get remove --purge grub*' to remove grub2, then 'sudo apt-get install grub' to install the new grub.  It should reconfigure for you.

Didn't work.Grub2 still there.

I've done everything here and am stuck with Grub2 and error 11 and a completely unusable box.

This is the kind of **** that makes Bill Gates a billionare!

---

### Post by igknighted on 2009-01-11
> **Norm24 said:**
> Didn't work.Grub2 still there.

I've done everything here and am stuck with Grub2 and error 11 and a completely unusable box.

This is the kind of **** that makes Bill Gates a billionare!

Didn't work how... can you give any specific error messages you got? If everything was removed/installed ok, but grub2 still shows in the mbr, the liveCD methods of restoring the mbr (like after a windows install wipes the mbr) should work now.  If you got error messages while removing and reinstalling, please post them.

And last time I checked, you can't do something like remove the XP bootloader and install the Vista one, so to mess up a system like that and say in windows it would be better is like comparing apples and oranges, it doesn't make any sense.  Besides, your system is completely salvageable, so don't fret yet.

We are looking for an elegant solution here, but installing a new ubuntu install (in addition to the current one) would install its own grub and let you boot your current system.  You could then fix grub from a familiar environment and then format over the new install.

---

### Post by cariboo on 2009-01-11
Boot from the LiveCD and select Boot From Hard Drive from the menu, this bypasses grub and boots directly in to your desktop. Open up a terminal and completely remove grub2:

```
sudo apt-get purge grub2
```

Next reinstall grub:

```
sudo apt-get install grub
```

Then follow adult swim's instructions in post #20

Jim

---

### Post by Slug71 on 2009-01-11
To install grub2 do the following. 

Install Grub2 from Synaptic.
A box will come up during installation for 'configuring grub-pc'. Just click forward and leave box blank.

Then in Terminal run

```
sudo update-grub2
```

```
sudo upgrade-from-grub-legacy
```

```
sudo update-grub
```

Reboot and it should be fine. The chainload method is broken so do the complete upgrade after installation as shown above.

---

### Post by Norm24 on 2009-01-11
> **igknighted said:**
> Didn't work how... can you give any specific error messages you got? If everything was removed/installed ok, but grub2 still shows in the mbr, the liveCD methods of restoring the mbr (like after a windows install wipes the mbr) should work now.  If you got error messages while removing and reinstalling, please post them.

And last time I checked, you can't do something like remove the XP bootloader and install the Vista one, so to mess up a system like that and say in windows it would be better is like comparing apples and oranges, it doesn't make any sense.  Besides, your system is completely salvageable, so don't fret yet.

We are looking for an elegant solution here, but installing a new ubuntu install (in addition to the current one) would install its own grub and let you boot your current system.  You could then fix grub from a familiar environment and then format over the new install.

Error 11 Again.

---

### Post by Norm24 on 2009-01-11
> **cariboo907 said:**
> Boot from the LiveCD and select Boot From Hard Drive from the menu, this bypasses grub and boots directly in to your desktop. Open up a terminal and completely remove grub2:

```
sudo apt-get purge grub2
```

Next reinstall grub:

```
sudo apt-get install grub
```

Then follow adult swim's instructions in post #20

Jim

Negative.Still get error 11.

---

### Post by Norm24 on 2009-01-11
> **Slug71 said:**
> To install grub2 do the following. 

Install Grub2 from Synaptic.
A box will come up during installation for 'configuring grub-pc'. Just click forward and leave box blank.

Then in Terminal run

```
sudo update-grub2
```

```
sudo upgrade-from-grub-legacy
```

```
sudo update-grub
```

Reboot and it should be fine. The chainload method is broken so do the complete upgrade after installation as shown above.

Grub2 i s kinda of the problem if you haven't followed.

---

### Post by Slug71 on 2009-01-11
> **Norm24 said:**
> Grub2 i s kinda of the problem if you haven't followed.

Yep i know i had the same problem as you just a little while ago trying to get it to work on Jaunty. I just did a fresh install to fix the problem and then reinstalled the way i explained earlier and it works fine.

Heres a link to a thread that will be of interest to you.

[http://ubuntuforums.org/showthread.php?t=1022594](http://ubuntuforums.org/showthread.php?t=1022594)

---

### Post by Norm24 on 2009-01-11
> **Slug71 said:**
> Yep i know i had the same problem as you just a little while ago trying to get it to work on Jaunty. I just did a fresh install to fix the problem and then reinstalled the way i explained earlier and it works fine.

Heres a link to a thread that will be of interest to you.

[http://ubuntuforums.org/showthread.php?t=1022594](http://ubuntuforums.org/showthread.php?t=1022594)

Just installed everything brandnew.

Thank god I backed up.

---

### Post by Slug71 on 2009-01-12
> **Norm24 said:**
> Just installed everything brandnew.

Thank god I backed up.

Cool, well if you decide to reinstall grub2 at some stage then just do it the way i said earlier and it should work. It did for me and i had the same problem as you. The trick is to do the full upgrade before rebooting and avoiding the chainload method.

---

### Post by Lexicon101 on 2009-06-28
error 11 has to do with grub2-installer (or however it's named) not adding the right partition numbers.
It's from trying to use the same partition numbers it would use with legacy grub, I believe.
In legacy grub, first partition on any given hard drive would be (hd*,0) (* represents the hard drive number here).
In grub-pc, the same partition would be (hd*,1).
Actually, in my case, the installer failed to add anything after "root=" at all, but from what I've read, most people get misnamed hard drives.

EDIT: Ah. Failed to read the timestamps. I'd realized that there was no helping the OP, but thought I might help others having this problem. I'm not even sure this is a valid problem any more..
Also, forgot to mention that the only way I found to fix this error was to edit the "grub.cfg" file where the old "menu.lst" used to be. Just add the hd numbers and change nothing else. You can do this from a liveCD if you can't boot into the partition.

---

