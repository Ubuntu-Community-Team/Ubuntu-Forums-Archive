---
title: "Partition advice needed."
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Nesaskewatch on 2010-05-06
I was installing Lucid onto a new Toshiba L500 laptop and was hoping to get a little advice before proceeding.  I have attached a pic of my drive as it is before Lucid.  I got as far as the point of no return (writing to the disk) when I bailed because I was unsure.  The live dvd showed three partitions: The 7 loader/recovery as sda1, the installed 7 OS as sda2, and a Vista loader(?) as sda3.  I know that I want to install to C: (sda2) and leave the recovery and Vista loader partitions alone.  Will selecting "Install along side..." during installation write to sda2?  Or, do I have to manually configure the partitions to keep from writing to the wrong drive?  I have never selected manual before and want to avoid wrecking this thing!  Advice is much appreciated!

As I don't have a cd for 7, I made a set of recovery dvd's.  I dont have a windows cd.

Cheers!

---

### Post by houseworkshy on 2010-05-06
I haven't installed ludid yet so this may be invalid.  As it is all on one disk anyway why not defrag windows and reboot to the live cd.  Then simply choose the "install into largest free space" in the automatic installer.  When I've done this I still have plenty of room in windows due to window's un-moveable files.

---

### Post by Nesaskewatch on 2010-05-06
I didn't see anything about installing to the largest free space...  I might not have gone in far enough.  I backed out before writing *anything* to the disk.  The installer warned me I was about to pass a point of no return when I bolted.

Also, if I select "install along side and choose between them at startup", I will end up with the loaders in the boot menu right?  That seems goofy.  Not to mention dangerous.  Is there some way of installing and not having to go back and edit the boot menu?  Should I lose the loaders now that I have the "recovery" dvd's?

Sorry if this is a dumb thing to worry about, but while searching for answers here, I have read a lot of horror stories about 7 not working after installing Lucid.  I also mangled my other laptop by messing with partitions.  It's good now, but I don't want to go down that road again!

Thanks again.

---

### Post by srs5694 on 2010-05-06
Unless you're using WUBI (a specialized installation method that puts Ubuntu in a file on a Windows partition), you do *not* want to install Ubuntu to your existing C: drive, since doing so will *wipe out all data on the drive!*

Now, allow me to back up and give you some important background information:

