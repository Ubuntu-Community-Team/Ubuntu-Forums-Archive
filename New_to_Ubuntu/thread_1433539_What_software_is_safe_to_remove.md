---
title: "What software is safe to remove"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by CP1320 on 2010-03-19
Hi, I just installed Ubuntu as my first look at a linux OS but I installed it on a fairly small second HD so wondered if there was anything like a list of what is safe to uninstall.
I have looked through the package manager and tried selecting a few things but some come up with long lists of other stuff that will be removed so thought I had better not go ahead.

---

### Post by s.fox on 2010-03-19
Hello and welcome to the forum,

What do you intend to do with your computer?  For example you could remove the media players,  but that would be silly if you intend to play music. :) Also,  which verion of Ubuntu are you using?

In terms of how to remove software I would give [this]("https://help.ubuntu.com/8.04/add-applications/C/gnome-app-install.html") quick guide a read.

-Silver Fox

---

### Post by Grenage on 2010-03-19
[s]Watch out for anything that wants to remove ubuntu-desktop[/s].  If in doubt, write down the names of packages you are not sure about.  You can then add them with ease from a command line (if you have to).

---

### Post by anaconda on 2010-03-19
openoffice takes a lot of space,  (abiword is a small replacement for ooword)
and evolution is one progran I usually remove.
and f-spot if you dont need it.

And "Grenage" the ubuntu-desktop CAN be safely removed! It is just a meta-package. It does NOT remove the whole gnome. Actually removing ubuntu-desktop only removes the meta-package called ubuntu-desktop and not the packages that are its dependencies (like gnome and about everything else)

---

### Post by Grenage on 2010-03-19
I did not know that; thank you for correcting me.

---

### Post by mcduck on 2010-03-19
> **Grenage said:**
> Watch out for anything that wants to remove ubuntu-desktop.  If in doubt, write down the names of packages you are not sure about.  You can then add them with ease from a command line (if you have to).

Actually it's absolutely safe to remove the "ubuntu-desktop" package. You won't loose anything, the only important thing is to remember to install that package again if you at some point want to upgrade to next Ubuntu version.

"ubuntu-desktop" is juts an empty package that has all the stuff included in default Ubuntu desktop setup marked as it's dependencies. But no other package depends on the ubuntu-desktop, so installing it will bring all the default stuff while removing it doesn't remove anything else (as dependencies are one-way thing).

What you *should* be careful with is anything that removes gnome- or nautilus-related stuff.

---

### Post by CP1320 on 2010-03-19
Thanks for the suggestions, openoffice is gone. I don't really intend to do much with the system now, I have been wondering about an upgrade from XP and thought I would look at alternatives to MS offerings but I was a bit surprised by the amount of disk space the install seemed to have taken up, the file manager only shows 9 gig free on a 30+ gig drive.
I use Opera for everything internet, mail etc. so anything like that could go.
It sounds like the OS still works if I remove the desk top but what would I get in that case, would it just be a 'DOS' type screen and not be able to run any of the GUI based software.

---

### Post by 3rdalbum on 2010-03-19
> **CP1320 said:**
> I was a bit surprised by the amount of disk space the install seemed to have taken up, the file manager only shows 9 gig free on a 30+ gig drive.

Ubuntu itself should take up around 3 gigabytes. Try using Applications > Accessories > Disk Usage Analyser to see where the rest of your space has gone.

> It sounds like the OS still works if I remove the desk top but what would I get in that case, would it just be a 'DOS' type screen and not be able to run any of the GUI based software.

If you remove the Gnome desktop and don't replace it with some other desktop, you just get a command-line interface, which is a more technically correct way of saying what you said. You wouldn't be able to run GUI software without a desktop environment.

For a new user I'd advise sticking with Gnome or installing XFCE.

Remember though, the "ubuntu-desktop" package isn't the actual Ubuntu desktop. It's just a package that, when installed, will automatically install the rest of the desktop. If you remove the ubuntu-desktop package, it WON'T remove your Gnome desktop (unless all the Gnome packages also appear in the "To be removed" section).

There are parts of Evolution you can remove, if you only use Opera as your e-mail client.

---

### Post by warfacegod on 2010-03-19
If you aren't blind, you can remove Braile. Search for britty in Synaptic.

No Palm Pilot thing? Remove that.

Search ttf and languages in Synaptic and remove the fonts that are in different languages than you use.

No web cam? Dump Cheese.

Speech synthesizing can go.

I get rid of the extra screensavers.

No bluetooth. Search bluez in Synaptic. Becareful to watch the dependencies on this one one or two might be needed elsewhere if I recall.

Computer Janitor can be very dangerous. It's one of the first things to go when I install a new OS. If you would like a replacement for it, download Ubuntu Tweak. A very useful app.

sreadahead.

F-spot.

If you don't torrent then Transmission can go.

If you don't play Solitare or any of the other games, dump them too.

System Testing.

There is lots more stuff that I remove but this should give you a good start.

---

