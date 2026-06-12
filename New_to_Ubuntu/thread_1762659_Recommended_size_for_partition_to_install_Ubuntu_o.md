---
title: "Recommended size for partition to install Ubuntu on?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by markyork on 2011-05-19
I know asking this will elicit a myriad of opinions on sizing recommendations, so I guess I'm asking what considerations I need to make in planning my (as yet undone) disk partitioning in preparation for dual-booting Windows 7/Ubuntu.

What I'm starting with:
I have a 500GB single-partition drive on my Toshiba laptop. Likely a small part of that is set aside by Toshiba for system recovery. I'm currently using about 90GB of that with Win and all of my files/programs.

When I actually partition the drive, I figured I'd create about a 150GB partition for Windows to give plenty of room for more junk there. I plan on creating another approximately 150GB NTFS partition for system backup. And then I've got the remaining 200GB (minus Toshiba's section) to play with.

How much physical disk space does Ubuntu take up? I plan on installing quite a bit of software on Ubuntu to test the feasibility of eventually replacing Windows, so I want to make sure I have room for everything. Also, the Ubuntu [installation guide]("https://help.ubuntu.com/10.04/switching/C/installing-partitioning.html") talks about creating a root partition, a home partition, and swap space. Do I need to create those partitions myself when I partition the rest of the drive, or is that done automatically during the installation process?

---

### Post by chellrose on 2011-05-19
Your 200GB +/- should be plenty of space, I think.  I've got a 125GB partition myself (not counting swap), 3 desktop environments, loads of other stuff, and I've used not quite half the space yet.

Yes, you do need to create a root partition (typically denoted / ) and a swap partition.  I'm not sure about a separate home partition, I don't remember having to make one, but maybe another user knows more.

IIRC, swap should be about **2x** the size of your computer's RAM.

---

### Post by markyork on 2011-05-19
Did some more reading of the partitioning guide I linked to in my OP. It says this:

"You don't need a huge amount of space for Ubuntu. You will need enough space for the following:
1) Root partition - where Ubuntu is installed. This should be at least 4GB.
2) Home partition - where your files are kept.
3) Swap partition - this need only be twice the size of your memory."

And this is after selecting "Manually edit partition table" during the installation, so I can I interpret that to mean do my two 150GB partitions as planned, then take care of the rest of the drive when I install Ubuntu?

What about the "Toshiba partition"? If I do it that way can Ubuntu possibly overwrite that?

---

### Post by chellrose on 2011-05-19
Right - swap needs to be **twice** the size of memory.  Sorry about that error.

Are you doing your partitioning during Ubuntu install (from the live CD), or with a separate partitioning utility such as gparted?  I haven't used any of those partitioning utilities, so if that's the case, someone with more expertise should guide you.

From the Ubuntu live CD, when you click install, it should take you to Ubuntu's partitioner.  That should show - currently - your Toshiba recovery partitions and your Windows.  You should be able to resize the Windows partition from there, but it's probably safer to do that from Windows 7 directly (**before** installing Ubuntu) as explained here: [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)  Right now, it probably shows the Windows partition as your entire hard drive minus the Toshiba stuff; you'll want to resize Windows to 150GB (or whatever size you want it to be).

From the Ubuntu installation, then, you'll need to create your root partition and your swap.  You can specify the sizes for these, and so you'll be able to leave an extra partition for your backup.  As for formatting/accessing that, I'm not sure -- maybe someone else can give a suggestion?  But at any rate, you'll be able to leave that space open for whatever you want to do with it.

Welcome to Ubuntu!

---

### Post by markyork on 2011-05-19
> **Sissy13 said:**
> Are you doing your partitioning during Ubuntu install (from the live CD), or with a separate partitioning utility such as gparted?  I haven't used any of those partitioning utilities, so if that's the case, someone with more expertise should guide you.

Currently I'm in the process of creating a system recovery/backup scheme. Part of that process will involve creating the partitions. The above question is kind of my question regarding my best course of action.

I want to be able to answer this question before I start partitioning:

