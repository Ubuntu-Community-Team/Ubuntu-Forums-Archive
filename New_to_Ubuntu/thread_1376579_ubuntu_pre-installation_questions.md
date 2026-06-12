---
title: "ubuntu pre-installation questions"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by mfsangabriel on 2010-01-09
Hi! I am very much interested in installing Ubuntu in my hard disk after trying out a Wubi install. I want to run both Windows and Ubuntu in my laptop and will probably switch to Ubuntu-only in the future. I have already freed up some space, defragged my drives and ran checkdisk for errors. My hard disk has a capacity of 150GB and has two partitions: C=60GB,NTFS and D=90GB,FAT32. I was about to install Ubuntu in the D partition when some questions popped up. Here goes:

1.  Is it ok to install in the existing D partition or do I have to create another one for Ubuntu? If either will do, what are the pros and cons?

2. Will installing Ubuntu in D wipe out all the data in the partition?

3. My DVD drive is E: and I have VirtualCD installed in Windows so F: is also taken as a virtual drive. If I were to create another partition can I use E: or F: and have no troubles or should I skip those two and use G: instead?

4. If a separate partition needed, is 20GB more than enough? (considering that Ubuntu only will run this laptop in the future.) 

5. What else do I need to know? : )

Hope anybody here could help me. I think I’ll be postponing the installation until I’ve read your advice. Thanks in advance!

---

### Post by bpalone on 2010-01-09
I can answer a couple of your questions.

Is 20 gig enough? ---- Yes

Will installing in your Fat32 partition destroy your data ----YES!!!!
It would wipe your Fat32 partition off of your HD.

You have a couple of options.  You can either use the Ubuntu Live CD and use GParted or you can download a GParted Live CD (do a Google search for Gparted) and resize your Fat32 partition to free up the 20 gig for your install of Ubuntu.  I prefer the GParted Live CD, but either will do.

[SIZE="7"]HOWEVER, BE SURE TO BACKUP YOUR DATA ON THE FAT32 PARTITION, BEFORE YOU DO ANYTHING.[/SIZE]

I haven't ever lost anything, but you never know and an ounce of prevention is worth way more than many, many hours of trying to recover with a non existent backup. In fact, it would be wise to back up your entire hard drive before doing anything, just as a safety measure.

If my memory serves correctly 8.04 LTS was recommended to have 10 gig of drive space.  It didn't use that much, but that gave some growing room.

Hope that helps you a bit.

---

### Post by mbzn on 2010-01-09
The installation is simple, as for your partitions, you can install Ubuntu on the (D: drive) but it is not recommended at all. rather try to free as much space on the drive that is not included in a partition. Then when installing Ubuntu select 'use largest continues free space'. It will be fine for the duel boot while you experiment. You can always after you delete your windoze partitions use that space for /home with the 15-20GiB as your /.(Which is way more than enough...)

---

### Post by kansasnoob on 2010-01-09
> **mfsangabriel said:**
> Hi! I am very much interested in installing Ubuntu in my hard disk after trying out a Wubi install. I want to run both Windows and Ubuntu in my laptop and will probably switch to Ubuntu-only in the future. I have already freed up some space, defragged my drives and ran checkdisk for errors. My hard disk has a capacity of 150GB and has two partitions: C=60GB,NTFS and D=90GB,FAT32. I was about to install Ubuntu in the D partition when some questions popped up. Here goes:

1.  Is it ok to install in the existing D partition or do I have to create another one for Ubuntu? If either will do, what are the pros and cons?

2. Will installing Ubuntu in D wipe out all the data in the partition?

3. My DVD drive is E: and I have VirtualCD installed in Windows so F: is also taken as a virtual drive. If I were to create another partition can I use E: or F: and have no troubles or should I skip those two and use G: instead?

4. If a separate partition needed, is 20GB more than enough? (considering that Ubuntu only will run this laptop in the future.) 

5. What else do I need to know? : )

Hope anybody here could help me. I think I&#8217;ll be postponing the installation until I&#8217;ve read your advice. Thanks in advance!

One of the first things you need to understand is how Ubuntu recognizes (names) drives/partitions:

[ATTACH]143031[/ATTACH]

I know that looks like a mess but I have Windows + 5 Linux operating systems each with a separate /home but sharing one SWAP. (Mostly for grub2 testing)

Anyway you can see from that my Windows (drive C) is recognized by Ubuntu as **sda1**. The a means drive #1, and the 1 means partition #1. Likewise sda2 = drive #1, partition #2, etc, etc.

The following guide generally describes how I like to prepare my partitions using Gparted before installing using the Manual (advanced) option:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

**Note: please disregard the stuff about a Dedicated GRUB Partition! You do NOT want one!** 

Also I like to create 3 partitions for my *buntus, the first / (aka: root) of about 6GB to 8GB, the second /Home whatever size I want, and the 3rd SWAP of usually about 1GB. Your individual partition sizes need to be determined by you.

There is some good general info here:

[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)

And here:

[http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

Note that there is a four primary partition limit so you should use an extended partition to "house" some of your Ubuntu "logical" partitions as I have.

One thing that would be very wise before resizing any NTFS or FAT32 partition is to defrag it with your Windows defrag tool first.

Some form of backup is also incredibly wise because there is always a danger of data loss when resizing partitions, installing operating systems, etc.

Oh, and try the Ubuntu Live CD before installing! Then try it some more! If graphics, sound, etc don't work from the Live CD you'll know you have some work ahead of you after installation!

---

### Post by J V on 2010-01-09
> **mfsangabriel said:**
> 1.  Is it ok to install in the existing D partition or do I have to create another one for Ubuntu? If either will do, what are the pros and cons?If you install in the existing one it will wipe out your windows, you need to make a different one

> 2. Will installing Ubuntu in D wipe out all the data in the partition?Yes, you need to shrink the D partition and then make a new ubuntu one in the leftover space

> 3. My DVD drive is E: and I have VirtualCD installed in Windows so F: is also taken as a virtual drive. If I were to create another partition can I use E: or F: and have no troubles or should I skip those two and use G: instead?The letters are just the way windows refers to them, linux doesn't have letters, partitions are just loaded like a regular folder. Ignore the letters, windows will do it itsself.

> 4. If a separate partition needed, is 20GB more than enough? (considering that Ubuntu only will run this laptop in the future.) More than enough... not if you download movies but yes, more than enough

> 5. What else do I need to know? : )Backup backup backup...

Make an extended partition so you don't run out of slots, then inside this make 3 logical partitions.

A 6 gig for /
A 1 gig for swap (Virtual memory)
and the rest for /home (where all your stuff is)

This lets you install another version and keep all your stuff...

Once ubuntu is in there will be lots to do, I suggest installing ubuntu-restricted-extras first :)

---

### Post by mfsangabriel on 2010-01-10
Thanks for the help! I was thinking bout skipping the backup part coz I was quite excited and my external HD's not with me right now. I'll just install Ubuntu when I get home. I'll just follow the links and download gparted. :) 

Thanks again!

---