### Post by KIAaze on 2010-03-19
If you don't mind reinstalling:
[Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")

---

### Post by CP1320 on 2010-03-19
Some of the drive figures are a bit confusing, I can't remember what the formatted capacity of the drive was but just over 30 gig I think and the disk analyser shows a file system capacity of 25 gig with 2.6 gig used by the file system.
I think I need to learn more rather than doing much with this system, I had a look on xfce.org and it sounds interesting, is it possible to substitute that in the original install or can it only be changed after.

---

### Post by 3rdalbum on 2010-03-19
> **CP1320 said:**
> Some of the drive figures are a bit confusing, I can't remember what the formatted capacity of the drive was but just over 30 gig I think and the disk analyser shows a file system capacity of 25 gig with 2.6 gig used by the file system.

Ahh, there's one of the joys of hard disks: The manufacturers say that 1,000 bytes equals a kilobyte, and 1,000 kilobytes is a megabyte, etc. In fact, as we're counting in binary, a kilobyte is actually 1,024 bytes.

There is so much confusion over this that there is now an unambiguous standard: Kibibytes (KiB), Mebibytes (MiB), Gibibytes (GiB) and Tebibytes (TiB). A Kibibyte consists of 1,024 bytes, etc. Ubuntu measures using these unambiguous standards, so a 30 "gigabyte" hard disk actually gets measured in Ubuntu using Gibibytes, which makes the capacity seem smaller.

> I think I need to learn more rather than doing much with this system, I had a look on xfce.org and it sounds interesting, is it possible to substitute that in the original install or can it only be changed after.

XFCE can be installed on top of Ubuntu. Just take a look in Synaptic Package Manager.

---

### Post by warfacegod on 2010-03-20
Some of what you are "missing" is system reserve. Ubuntu holds back for itself 5% of any HDD, by default. For instance, let's say you have a 300 GB external (for the sake of argument, assume it really is 300), Ubuntu's reserve would be 15 GB, which you can't use. There is a way around this but in your case, we're dealing with the drive that Ubuntu is installed to. It's not generally wise to change the system reserve in this scenario, if your inexperienced.

Another part of what you are missing is likely to be the swap partition. What in Windows would be called a Paging file. Mine, by default, is created at .5 GB (I no longer allow one to be created during install because I don't need it.) but I've seen swap partitions created as big as 4 GB on some systems.

---

### Post by Roger Allott on 2010-03-20
> **warfacegod said:**
> Some of what you are "missing" is system reserve. Ubuntu holds back for itself 5% of any HDD, by default. For instance, let's say you have a 300 GB external (for the sake of argument, assume it really is 300), Ubuntu's reserve would be 15 GB, which you can't use.

That's interesting, and new to me. Is this something Ubuntu does for all partitions, just those that are ext[SIZE="1"]n[/SIZE] format, or just the root partition?

---

### Post by mcduck on 2010-03-21
> **Roger Allott said:**
> That's interesting, and new to me. Is this something Ubuntu does for all partitions, just those that are ext[SIZE="1"]n[/SIZE] format, or just the root partition?

Reserving 5% of disk space for root user only is the default for Ext file system, so it's not really even a Ubuntu-specific thing.

You can change the reserved amount yourself, and even safely set it to zero on any non-system partition you might have. On system partitions you should leave at least some space reserved, I'd recommend at least a gigabyte. (Besides, the performance of Ext files systems starts to quickly decrease  when the drive is almost full, so you really don't want to fill your drives to 100% anyway if there's any way to avoid it (like getting a bigger hard drive..).

---

### Post by warfacegod on 2010-03-21
> **Roger Allott said:**
> That's interesting, and new to me. Is this something Ubuntu does for all partitions, just those that are ext[SIZE="1"]n[/SIZE] format, or just the root partition?

As far as I know, it's all partitions. Ubuntu has resevered space for itself on all drives I've used, all partitions I've created for those drives, and on all externals I've plugged in.

```
sudo tune2fs -m x /dev/sdx#
```

The first x being the percent you want the reserve to be. mcduck is correct, any non-system partition is safe to set to 0. I don't bother changing system partition reserves but (assuming you have a fairly sizable install partition, 20 GB or better) 1% should be fine. Obviously the second x is the drive and # is the specific partition.

mcduck is also correct about filling an ext drive to 100% Frankly, that holds true for any filesystem. Its just not a good idea.

---

### Post by CP1320 on 2010-03-21
Not sure if this is the right forum for this now but I have been looking at the KDE desktop and I think I might try Kubuntu on some better hardware and wondered if there was any advantage in installing it over 2 hard drives, (1, SATA II & 1, IDE) and if there is what partitions do I put where.
And I understand a new version will be out shortly, would it be better to wait for that.

---

### Post by KIAaze on 2010-03-21
Separating the data from the OS (i.e. /home from the rest) is definitely a good idea.
But I don't see many advantages in splitting it up between 2 HDs.
Using one HD to backup the other seems more useful.

If one of them is very small (10GB for example), it might make sense to reserve it for the OS only.
Or if you plan to have your data on an easily removable HD.

You could also reserve one HD to try out multiple distros, so you don't have to be afraid of repartitioning, partition resizing, reformatting, reinstalling, MBR hacking, etc. :)

edit: Not sure, but I think more disk access = earlier disk failure, so splitting things up so that one HD is less accessed than the other could be interesting.
Also, since you mentioned SATA/IDE, putting often accessed data on SATA (faster) could be good too.
No idea what is accessed most unfortunately.

---

### Post by warfacegod on 2010-03-21
> edit: Not sure, but I think more disk access = earlier disk failure

Theoretically, yes. However, unless there is some extremely heavy HDD use going on (gaming, for instance), it is unlikely to ever have any real effect.

---

### Post by 2hot6ft2 on 2010-03-21
I'm shocked that no one mentioned clearing the cache of downloaded packages.
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get autoremove
```
to remove packages that were downloaded during updates and installations which are no longer required.
There are more ways to clean the system of things here [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by smellyman on 2010-03-21
[QUOTE=CP1320]but I was a bit surprised by the amount of disk space the install seemed to have taken up, the file manager only shows 9 gig free on a 30+ gig drive.
I use Opera for everything internet, mail etc. so anything like that could go.[/QUOTE]

That is not possible.  I think something else is going on.

Look at your disc usage analyzer under Applications->Accessories

---