If I use third party partitioning software (it will either be GParted or EASEUS), do I need to create the Ubuntu home, swap, and root partitions then, or should I just create my 150GB Win partition, the 150GB NTFS backup partition, and a 200GB Linux partition first? Or should I just create the two 150GB partitions and leave the rest of the drive unpartitioned? Then install Ubuntu on the remaining 200GB partition and create the home, root & swap partitions within that 200GB partition?

> **Sissy13 said:**
> Welcome to Ubuntu!
Thanks a lot! I'm really looking forward to getting it installed and trying it out with the intention of seeing if I can eventually replace Windows with it!

---

### Post by jaacko on 2011-05-19
Hi!

I would use a Windows utility (Easeus for example) for resizing the current windows partition and for creating the 150gb backup ntfs partition and leave the rest of the space unpartitioned.

The partitioning for ubuntu is really easy to do while installing. Plus there's an option to install ubuntu to largest free space on the hard drive and let the installer do the partitioning automatically. The installer doesn't by default make a separate partition for home folder which I think is not even necessary.

Besides, I think you can't do ext4 partitions with Easeus if I remember correctly. At least with the free version.

This is how I've done it several times. For some reason I feel more safe when I modify windows partitions inside windows.

---

### Post by markyork on 2011-05-19
> **jaacko said:**
> Hi!

I would use a Windows utility (Easeus for example) for resizing the current windows partition and for creating the 150gb backup ntfs partition and leave the rest of the space unpartitioned.

The partitioning for ubuntu is really easy to do while installing. Plus there's an option to install ubuntu to largest free space on the hard drive and let the installer do the partitioning automatically. The installer doesn't by default make a separate partition for home folder which I think is not even necessary.

Besides, I think you can't do ext4 partitions with Easeus if I remember correctly. At least with the free version.

This is how I've done it several times. For some reason I feel more safe when I modify windows partitions inside windows.

Thanks for the advice, jaacko. I've been thinking about that and I decided also that it's probably best to let Windows handle Windows stuff and keep it's paws off everything else![-X

So I'll likely use Windows' own Disk Management utility to resize the C: drive down, then use Easeus to add the other partition (unless I can just add and resize the 2nd ntfs partition with the built-in Windows utility also), then finally install Ubuntu and let it handle the remainder of the drive.

---

