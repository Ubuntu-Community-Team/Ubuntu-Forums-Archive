---
title: "install ubuntu with a HOME partition and a separate DATA PARTITION"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by steninj on 2011-04-24
HEY ALL

 I am going for a fresh installation of ubuntu..(ubuntu alone)

my plan is to install it with a [SIZE=2]separate home partition and a separate data partition[/SIZE]...

so that i can either keep or avoid the application settings in my /home when i go for another installation


&
i always want to keep my datas like movies,music etc in an another partition...
i want this to be 100% untouched in every further installations..

how to create this data partition,,,,so that i can perfom read/write to this...

during an installation a "mount point" is must...

where it should be mounted?...

or how can i create that data partition..

please please please help!

---

### Post by werty2010 on 2011-04-24
nice idea...
im interested in this too
+1

---

### Post by Elfy on 2011-04-24
As far as the data partition goes - create the partition and mount it in fstab. I do all of this _after_ I've installed. 

I prefer to have my data partitions mount in /mnt - this way I can allow removable drives to appear on my desktop - but not the data drives. If you want them to be on the desktop then mount them in /media

I've a music drive in /mnt/music

The corresponding line in fstab for _my_ drive is
```

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
```

You can find uuid for your partitions with 

```
sudo blkid
```

To edit fstab after backing it up

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by frup on 2011-04-24
Do you symlink in to the relevant home directory directories?

---

### Post by The Cog on 2011-04-24
It's a good idea. User settings tend to collect cruft with time, and this time round I'm going through a process of deleteing all my user settings except for a few select programs (firefox bookmarks, thunderbird email settings etc). 

In addition to what forestpiskie said, all I can add is that I would have used /mnt/data rather than /mnt/music, but that just reflects what you want to keep in there. You can create the directory with the command:
**sudo mkdir /mnt/data**
You can make a symbolic link to this from your home partition like this:
**ln -s /mnt/data ~/data**
You will probably have to change the permissions of the folder (after mounting the partition to it) to alow the required user access.

---

### Post by Paddy Landau on 2011-04-24
What you want is this:

[LIST=1]
[*]Partition 1:Your Ubuntu installation. You need roughly 20Gb for this (that's more than enough space for Ubuntu).
[*]Partition 2: Your home directory, where you keep your data. This takes your entire disk except for partitions 1 and 2.
[*]Partition 3: Your swap partition. You need the same amount as you have RAM (but no less than 1Gb).
[/LIST]

Note that you do not need an extra partition for your music, etc. When you install a new version of Ubuntu, it will go into partition 1, while you leave partition 2 alone.

BTW, these three partitions can be in any order.

I suggest you boot from a Live CD. **N.B. I assume you want to reformat your entire disk, and you have full backups of all your data.** Let us know if this is incorrect.

Install Ubuntu, choosing the manual option for partitioning.

[LIST=1]
[*]Create partition 1 for root (/), and format it as ext4.
[*]Create partition 2 for home (/home), and format it as ext4.
[*]Create partition 3 and format this as swap.
[/LIST]
 
In future, when you install Ubuntu, again choose manual; but say that you want to format your root (/) partition, and you do *not* want to format your home (/home) or swap partitions.

I hope I've explained that clearly.

---

### Post by Elfy on 2011-04-24
> **frup said:**
> Do you symlink in to the relevant home directory directories?I don't  - but then I just point my media players where they need pointing.

> **The Cog said:**
> It's a good idea. User settings tend to collect cruft with time, and this time round I'm going through a process of deleteing all my user settings except for a few select programs (firefox bookmarks, thunderbird email settings etc).Just an example - I have my spare mounting on /mnt/spare.

Effectively you can call it anything you want - I'd just not have spaces. 

In addition to the additions - you can also not have a seperate /home partition and as long as when you reinstall you don't allow / to be formatted then /home stays. Done this once or twice.

Further - > so that i can either keep or avoid the application settings in my /home when i go for another installationif this is the case then I would be inclined to _not_ have a seperate /home and just backup the config's for those apps you _did_ want to keep.

---

### Post by candtalan on 2011-04-24
I have used your approach for some years now, it is so useful to be able to keep  /home/user clean, if I want. It is also simpler to decide about data backup.
However, I went onwards from the partition idea and used separate data drives. I think I usually mount these after an install process, I cannot remember. They are connected in anyway before installation begins, and I think they get auto mounted from Places or in file manager nautilus when I later use Ubuntu.

But because I use the two drives all the time, well one is, but the other is used to contain a complete copy of the first data drive, taken once per day, I 
configure fstab to permanently mount them. My fstab entry is:

```

#data-a
/dev/sdb1 /media/data-a ext4 defaults,users 0  0
#data-b 
/dev/sdc1 /media/bak-data-b ext4 defaults,users 0  0

```

I also run more than one installation of Ubuntu on the machine (different versions, whatever, on sda) so the common data drive is even more useful with that.

An aside comment: 
I know I am not using UUIDs here, but I do sometimes.....

---

### Post by steninj on 2011-04-24
> **forestpiskie said:**
> As far as the data partition goes - create the partition and mount it in fstab. I do all of this _after_ I've installed. 

I prefer to have my data partitions mount in /mnt - this way I can allow removable drives to appear on my desktop - but not the data drives. If you want them to be on the desktop then mount them in /media

I've a music drive in /mnt/music

The corresponding line in fstab for _my_ drive is
```

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
```

You can find uuid for your partitions with 

```
sudo blkid
```

To edit fstab after backing it up

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
thank you for that valuable info..

but try to understand my situation... 

i don't have much idea about ubuntu..

can u help me with step by step instructions..

situation is  i have a live cd with me and all files in my system has back up...

i am ready for a fresh installation of ubuntu alone,NOt dual boot

---

### Post by Elfy on 2011-04-24
Assuming that you want to make a home and data partition then.

Boot the livecd.

Open gparted (or partition editor) from the system admin menu

Select all existing partitions - mark for deletion - apply

You now have a blank slate

Create your partitions.

right click the unallocated space - create an extended partition - apply

right click inside the extended - create a swap partition - read here [https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?](https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?) 


(also if you need hibernate or swap ignore that and swap should at least be equal to RAM)
- apply

right click inside the extended - create a logical - 10-15Gb in size - ext4 - apply

right click inside the extended - create a logical - make this as large as you want your /home to be - ext4 - apply

right click inside the extended - create a logical - use whatever is left - this will be your data - ext4 - apply

Once all the partitions are created - exit and start the install procedure.

Once you reach the partition section - pick manual or advanced.

There will be a representation of the partitions you just created.

Pick the 10-15Gb partition - edit - pick / as the mountpoint
Pick the home partition - edit - pick /home as the mountpoint.

You might be able to apply a mount point for the data partition here - not sure. If not we can pick that up once you've installed.

Once mountpoints are created - carry on with the install.


Edit - that probably looks worse than it is - once you've created one partition the others will be easy. Same as the edit and set mountpoint.

---

### Post by steninj on 2011-04-24
> **forestpiskie said:**
> 
[SIZE=3]
You might be able to apply a mount point for the data partition here [/SIZE]- not sure. If not we can pick that up once you've installed.

Once mountpoints are created - carry on with the install.


Edit - that probably looks worse than it is - once you've created one partition the others will be easy. Same as the edit and set mountpoint.

thnk you so much [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428") for your valuable help...

you specified a mount point for data partition, [SIZE=3]what should be the mount point?[/SIZE]..

i think a mount point is necessary here..


everything else is clear from your explanation...

:)
thank u everyone

---

### Post by steninj on 2011-04-25
well.. that should be mount using fastab,right?...

ok...

now i i have my data partition in places/my computer/root/mnt

it looks fine,but am not much satisfied ;)
y can't i mount it directly in home?.

thank to [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428"), 
now

can anybody tell me how to use[SIZE=2] symlink method.[/SIZE].


:)

---

### Post by Elfy on 2011-04-25
In a terminal 

ln -s /path/to/real/file /path/to/non-existant/file

So assuming data is in /mnt/data

ln -s /mnt/data /home/yourusername/whatyouwanttocallit

---

### Post by srs5694 on 2011-04-25
> **steninj said:**
> my plan is to install it with a [SIZE=2]separate home partition and a separate data partition[/SIZE]...

so that i can either keep or avoid the application settings in my /home when i go for another installation


&
i always want to keep my datas like movies,music etc in an another partition...
i want this to be 100% untouched in every further installations..

There's seldom any advantage to this configuration over simply using a separate /home partition, and there are disadvantages to it. (Note I've *not* included an "IMHO" or even "IMO" in that statement.)

If you create a separate /home partition but no separate data partition, you can easily achieve your goal of starting with a fresh set of configuration files simply by using a different user home directory on your next installation. Note that a user home directory is a subdirectory within /home, such as /home/fred or /home/mary. You could do this while keeping your current username by renaming the original home directory or by using more advanced account-creation tools to create an account that uses a home directory that doesn't match the username. After installing, you'd then move the data files and directories you want to keep from the old installation over to the new user home directory. If you want to use both directories (say, to dual-boot an old and a new version of Ubuntu), you can set up symbolic links between the user home directories.