Your existing partitions, in order, are almost certainly a Windows Recovery Environment (RE) partition (used in booting and holding some important backup data; I'm a bit foggy on the details), the Windows C: partition that holds most of Windows, and a partition that holds the equivalent of your Windows installation DVD because Toshiba was too cheap to provide you with an actual separate DVD for this purpose. Before you do anything else, you should locate a utility in Windows that will enable you to create recovery DVDs from this last partition. Use it to create two sets of recovery DVDs. These will be vitally important if anything goes badly wrong, either now when you install Ubuntu or in the future -- say if your hard disk fails. This process will take a while, and to make use of your time, I recommend you write a letter to Toshiba (with a cc: to Microsoft) telling them how cheap you think they are for not providing proper recovery DVDs.

That out of the way, you'll have to clear away some space to make room for Linux. AFAIK, the third partition, which holds the recovery DVD data, can be safely removed now that you've got the recovery DVDs. (I don't have any authoritative reference for this assertion, though, so if removing the partition makes you nervous, don't do it, or at least back it up in some way other than using the Windows tool to make DVDs.) If you remove this partition, that will give you about 10GB, which is enough space for a modest Linux installation, but not much else. (There'll be little room for user data.) You could stop here if you just want to try Linux, or you could continue by resizing your Windows C: partition. The safest way to do this is using the Windows partitioning tool; however, the Ubuntu manual partitioning option during installation will also allow you to do it. There's a chance that the Ubuntu tool will leave Windows unbootable, though. There's another option called "side-by-side" installation that might do the job, but I'm not entirely sure what it does.

My own recommendation is to create three or four partitions for Linux by using the manual partitioning option:


[list]
[*]A Linux root (/) partition of 5-20GB, depending on how much software you plan to install.
[*]A swap partition that will be used by suspend-to-disk functions and for extra memory if the system runs out of RAM. Set it to be at least as large as your installed RAM, but not more than twice that amount. (More than twice your RAM size is unlikely to ever be used, so it just chews up disk space unnecessarily. In fact, you might not even use as much as you've got RAM, except for suspend-to-disk functions.)
[*]A Linux /home partition that will hold your user data. Size this to fill the available space after the root (/) and swap partitions are allocated.
[*]You can optionally shrink your C: partition further and set aside another partition, to be used as a shared-data partition for both Linux and Windows. This way, neither OS needs to access the other's main partition to transfer files or to access files you'd want to use in both (family photos, MP3s, etc.). Make it NTFS and put it between the Windows and Linux partitions for best performance.
[/list]


When you create partitions with the manual partitioner, you set a "mount point," which is the directory from which you'll access the partition. You must have a root partition (mount point of "/"), and you set a mount point of /home for the /home partition. Swap space doesn't have a mount point. The shared-data partition can go almost anywhere. You might try /home/shared or /home/username/shared, where "username" is the username you intend to use, but you could use /shared, /winshared, /flubbygubby, or whatever you like, so long as it isn't the same as one of the standard Linux directories.

Note that resizing partitions is inherently dangerous. If you haven't yet done much to customize your Windows side or create user files on it, you might just plow on ahead, since you'll be able to restore it to a from-the-factory state with your recovery DVDs; however, if you've put much effort into it, you may want to use a Windows backup tool to back up the Windows installation, or at least copy your user files to a DVD or USB flash drive for safekeeping.

If you partition as I suggest, you'll run into a limitation in the Master Boot Record (MBR) partitioning scheme used by most PCs today: You can have only four "primary" partitions. One of these can be set up as an "extended" partition, which can in turn hold as many "logical" partitions as you like. Fortunately, Linux can install just fine to logical partitions, so I recommend creating one big extended partition in your free space and then creating as many logical partitions as you need within it. (The shared-data partition, if you create it, can also be a logical partition.)

The Ubuntu default partitioning option is simpler; it just crams everything into a swap partition and a single root (/) partition; user files then go in the root partition's /home directory rather than in a separate /home partition. This works, but is less flexible, since if you ever need to re-install from scratch, you'll have to back up your user data and then restore it afterwards.

I hope this helps.

---

### Post by flyfishingphil on 2010-05-06
> **Nesaskewatch said:**
> I was installing Lucid onto a new Toshiba L500 laptop and was hoping to get a little advice before proceeding.  I have attached a pic of my drive as it is before Lucid.  I got as far as the point of no return (writing to the disk) when I bailed because I was unsure.  The live dvd showed three partitions: The 7 loader/recovery as sda1, the installed 7 OS as sda2, and a Vista loader(?) as sda3.  I know that I want to install to C: (sda2) and leave the recovery and Vista loader partitions alone.  Will selecting "Install along side..." during installation write to sda2?  Or, do I have to manually configure the partitions to keep from writing to the wrong drive?  I have never selected manual before and want to avoid wrecking this thing!  Advice is much appreciated!

As I don't have a cd for 7, I made a set of recovery dvd's.  I dont have a windows cd.

Cheers!
If you don't have it yet download the user guide and the manual and read thru those. Mine has Windough$ Vista in it and I installed Ubuntu on the same drive with no problem Yes, I do need to do a selection at startup but that only takes a second. As I recall there have been a couple of times I fired up the computer, went for coffee and was in Ubuntu when I got back.

Minor effort but you get used to it so you don't think about it much.

Hope this helps.

---

### Post by ranch hand on 2010-05-06
I would boot to the Live CD and partition the drive before installation using gparted (System>Administration>Gparted {or Partition Editor}).

You have a limit of 4 "primary" partitions on any drive.  You have 3.  You need a swap partition and a / (root) partition at least.

Therefore I would create 1 "extended" partition.  This is a type of primary partition that you can create any number of "logical" partitions inside of.

You should defrag your Win WTF Pro before starting.

See how much free space you have and make that your extended partition.  If you need to shrink the MS install do it from the MS tool for that (don't ask me, I know nothing about it).

You really should have a swap partition the size of your ram (suspend will not work if it is smaller), about 10 to 15Gb for a / partition and the rest (hopefully at least 20-30GB for /home.

The reason for a / and a /home partition is that if you fry your installation you can reinstall the OS and not have the /home partition formated for the reinstall.  While you should back up your data it is probably going to be fine (I have done this several times and never lost any data or config files).

We could give better advice with real information on your partitions.  You could, from the Live Session run in terminal and post the results of:
```

sudo sfdisk -l

```

Let the fun begin.

---

### Post by QLee on 2010-05-06
Suspend can still work even without a swap (because it is suspend to RAM, keeps the RAM powered)

For hibernate you need a swap file large enough to hold the contents of RAM (that's what's written to disk).

---

### Post by ranch hand on 2010-05-06
> **QLee said:**
> Suspend can still work even without a swap (because it is suspend to RAM, keeps the RAM powered)

For hibernate you need a swap file large enough to hold the contents of RAM (that's what's written to disk).
I will stand corrected with pleasure.  I do not use either one so my ignorance has just been reduced.

Thanks.

---

### Post by QLee on 2010-05-06
[QUOTE=ranch hand]... so my ignorance has just been reduced.[/QUOTE]

And not just you ranch hand, all the lurkers who might have misunderstood also now have a chance to understand, that's one of the most useful things about a forum style of help, peer review, knowledge increases and the community becomes better. We don't need egos, we just need good data, from which we all benefit over the long run.

---

### Post by ranch hand on 2010-05-06
> **qlee said:**
> and not just you ranch hand, all the lurkers who might have misunderstood also now have a chance to understand, that's one of the most useful things about a forum style of help, peer review, knowledge increases and the community becomes better. We don't need egos, we just need good data, from which we all benefit over the long run.
+1

---

### Post by Nesaskewatch on 2010-05-07
There's a whole lot of great advice here!  I am just recovering from yesterday's celebrations :redface:, and will take a bit longer than usual (!) to absorb all these excellent points.  My questions have clearly been answered though.  I suppose I shouldn't be so gun shy, but I hate it when I fubar things by diving in without knowing what I am doing.  Some of this advice has also cleared up some other fundamental things that will make future actions more easily understood.

Thank you, and I will post the abreviated results when the install is complete.

Cheers!

---

### Post by cryptotheslow on 2010-05-07
*edit - it's all been said already :)*

---

### Post by Nesaskewatch on 2010-05-07
Sorry this has taken so long.  Here is the output of > sudo sfdisk -l

```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    191-    192-   1536000   27  Unknown
/dev/sda2        191+  37516-  37325- 299812864    7  HPFS/NTFS
/dev/sda3      37516+  38913-   1397-  11220992   17  Hidden HPFS/NTFS
/dev/sda4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ 

```

Also, this is a good time to list this as well: Toshiba Satellite L500, Intel Dual-Core T4300.  320(?) gig HD.  3 gigs Ram.  Pre-loaded with Veendowz 7 Home Premium Excelsior Deluxe Obergroupenfuhrer Gestalt!  (The most repressive and overbearing operating system yet, with even less user control than ever before!)  Thoroughly cleaned and defragged.


I figured I would leave the partitions as they are, but use 7's "disk management" to resize sda2 (C: in 7) to ~100 gigs if it will let me.  (Windows will **_NOT_** be moved!)  I will then reboot, make sure 7 is still there and working, restart into the Lucid live dvd, launch gparted and format the new unused space to ext4, install Lucid to all but 10 gigs which is for the /home partition and the swap file. (4 and 6 gigs respectively)  I am hoping the installer will give me the chance to specify these things.  Like I said, I have never manually set up the partitions during installation before.  I am also going to spend some more time reviewing manual partitioning before I continue.  There isn't a whole lot that covers the "new" installer yet.  There appears to be some subtle changes from 9.04, but it should be close enough, yes?  

Another thing; would I be better to do a full install, *then* create the /home partition?  Or, should I do it all at once during the install?  If all while installing, will the installer assist me in any way, or are there methods for doing this manually?

Thanks fellers.  Nice to know there's help out there fer them what needs it.

---

### Post by ranch hand on 2010-05-07
If you look on gparted you will be able to see how much of the "hidden" partition is used.  You can shrink it to about double what is used.  I suspect that it is mainly empty.  It should contain a small amount of recovery tools that you need the install disk to get at.  I think there is another disk you can down load if you do not have the install disk.

If you make the partitions first and write down the numbers doing a "manual" install is simple.  Creating a /home partition later is a pain, manual install is simple.  Just follow the directions.

Right click on the / partition and select "change".  That will let you choose to use the partition and what the mount point should be (/) and whether to format or not.  The /home partition is the same deal.  I can do it, it can't be that hard.

I always (except for my first 2 installs ever) use the manual install.  I think it is easier.

---

### Post by Dude-PWB- on 2010-05-07
What I have always done for a dual boot on any Windoze machine that I have added Ubuntu to was open gparted from a live cd (Ubuntu Live Cd or Gparted Live CD) and simply shrink the Windows partition enough to leave adequate room for the Ubuntu install. For example, if it is a 200GB windoze partition, with 30GB used, I might shrink the partition from 200 to 120, leaving 80 for Ubuntu. I would create the partition with the 80, but leave it unformatted.

The newly unallocated space that is left over, I would just tell the Ubuntu installer to install in the largest continuous free space and it would always use that unallocated space for the install and install grub to keep windoze intact.

Not sure if it's the right way or the wrong way, but it has always worked for me.

---

### Post by ranch hand on 2010-05-07
I think that if you try that on vista or 7 you are going to have a problem.  I think it may be safe if you make sure that the box to "round to sectors" is unchecked but as I do not allow  MS product in the house I do not know.  I do know that it is really not a good idea to resize those two OS', with gparted, unless you do know.

---

### Post by srs5694 on 2010-05-08
> **Nesaskewatch said:**
> install Lucid to all but 10 gigs which is for the /home partition and the swap file. (4 and 6 gigs respectively)

You're thinking about the disk space backwards. When you split /home off, that's where your user files go. Linux system files then go in the root (/) partition. In most installations, Linux itself consumes about 5-10GB, and it's very hard to get the root (/) partition's space requirements to push up beyond about 20GB, at least on a typical desktop installation. (That's not to say it's impossible, of course, but it is hard.) User files, OTOH, can become monstrous, particularly if you use the system for storing large audio/video files, system backups, etc.

Therefore, I generally recommend that people set aside 5-20GB for root (/), 1-2 times the system RAM for swap, and the rest of the space allocated to Linux to /home. If you're absolutely overflowing in disk space or if you make a habit of installing every program you lay your eyes on, you might boost the root (/) size a few more gigabytes. Likewise if you have specific functions in mind that might consume more of its space (like running a mail server) -- but in that case you might want to split off a separate partition for the relevant directory/ies, such as /var. For typical desktop installations, though, this isn't necessary and 5-20GB (depending on how much software you plan to install) should be plenty.

> **Nesaskewatch said:**
> would I be better to do a full install, then create the /home partition? Or, should I do it all at once during the install?

Definitely split off /home during the install. It's possible to do it later, but that will require you to jump through extra hoops. There's absolutely no advantage to doing it the hard way, and depending on how you set up the partitions at the start, it can actually increase the risk to do it after the fact.

[quote=ranch hand]If you look on gparted you will be able to see how much of the "hidden"  partition is used.  You can shrink it to about double what is used.  I  suspect that it is mainly empty.[/quote]

Actually, that hidden partition is probably mostly full. Many recent retail systems come with such a partition, which holds copies of all the system software in a form that enables re-installation. Basically, it's a way for manufacturers to save $1 on the cost of a system installation DVD. Instead of providing this necessity, thew chew up 10GB or so of your hard disk space, wash their hands of responsibility, and then rake in the bucks for service calls or replacement disks when hard disks fail.

I recommend that anybody buying such a computer boot into Windows and locate the utility to generate recovery DVDs. On my latest purchase, this utility produces four or five DVDs (a couple of which are small enough to fit on CD-Rs). While you're functioning as a biological disc-change mechanism, you might as well open a word processor and write a letter to the manufacturer telling them how cheap you think they are for failing to provide something as vital as a physical emergency restore DVD. Send a copy to Microsoft, too. They'll keep pulling stunts like this for as long as we roll over and let them.

Once you've made your recovery DVDs (and a second set, just to be safe), I *think* it's safe to completely delete that partition. I did so on my latest computer purchase and it didn't blow up -- but of course I won't really know it's completely safe unless and until I need to restore Windows using those DVDs.

---

### Post by Nesaskewatch on 2010-05-08
Again, some really great advice here.  Thanks for clearing up my confusion.  I am *somewhat* overflowing with drive space, so I'll make the / volume 20 gigs.  I'm going to make another set of recovery disks too, so that should pretty much kill off the day for me.  I am also going to read up on making a seperate /home volume.  I am having trouble understanding some of this stuff.

Hasta manana amigos.  Muchos gracias!

---

### Post by ranch hand on 2010-05-08
You can look at what is in your system files by looking in nautilus (Places>Home Folder) and clicking on "file system" home is one of the folders there.  Every thing else goes in your / partition.

If you then look in the "home" folder and go to the View menu and click on "Show hidden Files" and then look at the files that show up (they will all start with a . as in .mozilla) you will see that most of your configuration files ore in the home folder there.

That home folder is what will be what is in your /home.  As you can imagine, this saves a lot of time if you need to reinstall your OS.  At least all your data and config files are still there.

If you need to do that you use manual partitioning in the installer and format the / partition and not the /home partition.

It is very easy to really get the / partition screwed in testing and I also have on OS that is for ISO testing that I install that way.  It is pretty slick.

I have a tendency to install quite a few programs with all the extras available on my stable installs.  I like a 25GB / there so that it doesn't fill up enough to get slowed down.  In testing, where I install a number of similar OS', 10Gb is what I usually use.

I also only run 15 to 20Gb for the /home partition in testing.

On here (I am now on my main stable OS) I have 25Gb for / and 150Gb for /home.  Both are about half full.

---

### Post by Nesaskewatch on 2010-05-08
I will avoid the problems and use the 7 disk utility to resize the partition.  It will leave me with enough space without having to wrangle the MFT around.  I think I understand the /home stuff now.  I may not do that on *this* system yet, as I now realize I should have done the installation of both 7 and Lucid at the same time.  That would have been the smart thing to do.  I will probably do a complete re-install when the Mangy Mutt arrives in 6 months, or maybe even sooner.  Mean time, I will just ride the Painted Pony and let the Spinning Wheel turn.  I now have my entire old laptop to try out the excellent advice you guys posted!  The Lucid install shall commence shortly.  

Thanks again for all the help guys: I would certainly have wrecked things without it.

BTW, the FFox spell check stopped working, so pardon any typo's.  :-&

---

### Post by Nesaskewatch on 2010-05-08
I have pressed a bit farther into the manual install, and wondered if when in "add new partition", should I select the mount point drop down menu and select /home as the mount point to establish a seperate /home partition?  If I choose nothing, will it select / as a default?

Thanks.

---

### Post by gjrepicky on 2010-05-08
This may be bringing coals to Newcastle, but it also may help.  I've installed various releases of Ubuntu on about fifty HP 530s at the school where I work (dual boot w/ Vista), my Toshiba M400 (Vista), my wife's Asus Eee netbook (Win 7 -- and, BTW, Asus includes a restore DVD with their little $300 machine, although neither HP nor Toshiba do!).  In each case I've followed the following procedure:

1.  Make a restore DVD set from your computer (there should be a "Create Restore Disks" utility in Windows).  I'd make two sets, and check that they're ok -- yes, I'm paranoid; no, I have never lost significant data.
2.  Defrag your Win installation if you can - probably can be omitted if the system is brand-new.
3.  Make a backup of any valuable data - I burn to DVDs and check 'em.
4.  Boot the Lucid live CD, and run the partition manager (System > Administration).  Shrink the large Windows partition.  You'll have to decide how much space to leave to Windows, how much to reserve for Ubuntu based on what you perceive to be your future needs.  If this is a relatively new machine, there should be more than enough space.  For my students, I use about 35 Gig for Ubuntu.
5. Exit the partition manager, exit the live CD, and reboot into Windows.  Windows will do some housecleaning, but I have never had the reboot fail -- this with close to 100 installations / re-installations.
6.  Reboot the Lucid CD and select install.  When you get to partitioning, select manual, and partition the free space you created.  With your Toshiba's three partitions already in place, you'll need to use logical partitions.  For our student machines, I partition 16 Gig as / (root), 3 Gig as swap, and 16 Gig as /home.  This is probably too much for / and swap, but it works. (A pretty good rule of thumb for swap is 2 x ram or 2 Gig, whichever is less.)
7.  Complete the Ubuntu installation.
8.  Enjoy! 

Mandatory disclaimer (paranoia again):  While I have had a 100% success rate, your results may vary -- no guarantees.

G.

---

### Post by ranch hand on 2010-05-08
In the manual partitioning using the installer you need to select a mount point for each partition.

As you can see there are a lot of choices.  Some folks like a lot of partitions.

The only one besides / and /home that seems like it might be nice to try some time is /var.  That folder has /var/cache/apt/archives in it and so if you reinstall / and have this separate you will have all of your programs in a .deb right there.

I haven't ever done that but I have been thinking about it.  I will need to install a copy of the daily build for 10.10-testing when they start having them and I think I will do it on there and see how I like it.

---

### Post by gjrepicky on 2010-05-08
Oops:  Re: previous post -- badly misstated swap rule of thumb.  Suggest 
2 x ram if ram < 2 Gig, swap = ram (plus maybe a little bit) if ram > 2 gig.

G.

---

### Post by srs5694 on 2010-05-08
> **ranch hand said:**
> You can look at what is in your system files by looking in nautilus (Places>Home Folder) and clicking on "file system" home is one of the folders there.  Every thing else goes in your / partition.

To elaborate a bit: Linux uses a unified directory tree for access to all files on all partitions. The root (/) directory is the "base" of this tree, and it's centered on one partition (the "root partition"). All Linux systems require a root partition.

Some, but not all, directories in Linux can be stored on separate partitions, which are "mounted" on empty directories (known as "mount points"). The /home directory is one of these that's often split off into its own directory in this way.

The /home directory, though, isn't quite the same thing as a *user's* home directory. (Note the presence or absence of that leading slash.) A user's home directory is actually a subdirectory of /home. For instance, if your username is fred, then your home directory is likely to be /home/fred. If the computer has another user (say, sally), then her home directory will be /home/sally. Big systems can have thousands of users, each with his or her own home directory in /home.

To learn about the purpose of each of the major directories in Linux (/home, /usr, /usr/local, /etc, /var, and so on), consult the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) documentation. This document spells out the purpose of all the standard directories, as well as the philosophy behind the details.

---

### Post by Nesaskewatch on 2010-05-08
I thought for a minute I understood what you are talking about, but can see now I am still in the dark.  Damn.  I will go to the hierarchy link and hope to find something that will twig my thick head.  I just don't seem to grasp what to do...

I'll just give up and go fix my brakes.  This is so frustrating!  I can tear down just about anything and reassemble it backwards and forwards, but just can't grasp what you guys mean.  I might as well be reading Chinese...

I gotta go soak my head.

---

### Post by ranch hand on 2010-05-08
Just like the first time you rebuilt an engine, take it slow, read up on it, have FUN.

What would be great is if you had an empty drive you could slap in something and just give it a whack.  That would be the best deal here.  Just install a couple of the same OS or something and see what happens.

It is a lot easier to visualize mechanical things, the only way to get that visualization here is to give it a try where there is graphic feedback.  At least that is what helped me.

---

### Post by QLee on 2010-05-08
[QUOTE=Nesaskewatch]I thought for a minute I understood what you are talking about, but can see now I am still in the dark.  Damn.  I will go to the hierarchy link and hope to find something that will twig my thick head.  I just don't seem to grasp what to do...[/QUOTE]

I don't have any new advice, you are getting good advice and suggestions, I'm just posting to support your quest. The path you are following is a good example of how to learn what you need to know to make your own choices, through use of the forum for advice. Almost anyone here will want to help someone who is clearly studying and trying to learn.

[QUOTE=Nesaskewatch]I'll just give up and go fix my brakes.  This is so frustrating!  I can tear down just about anything and reassemble it backwards and forwards, but just can't grasp what you guys mean.  I might as well be reading Chinese...[/QUOTE]

Yup! I agree with you and ranch hand, with mechanical stuff you can see it working or why it won't, darn hard to watch those electrons in action though and much harder to corral them, eh? <chuckle>

[QUOTE=Nesaskewatch]I gotta go soak my head.[/QUOTE]

A key thing to remember is to not try to do or learn too much in "one sitting", that usually makes anyone's head hurt. The break while you do the brakes is likely going to be ,"just what the Doctor ordered" (as long as nothing is too rusted and stuck), you'll come back fresh and it will probably already make more sense.

Buena suerte, amigo!

---

### Post by srs5694 on 2010-05-08
> **ranch hand said:**
> What would be great is if you had an empty drive you could slap in something and just give it a whack.  That would be the best deal here.  Just install a couple of the same OS or something and see what happens.

If you don't have a spare drive, a virtual machine (VMware, etc.) might be an option. Of course, those have their own learning curves....

Another possibility would be a USB flash drive. These are slow and give very little space, but you should be able to get a working but minimal Ubuntu install on an 8GB drive, or maybe even a smaller one.

---

### Post by BT1 on 2010-05-08
IF you don't have bitlocker on your win7, just remember that you can still access your files on the vista partition through Linux with ease. I currently have Win 7 installed on a few computers and if I want to listen to music or videos that are on the 7 partition (family uses 7 still), I just mount the drive and look for the file and open it. 7 Won't recognize files saved on ext4 yet so I just save all my files to the windows partition to save the headache of resizing for multiple Linux partitions.

---

### Post by Nesaskewatch on 2010-05-09
Thanks for the support.  The bucket was decidedly full yesterday!  I have managed to free up some drive space in the old noggin, so perhaps this will stick now.  I seem to be missing some fundamental bits of knowledge, and I end up merely parroting actions rather than knowing what I am doing.  Kind of like having a can of wonder juice that when added to the fuel makes the engine run smoothly, but not knowing what is in the can and why it works.  
Eventually, when you go to fix the engine, you have to know *why* the wonder juice does what it does.  I need to know just what is happening when I select /home rather than /usr as a mount point for example.  Or what happens when just / is selected, and why it makes a difference.  
A study of mount points and what they do is definitely in my near future.  I'll start with that stuff about Filesystem Hierarchy Standards.  looks like I'll find some wonder juice there.

BTW, I *still* haven't installed Lucid yet!  It makes sense to get past this first.  

Cheers!

---

### Post by srs5694 on 2010-05-09
A mount point is nothing but an empty directory that's used as a sort of "door" into another partition. Every Linux installation requires a root (/) partition, and other partitions and removable disks are then accessed by being mounted at mount points. This may seem strange if you're used to the C:, D:, and so on of Windows, but both methods are just ways to identify specific devices.

---

### Post by QLee on 2010-05-09
[QUOTE=Nesaskewatch]Eventually, when you go to fix the engine, you have to know *why* the wonder juice does what it does.  I need to know just what is happening when I select /home rather than /usr as a mount point for example.  Or what happens when just / is selected, and why it makes a difference.  
A study of mount points and what they do is definitely in my near future.  I'll start with that stuff about Filesystem Hierarchy Standards.  looks like I'll find some wonder juice there.[/QUOTE]

Just a few quick comments which I hope might help when you are studying. 

People choose to put /home (where all the user files reside) on a separate partition so they can format the root partition and/or install/re-install and keep all the user configurations and their data  because they choose to not format the partition that contains /home. 

The / partition is the root of your filesystem and it's where all the system files reside, keep that in mind, it's the root of the filesystem (and everything mounted is no longer treated as discrete "drives" or partitions, they are part of the "filesystem" (they can even be formatted with different filesystem types, ext2, ext4, etc.)

People sometimes put /var on a different partition because the logs live there and your apt cache, etc., so it's very active, especially in case of something going "haywire" (highly technical term) and flooding the logs.

And so on for various reasons depending on the directory we are talking about. A key thing we want to avoid is having our root filesystem become full or almost full, cuz the system she ain't going to boot then. I'll mention that again, you don't want full.


[QUOTE=Nesaskewatch]BTW, I *still* haven't installed Lucid yet!  It makes sense to get past this first. [/QUOTE]

That's how I would choose to do it but some people like to learn by jumping right in the water over their heads. I think either method can work on a user-by-user basis depending on personal style and ability. And as I commented previously, your approach is not likely to lack people who sincerely want to help you suceed.

---

### Post by ranch hand on 2010-05-09
Oh come on.  Start with the complicated stuff first.  You can pick up the basics as you go along.

Unless, of coarse, you have a stroke from the stress.

Take your time, be comfortable, remember to breath, have FUN.

---

### Post by QLee on 2010-05-09
> **ranch hand]Oh come on.  Start with the complicated stuff first.  You can pick up the basics as you go along.[/QUOTE]

 said:**
> Unless, of coarse, you have a stroke from the stress.

Agreed, that would be coarse. Gosh maybe that is why some threads die with no final message from the OP to let us know how things came out. :-)

[QUOTE=ranch hand]Take your time, be comfortable, remember to breath, have FUN.[/QUOTE]

Yes, it is possible to have fun and in a thread like this we can go OT a bit and still not incur the wrath of moderation. There is a bunch of good information and no one has insisted that their way is the only way, or even the best way, on top of that we've managed to do this without insulting anyone. Ouch, I just hurt myself while patting myself on the back. :-)

A little fun once-in-a-while helps to relieve everyone's stress, even for an old coot like me who normally wants to be "serious about technical issues"

---

### Post by Nesaskewatch on 2010-05-09
Wow, that FHS paper is fascinating!  And I only read the contents so far! ;)  I just started #4 The /usr Hierarchy.  I am actually taking notes!  

Anyway, I am beginning to grasp how and why I am about to create a separate 25 gig /home partition.  I am also intrigued by the concept of a separate /var volume, but probably will not need to worry about that for a while yet.  I will install Lucid to the remainder of the disk as ext4. (~110 gigs)  7 will continue to waste about 160 gigs, unless I decide to mess with the MFT and squash it like a bug down to 60 gigs or so.  Perhaps that will be my next odyssey?  Deliberately use gparted and recklessly shrink it's partition down to 25 gigs just for fun?  ](*,)  Who knows, I might like fixing it.  I'll certainly enjoy wrecking it, that's for sure!  I wouldn't have believed that M$ could possibly create an OS that is even less controllable than Vista.  It has more hidden and sneaky processes than ever before.  I'm surprised they actually allow us to use it at all.  I figured they'd rather have it occupy our systems and secretly report on our activities than do anything even remotely useful.

You guys have given me a lot to learn and numerous ways to learn it.  I really appreciate your advice and encouragement.  After mowing/fertilizing the lawn this afternoon, I am going to spin up the new laptop and go ahead with the install.  I think I get it now.

I'll let you know.

Cheers!

---

### Post by ranch hand on 2010-05-09
If you are using 110GB and only 25GB for /home, something is wrong.

25Gb is a pretty big / partition but not much of a /home partition.

The 10.10-testing OS I am on right now has a 45Gb /home and a 18Gb / partition.

Your root partition does have all the real important things for running your box.  This does not really take up much room.

Your /home partition really needs some size to it.

For instance, the entire /etc (in my root partition) is about 10.5Mb.  That is slightly bigger than 2 saved photos.

My /home/sam/pictures folder (in my home partition) is 3.6Gb.

The box does not need that 3.6Gb at all, I do.  With out the /etc folder the box will not run (all the grub scripts live there for one thing).

If you have installed Ubuntu before on 1 partition, which would be / it is no wonder you want it large.  The thing is, you do not have your home folder in there anymore.  That is where the size comes from.

---

### Post by Nesaskewatch on 2010-05-09
> **ranch hand said:**
> The thing is, you do not have your home folder in there anymore.  That is where the size comes from.

I have steadily increased the proposed /home size in response to various comments.  I understand what you are saying, and would ask; what size would be safe?  I do a fair bit of playing around with installing and removing packages, and have not sized anything yet.  Not a problem to adjust my plans at this point.  Also, will the installer load up the needed files into the separate /home partition automatically?  Or, do I have to direct the files there somehow?  I am yet to go all the way through the manual installation and don't know what to expect.  I *will* wear a white shirt for the occasion. :biggrin:

I will end up with a /home partition of ? size, and a swap of 8 gigs. (~Double the 4 gigs of ram I will have in 3 days)  The balance available as ext4 formatted free space.  ~160 gigs NTFS wasted on 7.

Muchos Gracias El Rancho!

---

### Post by srs5694 on 2010-05-09
> **Nesaskewatch said:**
> I have steadily increased the proposed /home size in response to various comments.  I understand what you are saying, and would ask; what size would be safe?  I do a fair bit of playing around with installing and removing packages, and have not sized anything yet.  Not a problem to adjust my plans at this point.  Also, will the installer load up the needed files into the separate /home partition automatically?  Or, do I have to direct the files there somehow?  I am yet to go all the way through the manual installation and don't know what to expect.  I *will* wear a white shirt for the occasion. :biggrin:

I will end up with a /home partition of ? size, and a swap of 8 gigs. (~Double the 4 gigs of ram I will have in 3 days)  The balance available as ext4 formatted free space.  ~160 gigs NTFS wasted on 7.

Please review [my post #17 to this thread.](http://ubuntuforums.org/showpost.php?p=9259238&postcount=17) System files, including any software you install, does *not* go in /home; /home is for user files -- your word processing documents, digital photos, MP3s, and so on.

System files installed via Ubuntu's software installation tools go in specific directory, such as /usr/lib and /usr/bin. Where those locations are in terms of partitions depends on your partitions' mount points. For instance, if you split off /usr, then any files stored in /usr/bin will be in the bin directory on the /usr partition; but if there's no separate /usr or /usr/bin partition, the'll be in the usr/bin directory on the root (/) partition.

---

### Post by Nesaskewatch on 2010-05-09
> **srs5694 said:**
> Please review my post #17 to this thread.

Boy am I glad you posted this!  I don't know how, but at some point I reversed what you stated in comment 17 and had it all backwards ever since.  (As I think you continued to hint at for some time)  Now I know why nothing made sense!  What a silly bunt.  

(Insert hallelujah chorus, and fade from a dark forbidding sky to a shot of a beautiful sunrise)

It's amazing the way the mind can get tripped up by something like that.  Also the fact that the error was so deep as to be virtually hidden, rendering me almost dumbfounded.  Mind, meet computer.  Garbage in, garbage out.  

Thank you very, very much!

Excelsior!  Away!!!  (Sound of horse galloping away)

---

### Post by ranch hand on 2010-05-09
By George I think he's got it.

I think you are ready for the fun part now.  Install that bugger and enjoy.

---

### Post by QLee on 2010-05-10
Just so you know Nesaskewatch, that comment I made about /var was to be an example meant to encourage you to look at the various directories in terms of what is kept in them and how much space is likely to be required for normal operation of your system. Most home-user desktop systems would not have or need a separate /var. Likewise /usr might be bigger for someone who installs a lot more than a default system, and so on.

Definitely consider what is being said about /home, that is where user files live (user files of all users in a multi-user system in discrete directories) things like videos, pictures, music, can take up a lot of space.

If I were setting up your system, I would set swap equal to RAM if I wanted to hibernate the system but, with the 4G you have, chances are you'll never hit swap and thus could run without one. I usually make one anyway, even if it is a small one (i.e. 300-500M) 

On a typical-user desktop system with a separate /home I have never filled a 10G / and I don't even clear the apt cache most of the time. 10-20 seems to be the recommendation.

You might also consider leaving a couple of smaller partitions to test and experiment with. You could choose to partition them now or leave unpartitioned space for it. That would be safer, maybe easier, than carving some out later. You seem to be getting into the fun, you'll probably be beta testing the next release.

---

### Post by Nesaskewatch on 2010-05-10
> **QLee said:**
> "...that comment I made about /var was to be an example meant to encourage you to look at the various directories in terms of what is kept in them and how much space is likely to be required for normal operation of your system."

Copy that.  I am already planning on setting up my "old" laptop with a dozen or so volumes/configurations for monkeying with.  The new one will just be a dualie, set up pretty much along the lines that srs5694 outlined waaaaay back at comment 4!  (It just took a lot of wrangling for you guys to halter this foal!  Sorry it took so long for me to catch on...)

> **QLee said:**
> "You could choose to partition them now or leave unpartitioned space for it. That would be safer, maybe easier, than carving some out later."

Copy that too.  It's all about "safe" on this system.  As evinced by my paranoia in setting it up right from the get-go.  
All my business stuff will be living here for the foreseeable future (Warranty work orders, tax stuff, etc) so I want it as close to perfect as possible.  

I do have one last question or two...  (ya right)  I will be deleting the old sda3. (7 recovery partition)  I would like to put everything on a new sda3 primary, and save sda4 for some time later if the need should ever arise.  To achieve this, do I have to add partitions in any particular order in the manual installer?  like; add /, then swap, then /home, in that order, with all ending up being 3 logical drives on one extended partition?  Will it use up the primary drive numbers, or do I have a choice even?  In other words, how do I make sure all of the Linux drives are inside one extended partition?  
All finishing like this:> sda1 = 7 loader, sda2 = 7 OS, sda3 = Linux extended partiton, sda5 = / (25 GiB), sda6 = /home (as big as possible), sda7 = swap (8GiB)
Again, sorry for all the caution here.  I don't want to mess it up.  I haven't seen anything while searching that uses the "new" installer included with the Lucid live dvd.  In fact, I haven't seen *anything* in this much detail.
  
Thanks fellow campers!

---

### Post by ranch hand on 2010-05-10
That looks like a workable layout.  I really would do the partitioning first with gparted on the Live 
CD.

Then when you fire up the installer all you have to do is choose the partitions manually that  you want to use (write them down).

The only thing that I think can get you is the installation of grub.  You should get a screen asking where you want it.  You want it on /sda and no where else.

The dialog on that screen says something like "if you are not sure just put it on everything".  This is not good.  It is how you overwrite the boot loader for MS so that you can't boot to it.  Not good at all for folks who want to boot to MS.

I think there is an "advanced" option on the install screen where you OK installation.  You may want to look at that as I think it lets you set where you want grub to be.  Just remember that ALL you want that on is the MBR and to do that it needs designated to install on /sda.  Just the drive, no partitions.

It will still be on your root partition but the MBR  will have a link, basically, to that information.  This is not needed on any partition so don't do it.

As you know, this is a pain to straighten out.

---

### Post by srs5694 on 2010-05-10
> **Nesaskewatch said:**
> I would like to put everything on a new sda3 primary, and save sda4 for some time later if the need should ever arise.  To achieve this, do I have to add partitions in any particular order in the manual installer?  like; add /, then swap, then /home, in that order, with all ending up being 3 logical drives on one extended partition?  Will it use up the primary drive numbers, or do I have a choice even?  In other words, how do I make sure all of the Linux drives are inside one extended partition?

I don't recall exactly what the Ubuntu installer's partitioner does; however, most partitioning software for Linux gives you the choice of creating partitions as either primary or logical (although sometimes one or another option is unavailable, depending on what partitions already exist).

There are three ways in which you can think of the partition order:


[list]
[*]The chronological order in which partitions are created
[*]The order of partition definitions in the partition table (which is also the numbering of the partitions, as /dev/sda1, /dev/sda2, etc.)
[*]The order of the partition data on the disk (sector x to sector y, etc.); that is, what part of the disk space each partition consumes
[/list]


Chronological order of creation is unimportant per se, although in the case of logical partitions, that will correlate with partition table order unless and until partitions are sorted. Partition table order is not very important, although if partition table order does not match disk-space order it can be confusing. (The partition table is just an index to disk space used; the two do not need to match up.) Disk space order can affect performance because disk head seeks take time. Thus, if you've got, say, two heavily used Linux partitions on opposite ends of the disk with Windows partitions in-between, head seeks in Linux will have to move over the intervening Windows space, which will slow things down. You can improve performance by keeping each OS's partitions contiguous.

For instance, the following is a very inefficient layout:


[list]
[*]Linux root (/)
[*]Windows C:
[*]Linux /home
[*]Windows D:
[*]Linux swap
[*]Shared data
[/list]


You can rearrange the preceding to make something much more efficient:


[list]
[*]Windows C:
 
[*]Windows D:
 
[*]Shared data
 
[*]Linux root (/)
[*]Linux swap
 
[*]Linux /home
[/list]


The numbers assigned to the partitions, and their identity as primary or logical partitions, are unimportant in terms of performance/efficiency. That said, you should try to minimize the number of primary partitions used, so that you can repartition and add primaries in the future, should that be necessary. In the preceding example, I'd make the Windows C: partition a primary and put everything else in logical partitions.

---

### Post by Nesaskewatch on 2010-05-10
> **ranch hand said:**
> As you know, this is a pain to straighten out

That was another longer than necessary trek due to operator incompetence...  I now consider myself an expert at wrecking the MBR on multiple windows operating systems.  I saw that the installer *still* has that option to mangle the MBR on windows machines.  Anyone filed a bug on that yet?

Thanks for the help Senor Rancho del mano

> **srs5694 said:**
> The order of the partition data on the disk (sector x to sector y, etc.); that is, what part of the disk space each partition consumes

You have a way with stating things very clearly.  Thank you.  The order written to the disk is what I want to optimize.  Though a setup like the one you tag as poor would be fun and easy to create!

Thanks.  That clears the last hurdle.

I'll post back shortly with a pic of my drive as configured.

Cheers!

---

### Post by Nesaskewatch on 2010-05-12
I had a couple of jobs to tend to, so I only just finished the partitioning in GParted from the live dvd this morning.  The other day, I used the windows disk management utility to shrink 7 down as low as it would let me. (160 gigs!)  Reboot and 7 still seemed alive.  Today I deleted the old sda3 which was the 7 recovery volume at the end of the disk.  Reboot and check 7.  Then I created an extended partition for *all* the free space.  Reboot and check 7 again.  I added sda5 as /, sda6 as /home, and sda7 as swap; all in the extended drive (sda3) as logical partitions.  All formatted as ext4 save the swap, which didn't give me the choice to do it anyway.   Reboot and all seems fine.  Sda1 and 2 are the 7 loader and boot in that order.  Sda4 is not used.  7 continues to function AFAIK.  I ended up with a little 3.7 meg block of unused space between 7 and the Linux extended drive.  Is that because I forgot that I should use a calculator to size the partitions?  #-o  I guess I could set that space up later as a /share drive anyway right?

I am ready to install, but I am sorry to have to ask the same question again...  Will the installer load the appropriate data into the correct volumes that I have already set up, or do I have to tell it to put /home data in the /home partition, root data in /, etc.  Is that done the same way as if it were unallocated?  ie; select "add a partition" and use the drives I already formatted for /, /home, and swap?  Should I have left the formatting to the installer?

Cheers!

---

### Post by srs5694 on 2010-05-12
Don't worry about the 3.7MB area. It's probably just an artifact of the way GParted wanted to align partitions, and 3.7MB is trivial in today's world. (That's less than three 1.44MB floppies!)

You must tell the installer which partitions to use as root (/) and /home. It will then put everything where it belongs. It won't let you install at all if you don't tell it where to put root (/), but if you neglect to tell it where to put /home, you'll end up with /home on the root (/) partition, which will require some post-installation juggling to correct.

---

### Post by ranch hand on 2010-05-12
Yes you will have to use the manual option when you get to the partitioning portion of the installation and right click on the chosen partitions for / and chose ext4 (instead of don't use this partition) and also designate the mount point.  Do the same for home.

It will warn you that you are not formatting the / partition and all data on there will be lost.  So what?  There is no data.

The only advantage to formatting again is to add a label to your partition (I think that is an option in the installer).  You could also do this after installation with gparted before you reboot.  I like labels, maybe you don't.  I do it with gparted, not even sure why, just do.

The swap partition will be auto recognized.

---

### Post by Nesaskewatch on 2010-05-12
Much appreciated folks.  I should have a screen shot of the finished product to post shortly.

---

### Post by QLee on 2010-05-12
I Agree with ranch hand, I also like labels, I find a "label" that I have assigned much easier to remember than a long string like a UUID. In addition, months later when I go back to a system that I haven't used in a while, I have an easier time remembering what I did in the past.

With your new system, you only have the dual boot so not so likely to forget anything or get confused because you'll know by the filesystem type.

On that test machine though, I suggest to consider labels, you plan to have lots of partitions and it can really help to organise your testing process. However, I'm getting older and memory is not as good as it used to be, maybe this would be overkill for your purposes. You could manually mount by label too and then you wouldn't even have to remember which device node the partition you want was on (or figure it out at the time). Plenty of time to work this out after you get your main system functioning as you want and it probably should be a new thread, this current thread is long enough and has a lot of good info, no sense in making it longer than most people will read cuz then you're stuck with us, we'll read it because we had fun and success. ;-)

QLee on Computer Leto, over and out.

---

### Post by Nesaskewatch on 2010-05-12
Copy that QLee.  You read my mind.  I had labelled the drives in GParted.  I too am gettin' long in the tooth, and the lone remaining brain cell tips off the stem when I get to thinkin' too hard.  :-k  Looks like she's good to go now!  Bit of a wireless issue, but as you said, 'nuff said on this thread.  I'll wander over to the wireless guys if I can't sort it myself.  

Thanks for the great advice folks.  I will make sure and pass it on should the opportunity arise.  I can't say enough how delighted I am with Ubuntu!  Anything a guy needs and *then* some.

Next couple rounds on me!

Cheers!

---

### Post by ranch hand on 2010-05-12
Have fun with your wireless and be sure to install gimp that they decided to leave out.

Feels good doesn't it.

---

### Post by Nesaskewatch on 2010-05-12
> **ranch hand said:**
> 
Feels good doesn't it.

Dern tootin!  Nothing like starting from scratch.  Now I get to learn all about wireless problems!  lol  I got a great deal on this unit so it's well worth the trouble.  Not that learning on the fly is trouble.  ;)

Also, I promised a pic of the finished product so I attached one.  I'm yet to label the *all* the drives, but you get the picture.

Thanks again.

---

### Post by ranch hand on 2010-05-12
Looks pretty good.  The empty spots are probably caused by the weird way that MS has of starting and ending partitions.  Gparted is just correcting that with the second one.  The first one is an example of MS waste.

Looks like a good lay out.

This way if you need, for some reason, to reinstall all your data is on a partition that doesn't get formatted and your config files are there too.  Still a pain but not a wreck.

Good work.  I think you may enjoy fooling with partitions now, I know I do.  Amazing what you can do if you want to and have an OS that lets you.

---

### Post by srs5694 on 2010-05-12
> **ranch hand said:**
> Looks pretty good.  The empty spots are probably caused by the weird way that MS has of starting and ending partitions.  Gparted is just correcting that with the second one.  The first one is an example of MS waste.

FWIW, Microsoft has changed their partition start points with Vista and 7 for good reason. A variety of technologies, including "Advanced Format" disks (with 4096-byte physical sectors masquerading as eight 512-byte sectors), some types of RAID, and SSD, require partitions to be aligned on boundaries ranging from 4KB to about 256KB for best performance, although the upper limit is a bit foggy (it varies from one technology or implementation to another). Starting partitions on other than the optimum points can severely degrade performance. Check out [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) for some benchmarks on Advanced Format drives with several Linux filesystems.

Aligning partitions on 1MB boundaries, as Microsoft now does, acts as insurance against all these issues; 1MB (2048-sector) alignment works well for just about everything. It's true that a bit of disk space at the start of the disk gets wasted, but on a modern disk with a size measured in hundreds or thousands of gigabytes, this isn't a big deal.

Unfortunately, most Linux tools still use the old style of partition alignment, which is based on the (now entirely fictitious) idea of uniform 63-sector tracks on hard disks. In the old days (in the 1980s), there were real benefits to aligning partitions on track (or cylinder) boundaries, so old partitioning tools, including those for Linux, aligned partitions in that way. This is now changing, but the old ways die hard. Chances are, Nesaskewatch, that your Microsoft partitions are aligned on 2048-sector boundaries whereas your Linux partitions are aligned on 63-sector boundaries.

Now, I don't mean to send you back to the drawing board, Nesaskewatch. Very few individual hard disks suffer from these problems, and AFAIK all the single conventional disks that do are larger than yours, so you're fine aligning your partitions wherever they happen to fall with your partitioning tools. I'm just pointing this out for future reference and to better explain these gaps you're seeing.

---

### Post by Nesaskewatch on 2010-05-13
> **ranch hand said:**
> I think you may enjoy fooling with partitions now, I know I do.

Just getting them to *work* has been a blast!  This is the first time my meddling has worked on the first try!  As I'm sure you recall, my last attempt at partitioning caused more than a little grief.  That will be my first project; creating a separate /home and moving things around on the MSI disk in the order they should be.  Then I can commit more advanced crimes like moving unmovable MS files!

> **srs5694 said:**
> Chances are, Nesaskewatch, that your Microsoft partitions are aligned on 2048-sector boundaries whereas your Linux partitions are aligned on 63-sector boundaries.

That's confirmed.  The unallocated blocks appeared after using GParted to setup the drives.  They were not there prior.

> **srs5694 said:**
> Very few individual hard disks suffer from these problems, and AFAIK all the single conventional disks that do are larger than yours, so you're fine aligning your partitions wherever they happen to fall with your partitioning tools. I'm just pointing this out for future reference and to better explain these gaps you're seeing.

You should see just how much I fuss over a job before I return it to the customer.  Anything less than perfect is below standard in my shop.  My apprentices used to learn pretty fast not to say "good enough" around me.  My reply: "No.  It isn't *good* enough, because you haven't *done* enough!  Get back to work!"  :evil:  lol  Things like those little innocuous blocks of unused drive space will bug me until gone!  But I'll leave 'em be for the time being.  Least 'til I gets me some book learnin' first!  Computers afford me the opportunity to indulge my perfectionism without having to physically replace pieces of it most times.  My dream is to buy a wrecking yard and weld the gate shut!  Then I'll spend my remaining days building things out of the 'inventory".  Computers are just a virtual wrecking yard really.

---

### Post by ranch hand on 2010-05-13
It might be a good idea to mark this as solved to protect the innocent who may wonder in.

---