### Post by ajgreeny on 2011-05-19
Things have changed a bit and I suggest you have a read of [http://ubuntuforums.org/showthread.php?t=1761423](http://ubuntuforums.org/showthread.php?t=1761423) where there is a lot of good informed opinion about partition sizes.  Points to consider:-

1.  Definitely use windows disk management to shrink your win partition after two defrags, if possible in safe mode and with virtual memory disabled for the defrags; remember to enable the virtual memory again afterwards

2.  No real need to have twice your ram as swap these days; that was in the days when physical ram was much smaller than current machines.

3.  I recommend a separate /home partition, as it makes any reinstallation you might need to do, much, much easier and quicker.

4.  You can use gparted on the live CD/USB to make the partitions you want before you actually install, if you wish, but it is not needed.  Just choose "Something Else" (stupid name, if you ask me) at the partitioning page and find the unallocated space made when you shrunk windows, and you can then make one large extended partition of the whole of that space, and within that, make all you need as logical partitions.  Linux is quite happy booting from a logical partition, unlike windows

5.  I have never heard of Easeus, so can not comment on it, but gparted or the installer partitioning utility is very good, I would say pretty well failsafe in partitioning ready for linux/ubuntui.

---

### Post by Lateralis on 2011-05-19
My two pennies worth on swap partitions. 


Swap is only useful if you have limited RAM (2 GBs or less I'd guesstimate) or intend to use the hibernate feature.  If you intend to hibernate your computer you must have either a swap file or swap partition, and the size of this file/partition must be sufficiently large to store the entire contents of your RAM and any other pages which are being stored in swap at the time of hibernation.  In practise, this means having a swap file/partition between 1.5 and 2 times your available RAM.  

If you do not intend to use hibernate, and have a sizeable amount of RAM, i.e. 4 GBs or more, then a swap file/partition is probably redundant.  

For more information on this particular topic, see [here]("http://ubuntuforums.org/showthread.php?t=1042946").

---

### Post by wildmanne39 on 2011-05-19
> **markyork said:**
> I know asking this will elicit a myriad of opinions on sizing recommendations, so I guess I'm asking what considerations I need to make in planning my (as yet undone) disk partitioning in preparation for dual-booting Windows 7/Ubuntu.

What I'm starting with:
I have a 500GB single-partition drive on my Toshiba laptop. Likely a small part of that is set aside by Toshiba for system recovery. I'm currently using about 90GB of that with Win and all of my files/programs.

When I actually partition the drive, I figured I'd create about a 150GB partition for Windows to give plenty of room for more junk there. I plan on creating another approximately 150GB NTFS partition for system backup. And then I've got the remaining 200GB (minus Toshiba's section) to play with.

How much physical disk space does Ubuntu take up? I plan on installing quite a bit of software on Ubuntu to test the feasibility of eventually replacing Windows, so I want to make sure I have room for everything. Also, the Ubuntu [installation guide]("https://help.ubuntu.com/10.04/switching/C/installing-partitioning.html") talks about creating a root partition, a home partition, and swap space. Do I need to create those partitions myself when I partition the rest of the drive, or is that done automatically during the installation process?
Hi, I give my root 40 gigs, swap 2 gigs, boot 125 megabytes, yes I have put my boot on a separate partition for quite some tine now. then the rest to home. I notice though if you let natty livecd make your partitions for you it does not give you a separate home partition.

---

### Post by YesWeCan on 2011-05-19
You may want to use the "alternate install CD/ISO" to set up customized partitions.

I have completely migrated from Windows to Ubuntu. My Ubuntu / occupies a little under 5GB. My /home over 300GB (I have a lot of photos). Windows 7 seems to gobble up 20GB plus whatever user files you have.

Swap is there as emergency overspill RAM. It is not very good as RAM because it is slow. If you have a laptop and want to hibernate, the OS temporarily copies the RAM contents into the swap space. If you aren't intending to do this then swap can be whatever you like and I wouldn't bother having more than your RAM.

---

### Post by thane1 on 2011-05-19
IMHO... Use what you want from researching your Ubuntu system storage requirements.  But _*Most Definitely[I][U]_*[/I][/U] leave yourself room for a separate /home partition.  In my experience, when a new version of Ubuntu comes out and you're ready to upgrade (or your present OS gets screwed up to the point, that you decide its just easier to reinstall), if your /home is on a separate partition, you can just reinstall the old / install the new Ubuntu OS and do a "select partitions manually" option, to keep your /home partition and all of your settings.  

JUST MAKE SURE, that you don't select the reformat the partition option, when you set your old /home partition to be the /home for the new install!  If you do the new install / reinstall this way, your upgraded, next versions of Ubuntu will go (probably) more smoothly / be less buggy, than doing a Synaptic "upgrade" of the OS.

---

### Post by Dondermans on 2011-05-19
> **markyork said:**
> Currently I'm in the process of creating a system recovery/backup scheme. Part of that process will involve creating the partitions. The above question is kind of my question regarding my best course of action.

I want to be able to answer this question before I start partitioning:

If I use third party partitioning software (it will either be GParted or EASEUS), do I need to create the Ubuntu home, swap, and root partitions then, or should I just create my 150GB Win partition, the 150GB NTFS backup partition, and a 200GB Linux partition first? Or should I just create the two 150GB partitions and leave the rest of the drive unpartitioned? Then install Ubuntu on the remaining 200GB partition and create the home, root & swap partitions within that 200GB partition?


Thanks a lot! I'm really looking forward to getting it installed and trying it out with the intention of seeing if I can eventually replace Windows with it!

I would advise against keeping your backup on the same physical disk as your operating system(s). Learned it the hard way when a Maxtor drive refused to spin up one day.

Currently, my essential files are well under 4Gb in size, so they fit on a thumbdrive. More information on back up strategies can be found here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by thane1 on 2011-05-19
A further thought... You should obviously be doing a backup on some sort of media (flashdrive, dvds, cds, whatever you have) of your personal /home files, before reinstalling the OS, in case the install gets messed up.  When your do this backup, don't forget to look at any hidden files, which will be stored in your /home/"your personal account" files.  These files will be preceded with a "." such as .Mozilla or .Thunderbird .  This is where your email and internet personal files will be stored, such as address book, emails, bookmarks, etc.

---

### Post by markyork on 2011-05-19
Wow!

You guys are great with all of the suggestions, thoughts and links! It's good to know I'm getting into a product that enjoys such a helpful community!

I likely won't be doing the partitioning and install until next week, but I'll be reading up on how I'm going to do it in the mean time (I'm a planner - I'll have a step-by-step plan when I actually jump in with both feet!)

Thanks again

---

### Post by scorpious on 2011-05-19
haha yes Ubuntu forums is always full of handy advice :)

personally I split my drive into 3 sections. 

[LIST=1]
[*]my Ubuntu operating system stuff - about 100G
[*]my win7 operating system stuff -100G
[*]storage - whats left, in my case about 1.8T
[/LIST]
That way I can that way I save all my work, movies, games etc into storage and I can access everything from both operating system's.

Works great!!!

---

### Post by Mr. Shannon on 2011-05-19
Regarding the size of the / partition (assuming a separate /home partition).  I would go with 25G maybe 30G.  I currently have a 21.5G partition for / but I had to use 
```
apt-get clean
```
 to remove uneedded files in order to make enough room for any temporary DVD iso file I may end up with.  By the way, my installation has a lot of packages, including a couple that top a gigabyte.  So unless you install something unusually large, 25-30G should be fine for the root file system.

---

### Post by jramshu on 2011-05-20
When I shrunk my Vista drive I used disk cleanup to clean out unnecessary junk and remove old restore points(it keeps the last one made), deleted a crapload of programs I don't use and don't even remember why I downloaded, ran defrag a couple of times. Right clicked "my computer" ticked compress drive to save space(something like that), rebooted. Then use disk management to free up drive space. Windows is very greedy when it comes to giving up drive space on its own.

I know this is what I did in Vista, but I hear it's similar on 7.

My partitions:
3G swap (I was told somewhere that 1.5 times memory is fine, and seems to work fine.) 
20G for / (Just in case)
50G for /home

---

### Post by markyork on 2011-05-20
> **wildmanne39 said:**
> I notice though if you let natty livecd make your partitions for you it does not give you a separate home partition.

This concerns me... Seems other posts in this thread and others imply that Natty **will** allow creating a separate home partition in the Manually Partition step during installation.

Can I get some clarification, please?

Thanks!

---

### Post by jramshu on 2011-05-20
Yes, if you select the manual(advanced) partition setup you can set your /home partition.

EDIT: If you let Natty set partitions for you it will probably not put in a /home partition

---

### Post by markyork on 2011-05-20
Thanks, jramshu!

---

### Post by Elfy on 2011-05-20
> **markyork said:**
> This concerns me... Seems other posts in this thread and others imply that Natty **will** allow creating a separate home partition in the Manually Partition step during installation.

Can I get some clarification, please?

Thanks!
I think that this post is about the automatic partitioning scheme(s).

Doing it manually you'll achieve what you want.

---

### Post by philinux on 2011-05-20
For SWAP info see this.


[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by wiak on 2013-04-14
soo, if you have a 24GB partition, you give root 14GB and home 10GB, and if you have 32GB memory, you give your swap your soul? :roll:

---

### Post by oldfred on 2013-04-14
Thread closed due to age.

@wiak - ifyou need some help please start a new thread. We are a little past Natty now.
If you have 32GB of RAM you will never need swap unless you hibernate. And if only 24GB do not use separate /home.

---