Since the /home directory is intended to be the user data directory, creating both /home and user data partitions essentially duplicates the purpose of a single partition. This creates a number of problems, such as:


[list]
[*]**Partition sizing** -- Deciding how to size the partitions can be tricky. If you decide wrong, you'll have to resize partitions, which is always risky and time-consuming. This reason alone is a very compelling argument against creating separate /home and data partitions.
[*]**Navigation** -- Navigating between the two partitions can be awkward, although the extent of the awkwardness depends on where you mount the data partition and what utilities you use to do the navigating.
[*]**Link maintenance** -- Some have suggested using symbolic links, implicitly to help with the previous issue. The links themselves require maintenance, though. (You'd have such issues with a dual-boot configuration and a single /home partition, but in that case this issue applies equally to both configurations, so it doesn't help the argument for using separate partitions.)
[*]**Multiple account maintenance** -- If you create multiple accounts, you'll have to manually create appropriate user directories in the data partition, or write a custom account-creation script to do this automatically. Note that even a single user can sometimes benefit from multiple accounts -- say, to try out a new configuration without risking the original one.
[/list]


The one advantage I can think of to creating separate /home and data partitions is that you can take advantage of different filesystem features or mount point options on the two partitions. For instance, if you wanted to keep both large numbers of very small files and very small files, you could use ReiserFS for the small-file partition and XFS for the large-files partition. (ReiserFS can cram more small files into a given partition size than can most other filesystems; and XFS works particularly well with large files.) Similarly, if some of the data was intended to change very rarely, you could mount that partition read-only, thus protecting it from accidental changes. I don't think that either of these advantages is likely to apply to a typical user desktop installation, though. Ext4fs is a good general-purpose filesystem, and even ext3fs, ReiserFS, JFS, and XFS work well enough for most purposes that a typical desktop user wouldn't benefit much by using two different filesystems. Ordinary Linux permissions can be used to keep the even the owner from erasing or overwriting files, if that's an issue.

Some people use a separate data partition and keep /home in the root (/) partition. This has most of the same drawbacks as separate /home and data partitions, but sizing isn't an issue, so that's a much less problematic configuration. Keeping your original configuration files can require a backup and restore operation if you completely wipe the installation partition during a re-installation, though.

The bottom line: Linux's designers intended /home to be where most user data are stored. Putting user data elsewhere is certainly possible, but it's re-inventing the wheel. An understanding of accounts and placing /home on its own partition will get you what you want in 99% of the cases.

---

### Post by Paddy Landau on 2011-04-25
> **srs5694 said:**
> There's seldom any advantage to this configuration over simply using a separate /home partition, and there are disadvantages to it...
+1. The one exception is where you have two or more physical disks, and then the decisions depend on your setup.

With the low price of modern storage, and the fact that Ubuntu can easily fit on 10Gb, you are absolutely right.

---

### Post by srs5694 on 2011-04-25
> **Paddy Landau said:**
> +1. The one exception is where you have two or more physical disks, and then the decisions depend on your setup.

I forgot about that possibility. In that situation, though, I personally would use an LVM configuration. It's a bit of a pain to set up, especially in Ubuntu, but it greatly increases flexibility in multi-disk setups. In particular, you can have one big /home logical volume that spans multiple disks. Aside from being harder to set up, LVM also has the drawback that if one drive fails, you're likely to lose all the data on both drives. If you keep good backups, though, IMHO the advantages outweigh the disadvantages.

---

### Post by Paddy Landau on 2011-04-26
> **srs5694 said:**
> ... In that situation, though, I personally would use an LVM configuration...
I had not heard about LVM before. I [looked it up]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29") and it looks great. Something to remember, thank you.

---

### Post by Kevin McCready on 2013-01-14
> **srs5694 said:**
> The one advantage I can think of to creating separate /home and data partitions is that you can take advantage of different filesystem features or mount point options on the two partitions. 

I have to admit I haven't understood all the above discussion. But isn't there another advantage. I want to simply backup my system (not my data) so I can reinstall if I need. I'm thinking of using the dd command. If I did that, and I didn't have a separate partition for my data, wouldn't I end up with a huge iso?

---

### Post by Paddy Landau on 2013-01-14
> **Kevin McCready said:**
> … I want to simply backup my system (not my data)
Look at [CloneZilla]("http://www.clonezilla.org/") (flexible, not very user-friendly) and [RedoBackup]("http://redobackup.org/") (less flexible, but user-friendly).

---

### Post by overdrank on 2013-01-14
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

