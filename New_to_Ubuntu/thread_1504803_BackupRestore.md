---
title: "Backup/Restore"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-06-08
Looked around and didn't see what I am looking for so here goes.

Currently using 9.10 and, since everything is working like I wanted, looking at upgrading to 10.04. Want to do a backup/restore system so I have everything saved just in case something goes wrong.

Computer info in signature and have a Seagate Maxtor OneTouch Mini 4 external harddrive @ 160GB. 9.10 recognizes it via USB as soon as I plug it in but that's as far as I get.

Would like to do a backup on everything and have it a "plug in & restore" option like it was in Windows. Can't install (don't trust wine - too many problems with that previously) the program from the disc. Is there a program available in Ubuntu for doing this? Or does anybody know if there is Seagate/Maxtor software for this available anywhere. (Searched, didn't find, maybe entered wrong.)I see several listing in the Software Center, but not sure which ones will do what I want.

Suggestion gladly accepted, except "drop dead"!

Thanks.

---

### Post by karthick87 on 2010-06-08
Have a look at [here]("http://ubuntuforums.org/showthread.php?t=35087").

---

### Post by flyfishingphil on 2010-06-08
> **getyourkarthick said:**
> Have a look at [here]("http://ubuntuforums.org/showthread.php?t=35087").
From 2005. Shows a good step by step (a little unclear in some areas for a newbie) but is it still applicable? Want to do a backup/restore to external drive so if something goes wrong in upgrade I can just step back to what I had before I did the upgrade. Lots of argument there regarding Norton Ghost and server. Single laptop here and no Ghost.

---

### Post by XubuRoxMySox on 2010-06-08
When you installed Ubuntu you were offered the Partitioning tool. It's always a good idea to keep a separate **/home** partition. That is where Linux puts your photos, documents, browser bookmarks, e-mailsettings and folders, desktop configuration etc. When you do a fresh installation and leave that partition unformatted, you don't lose them!

You lose *applications*, but not the data. It's one of the best kept secrets of Linux! There's nothing like it in Windows - when you reinstall Windows, you wipe the entire drive!

It's a good idea to back-up stuff to external media (CDs, USB stick, etc) anyway though. You can even back up applications that you have downloaded, using **aptoncd** (available in the repositories). 

Google the word "**remastersys**" for a look at creating a bootable iso of your entire system! 

Really amazed at Linux' power and versatility,
Robin

---

### Post by Arla on 2010-06-08
Have you looked at [fsarchiver]("http://www.fsarchiver.org/Main_Page")? I've used that in the past and so far not had issues.

---

### Post by flyfishingphil on 2010-06-08
See many references to doing backup into home and OS in different partition. Now I'm real concerened about partitions.

Viewing thru GParted all I see is:

_Partition 1            File System            Size_
/dev/sda1                  ext 4                  224.6 Gib
/dev/sda2                  Extended               8.28 GiB
  (sub below sda2
    /dev/sda5               Linux Swap            8.28 GiB

Now that has me wondering if, when I did the full installation of 9.10 following the setup procedures, did it partition for  the "home" partition many refer to. How do I check, before I try the backup/restore plans suggested, to see if it is partitioned correctly? (Noticed a couple of things: Only shows a total of 232.88 GB in size with a 250GB HDD and only shows sda1, sda2 and sda5. Where are 3 & 4?)

Weird! during that it suddenly shutdown and restarted. Feels a little warmer than usual but have external fan system blowing hard. Can't afford to lose everything again.

---

### Post by philinux on 2010-06-08
Remastersys is awesome.

---

### Post by Arla on 2010-06-08
> **flyfishingphil said:**
> See many references to doing backup into home and OS in different partition. Now I'm real concerened about partitions.

Viewing thru GParted all I see is:

_Partition 1            File System            Size_
/dev/sda1                  ext 4                  224.6 Gib
/dev/sda2                  Extended               8.28 GiB
  (sub below sda2
    /dev/sda5               Linux Swap            8.28 GiB

Now that has me wondering if, when I did the full installation of 9.10 following the setup procedures, did it partition for  the "home" partition many refer to. How do I check, before I try the backup/restore plans suggested, to see if it is partitioned correctly? (Noticed a couple of things: Only shows a total of 232.88 GB in size with a 250GB HDD and only shows sda1, sda2 and sda5. Where are 3 & 4?)

1. You don't have a separate Home/OS partition, the regular full install does NOT partition those two into two different places.

2. 232.88GB is probably the right size total for the drive, the problem with drives is that hard drive manufacturers note the size based on 1000K in a MB (and 1000MB in a GB) where the OS reports it based on 1024K in a MB and 1024MB in a GB.

---

### Post by XubuRoxMySox on 2010-06-08
As far as partitioning goes, it only sounds scary. But it's actually pretty easy. I always choose to **partition the drive Manually** and define my partitions this way:

My first partition is "**[COLOR="Purple"]swap[/COLOR]**," and it's size is twice my computer's RAM. My little hand-me-down Dell has 512 of RAM, so I make my swap partition 1 gig in size.

Swap is not "ext4" or whatever, it's just a place for your machine to use as "virtual RAM" in an especially demanding circumstance. 

Next is "**[COLOR="Purple"]/[/COLOR]**" (that's the mount point) which is where the OS is actually installed. I give mine 15-20 gigs (which is way more than it needs - my fully installed system actually takes up less than 3 gigs of space, but 10 gigs is recommended as a minimum on a 40-80 gig hard drive). I designate the file system as ext4.

And lastly, I use the rest of the hard drive as "**[COLOR="Purple"]/home[/COLOR]**" (that's the mount point). Also designated as ext4 on my machine.

This is all done in three steps (because once I make a change, the partitioning software "reloads" and recalculates to show the changes I selected). It helps me avoid mistakes, too, by showing me what I've done, and how much disk space is left to work with after the change. If this is your first time doing it, you should format both **[COLOR="Purple"]/[/COLOR]** and **[COLOR="Purple"]/home[/COLOR]**. But thereafter, you can leave **[COLOR="Purple"]/home[/COLOR]** unformatted and keep all the data stored there for your next installation!

Once you've got 'em all set up, click *Forward*, acknowledge the warning that the changes will wipe away data on the partitions you selected for formatting, then watch the magic!

With a decent internet connection, you'll have a ready desktop in under 15 minutes. 

Enjoying mine very much,
Robin

---

### Post by WinterWeaver on 2010-06-08
I also have a separate home partition, and it works great.

To backup that home partition however, I use Back in Time (it's in the repos)

It's a great utility that reminds me of time machine on the Mac.

---

### Post by flyfishingphil on 2010-06-08
> **Arla said:**
> 1. You don't have a separate Home/OS partition, the regular full install does NOT partition those two into two different places.

2. 232.88GB is probably the right size total for the drive, the problem with drives is that hard drive manufacturers note the size based on 1000K in a MB (and 1000MB in a GB) where the OS reports it based on 1024K in a MB and 1024MB in a GB.
Interesting to learn. I don't remember it asking me if I wanted to set up a home partition. Having played around with it a bit I figured that would be done on installation.

So, now that I have everything operational as I like it, is it possible to go back in and do a "home" partition without "damaging" the "goods", or do I need to restart everything?

Using VBox, with WinXP for a couple of programs that require it like my cell phone, and hate the thought of having to go thru that entire process again to get everything to work right. Bad part is I got it to work, after several hours, but don't really know what the last effort that got it operational was. Also don't want to have to go thru the "counterfiet" issue on the XP if I had to install it again and "exceeded" the "1 computer" quota.

Would something like Simple Backup & Restore or File Backup Manager in Software center be workable?

---

### Post by paparozoumis on 2010-06-08
I use Clonezilla for backing up all my linux and Windows machines, does the trick perfect. 
If you search a bit you can find all the details of how to use it with just a few up and down arrows and Enters...

---

### Post by jmszr on 2010-06-08
flyfishingphil,

Here is a link to instructions for setting up a /home partition post installation of Ubuntu: [http://ubuntuforums.org/showthread.php?p=9141619](http://ubuntuforums.org/showthread.php?p=9141619) .

+1 for Back-In-Time.

---

### Post by flyfishingphil on 2010-06-08
> **jmszr said:**
> flyfishingphil,

Here is a link to instructions for setting up a /home partition post installation of Ubuntu: [http://ubuntuforums.org/showthread.php?p=9141619](http://ubuntuforums.org/showthread.php?p=9141619) .

+1 for Back-In-Time.
Thanks, I'll check it out and see what I can do. 

Just did a "copy" of the "home" folder to a dvd (about 1.3 GB) and it appears everything transfered.

Looked over the instructions and they created a couple of questions. I'll read the "Koala Bible", for the umpteenth time, and see if I can figure out exactly what it is I want to do here as there seems to be a liilte confusion here, on my part, about what I want to do.

[I]B. You should see all of the partitions on your hard drive. If you only have Ubuntu installed (I do) you will see 2: one is / and the other is swap. Right click on the / partition and select "Resize/Move". Shrink it to however big you wish your /home partition to be.

C. Now right click the free space and (it will say unallocated and have a grey square) and select "New". Make it whatever file system you wish, label it something if you want to keep better track of it, and click "Add".[/I]

I thought that the "home" partition was where you kept the "stuff" you didn't want to lose. If so, where is the "programming", like 9.10, that could crash, kept and where do you direct additional applications to install to? If not, where do you keep all of the files, etc, that you want to protect from possible crashes?

No rush on answers. Like I said I'll try reading the Koala Bible agains and see what it says there. 

More confusion to follow

---

### Post by Miljet on 2010-06-08
> Partition 1 File System Size
/dev/sda1 ext 4 224.6 Gib
/dev/sda2 Extended 8.28 GiB
(sub below sda2
/dev/sda5 Linux Swap 8.28 GiB

Now that has me wondering if, when I did the full installation of 9.10 following the setup procedures, did it partition for the "home" partition many refer to. How do I check, before I try the backup/restore plans suggested, to see if it is partitioned correctly? (Noticed a couple of things: Only shows a total of 232.88 GB in size with a 250GB HDD and only shows sda1, sda2 and sda5. Where are 3 & 4?)

Each disk can contain a maximum of 4 primary partitions. One of those primary partitions can be an extended partition which serves as a container for other partitions, known as logical partitions. The labels sda1 through sda4 are reserved for primary partitions - even if they are not used. Just think about the way Microsoft reserves drives A and B for floppy drives even though most modern machines do not even have a floppy drive. So all logical partitions start numbering at sda5. Clear as mud?

You have sda1 which is a primary partition that contains your entire Ubuntu installation. Then you have sda2 which is both a primary partition and an extended partition. Then you have sda5 which is a logical partition located inside the extended partition sda2. sda5 is used as swap.

I don't remember seeing it mentioned so I will remind you that you can not resize partitions that are mounted (in use.) So you will have to boot from a live CD to change partitions.

Your program files are located at "root" which is represented by a forward slash (/). When you create a separate home partition which contains all your personal files and individual settings for various programs, it will be mounted at "/home".

One final note, when you shrink sda1 to create unallocated space for /home, the new partition should be sda3. It will look funny to have sda3 come before sda2, but that is perfectly normal.

---

### Post by flyfishingphil on 2010-06-08
> **Miljet said:**
> Each disk can contain a maximum of 4 primary partitions. One of those primary partitions can be an extended partition which serves as a container for other partitions, known as logical partitions. The labels sda1 through sda4 are reserved for primary partitions - even if they are not used. Just think about the way Microsoft reserves drives A and B for floppy drives even though most modern machines do not even have a floppy drive. So all logical partitions start numbering at sda5. Clear as mud?

You have sda1 which is a primary partition that contains your entire Ubuntu installation. Then you have sda2 which is both a primary partition and an extended partition. Then you have sda5 which is a logical partition located inside the extended partition sda2. sda5 is used as swap.

I don't remember seeing it mentioned so I will remind you that you can not resize partitions that are mounted (in use.) So you will have to boot from a live CD to change partitions.

Your program files are located at "root" which is represented by a forward slash (/). When you create a separate home partition which contains all your personal files and individual settings for various programs, it will be mounted at "/home".

One final note, when you shrink sda1 to create unallocated space for /home, the new partition should be sda3. It will look funny to have sda3 come before sda2, but that is perfectly normal.
Miljet. Thanks! Very clear MUD! Actually that breakdown of partitions helped a lot. Everything I find says create all the partitions you want on one page then "you can only have 4 partitions on another page with only a reference to "other partitions will be logical". Not that they are sub-partitions within a primary partition. (Question here: How do you do the "logical partitions" in a primary? Never really understood creating D, and other, drives either.)

In the Koala Bible manual it mentions doing a partition specifically for installing the Ubuntu of choice. (Maybe 20 GB) I would think that anything I installed after that, using Software Center or Synaptics Manager, would then install in the same location, or do you need to direct all future installations to that specific drive and, if so, how?

Now, another step in the darkness by a blind man!

In all that I have on hand, in manuals downloaded and printed, I get the impression that doing a "clean install" of 10.04 is the better way to go since it would allow for the resetting of the drive into multiple parts. Now a couple more questions:

Since the WinXPPro I'm using is designated for use in just one computer, and doing that may result in another installation with the resultant "counterfeit version" problems (requiring convincing MS that I am doing a reinstall, etc, and need a new activation code) how do I get around that potential problem? Would it be better to just do the full upgrade (takes about 3 hours, but that's ok) and replace the 9.10 with the 10.04? Would that keep everything I am doing in VBox available without having to do a bunch of reinstalls?

Next question: If I do the upgrade, instead of a full format/clean install, and want to do the reset as described in the link above (from jmszr) maybe I missed it but it appears to only give you one additional partition. If I want one for saving documents, and one for website project, how do I do that using the HOW TO jmszr sent?

Don't see that addressed in the Koala Bible or the Ubuntu Pocket Guide and Reference I printed.

And, yes, I know what this would cost using Windough$! That's why I sign it that way. Thanks again for the assists.

---

### Post by flyfishingphil on 2010-06-09
Just stepped up and did the upgrade to 10.04 (again). Everything seems to be working properly so now I guess I go ahead and try to "after installed" partitioning.

I asked above, following the directions I printed out from the ref above, how do I do more than one partition. It only says to right click the free space and select new to create a new partition. Maybe I'm missing it but how would I get 2 partitions out of that empty area instead of just one?

---

### Post by Miljet on 2010-06-09
A "clean install of 10.04" does not affect your XP installation. You are only reinstalling Ubuntu, not everything on your disk.

On second thought, I must have missed something because now you are talking about messing up your WinXP installation. You do not have a WinXP installation on this disk.

---

### Post by flyfishingphil on 2010-06-09
> **Miljet said:**
> A "clean install of 10.04" does not affect your XP installation. You are only reinstalling Ubuntu, not everything on your disk.

On second thought, I must have missed something because now you are talking about messing up your WinXP installation. You do not have a WinXP installation on this disk.
Thanks miljet. I'm from the "old timers" in playing with windows/computers. Actually started out in the Cobalt days, left for a while and came back to Win 3.1. When I read something that says "clean install" that usually means "formatted drive" not "reinstall" or "install over" what is already there. I didn't want to "format" and do a "clean install" because that would have required setting up both VBox and XP again and, with the games they play, it would probably have read it as a "new/second" computer and it's only cleared for use on one. Hence the potential of being declared "counterfiet" and spending a couple of hours on the phone getting everything straightened out with MS and getting a new key so I could re-install XP.

Regarding having the XP, that's being used inside the VBox for a few Win user specific programs like my SE W760 cell phone and my Magellan Explorist GPS and to get everything out of a Canon Printer/scanner. Tried WINE but, basically, if it ain't a game it ain't gonna work! (About as reliable as politicians after they're elected.) It's the only way I have found to work, and make it possible to plug my phone in and go online (internet), using my cell.

Now, just have to read the instructions about a dozen times, download the needed stuff and plug it in so it's available, and do the post install partitioning.

---

