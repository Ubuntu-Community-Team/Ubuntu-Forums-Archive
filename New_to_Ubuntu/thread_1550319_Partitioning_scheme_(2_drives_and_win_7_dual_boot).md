---
title: "Partitioning scheme (2 drives and win 7 dual boot)"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-08-10
Hello,

I have installed ubuntu thru Wubi about a week ago and I am really impressed of the improvements since the last time I have installed it. I am about to format and repartition my drive to make a proper installation of it. I will re-install Win 7 for some of my games till they are supported in a distro (having issues with Asheron's call).

So, I have seen but lost a thread here that was saying that for a dual boot, 2 drive installation, I should, on drive #1, put 50% for win, 48% for Linux and 2% for /Swap, on the second drive, a partition for files that both OS can access, another 2% for swap ( to have the linux advantage of swap on different drives) but I dont remember the rest. 

I have 2 X 320 GB drives, I am on a notebook, Intel Centrino duo quad core 2.0Ghz, 4 GB ddr3, and Nvidia GTX260M with 1Gb DDR3.

Question is, does this scheme seems ok and what is it missing ? (/boot, grub, /home etc...), Which order should I do it or do I have to go windows first but partition with Live CD first ?

I know my way around in Linux, I can do a lot of things in it and fix problems has they arise or, find the answer to it. I have been playing with computer since Daddy bought a TI99-A and Terminal does not scare me off, it attracks me so, should I look into another distro/flavor or go with ubuntu and wait till Wine support the games I still want to play ? 

I am off work for rest of life for a Thoracic outlet Syndrome (see in my signature if you want to know more and no, it is not to get you to give :) ) so now, I do have a lot of time to invest into Linux and learn it properly :) 

Thanx for the help :)

---

### Post by Ozymandias_117 on 2010-08-10
> **Mobidoy said:**
> Hello,

I have installed ubuntu thru Wubi about a week ago and I am really impressed of the improvements since the last time I have installed it. I am about to format and repartition my drive to make a proper installation of it. I will re-install Win 7 for some of my games till they are supported in a distro (having issues with Asheron's call).

So, I have seen but lost a thread here that was saying that for a dual boot, 2 drive installation, I should, on drive #1, put 50% for win, 48% for Linux and 2% for /Swap, on the second drive, a partition for files that both OS can access, another 2% for swap ( to have the linux advantage of swap on different drives) but I dont remember the rest. 

I have 2 X 320 GB drives, I am on a notebook, Intel Centrino duo quad core 2.0Ghz, 4 GB ddr3, and Nvidia GTX260M with 1Gb DDR3.

Question is, does this scheme seems ok and what is it missing ? (/boot, grub, /home etc...), Which order should I do it or do I have to go windows first but partition with Live CD first ?

I know my way around in Linux, I can do a lot of things in it and fix problems has they arise or, find the answer to it. I have been playing with computer since Daddy bought a TI99-A and Terminal does not scare me off, it attracks me so, should I look into another distro/flavor or go with ubuntu and wait till Wine support the games I still want to play ? 

I am off work for rest of life for a Thoracic outlet Syndrome (see in my signature if you want to know more and no, it is not to get you to give :) ) so now, I do have a lot of time to invest into Linux and learn it properly :) 

Thanx for the help :)

You can create separate /boot /usr /home /var but it's not needed.

My suggestion based on what you've posted, would be to partition your first drive 50% for windows 50% for Linux (Or whatever sizes you want for them. If you're not going to store any media files on the Linux partition, just programs from repos, etc. 20 Gigs should be plenty)

Then make a Swap partition 1.5x the amount of RAM you have (You will need this for Hibernate/Stand By) on your second drive. Then make the rest of your second drive for data. (NTFS or Fat32 so Windows will use it :P Remember that Fat32 can't store files larger than 4Gigs)

Edit: There isn't any reason to make two swap partitions.

---

### Post by Mobidoy on 2010-08-10
> **Ozymandias_117 said:**
> You can create separate /boot /usr /home /var but it's not needed.

My suggestion based on what you've posted, would be to partition your first drive 50% for windows 50% for Linux (Or whatever sizes you want for them. If you're not going to store any media files on the Linux partition, just programs from repos, etc. 20 Gigs should be plenty)

Then make a Swap partition 1.5x the amount of RAM you have (You will need this for Hibernate/Stand By) on your second drive. Then make the rest of your second drive for data. (NTFS or Fat32 so Windows will use it :P Remember that Fat32 can't store files larger than 4Gigs)

Edit: There isn't any reason to make two swap partitions.

Ok so, on first drive, 160GB~(NTFS) for win7 and 160GB~(EXT3 ???) for Ubuntu, on the second drive, 6Gb(SWAP) and the rest for files (NTFS) for Both ? Nothing for Grub ? and with all that free space, should I try another/other Distro(s) ?

---

### Post by Ozymandias_117 on 2010-08-10
> **Mobidoy said:**
> Ok so, on first drive, 160GB~(NTFS) for win7 and 160GB~(EXT3 ???) for Ubuntu, on the second drive, 6Gb(SWAP) and the rest for files (NTFS) for Both ? Nothing for Grub ? and with all that free space, should I try another/other Distro(s) ?

I feel like I see a performance increase with Ext4 over Ext3, and I've never had any problems with it, so I would suggest Ext4. Grub doesn't NEED it's own partition, and I don't bother with a separate /boot unless I'm setting up a server.

I've not personally tried it, but I've heard really good things about Fedora 13. (One swap partition for all your distros is enough)

---

### Post by Mobidoy on 2010-08-10
> **Ozymandias_117 said:**
> I feel like I see a performance increase with Ext4 over Ext3, and I've never had any problems with it, so I would suggest Ext4. Grub doesn't NEED it's own partition, and I don't bother with a separate /boot unless I'm setting up a server.

I've not personally tried it, but I've heard really good things about Fedora 13. (One swap partition for all your distros is enough)

Ok, last question before I jump in :) I have the 64 bits version installed and all was well but, on the Ubuntu download page, it says that:

32-bit - Recommended for most users
64-bit - Not recommended for daily desktop usage

Should I really go with 32 (and prevent possible hardware compatibilty issues) or 64 is fine ?

---

### Post by Ozymandias_117 on 2010-08-10
> **Mobidoy said:**
> Ok, last question before I jump in :) I have the 64 bits version installed and all was well but, on the Ubuntu download page, it says that:

32-bit - Recommended for most users
64-bit - Not recommended for daily desktop usage

Should I really go with 32 (and prevent possible hardware compatibilty issues) or 64 is fine ?

No, that's a bug. It's been a bug for like 4 releases. It's even listed as a bug on launchpad. Not sure why it hasn't been changed. (Unless they are leaving it like that so people who don't know anything about computers download the 64-bit and try to install it on a p3 ;))

---

### Post by oldfred on 2010-08-10
I look at system partitions and data partitions as two different types and they should be separate. When I was using windows more I had a shared NTFS partition, but now my shared is used very little and most of my data is in a /data partition. You can have either a separate /home if only having Ubuntu and upgrading or /data, as you should not share /home with other distros. I use 20-25GB for / (root) (size actually used is now only 6GB) and have 3 Ubuntu system partitions plus a couple  of additional partitions that I have not used to try other systems. I mount my data in all of them so I have the same data everywhere. With all my data out of /home my /home is only 1GB. 

If you are not sure what you plan to do you do not have to allocate all your drive space but make sure it is in the extended partition so you can add partitions.

---

