---
title: "Partition Sizes and File System"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by ChappyHappy on 2009-10-30
Hi, I'm new to Ubuntu and I want to dual boot Vista and Ubuntu (both 64bit) on my 250GB HD.

I plan to use Ubuntu mainly with Vista for programs that I cant get to work in Ubuntu.

After reading multiple threads and guides...
I'm planning to have the following partitions:

Vista, 70gb, ntfs (primary)
Data, 90gb, ntfs (logical)
Ubuntu /, ??, ?? (primary)
Ubuntu /home, ??, ?? (primary)
swap, 4, -- (??)


I planned Data after Vista in case I need to give more HD space to Vista later, and in ntfs so it's accessible by both Ubuntu and Vista if expanding for Vista is not required. I dont plan to have any extended partition later on either.
I know /home is useful for reinstalling ubuntu.  And / is for installing programs for ubuntu.
The problem is I dont know what to set the sizes and file system for / and /home.

From my understanding, "/" is equivalent to C:\windows and "/home" is the Document and Setting. What is the Program Files equivalent? I was planning to give / 80gb and /home 6gb. But Tberk's screenshot confused me with /home having more space than / [[IMG]http://s473.photobucket.com/albums/rr96/DrFrankenBerk/?action=view&current=Screenshot.png[/IMG]]("http://s473.photobucket.com/albums/rr96/DrFrankenBerk/?action=view&current=Screenshot.png")

And I read in a post somewhere that 64bit Ubuntu uses jfs instead of ext3/4, but I cant find it again in any document/guides.

So basically:
-What should the partition sizes for / and /home be?
-What file system should / and /home use?
-Am I using the correct partition types (primary and logical)?
-Would my partitions be sufficient for me?

Thanks

---

### Post by Marflus on 2009-10-30
> From my understanding, "/" is equivalent to C:\windows and "/home" is the Document and Setting. What is the Program Files equivalent? I was planning to give / 80gb 

You can't really make this sort of equivalence between linux and windows. The two Operating Systems organise their files in fundamentally different ways, and so direct comparisons are tough to find. For example, there is no "Program Files" in Ubuntu - Software can be installed in a number of different locations, and their executable files are stored in another folder altogether.

/ is the root of your Ubuntu install, and therefore unless (like you are planning to do) you place some parts on other partitions, it would take up the vast majority of your available Hard Drive space. Since you're giving /home it's own partition, you'll find that / doesn't usually require a vast amount of space - I personally get by just fine on 15Gb, and some might use less. swap is space used when the system runs out of RAM - guidance is to use about 1-2 times the amount of RAM in your system here. /home contains pretty much everything relevant to the users, including all the program configuration files and folders, all your personal documents, etc. For this reason, it's generally big. Any space left on your system after swap and / should go into /home.

I've never had any problems using 100% primary partitions on Ubuntu, but that may not be a good idea, I don't know. I don't claim to be an expert in that area, so...

I don't know that 64bit uses jfs, if it does obviously that's the way to go. Otherwise, ext4 is the latest and greatest filesystem available for Ubuntu.

I think that's all...Sorry I can't help more with those last bits, hopefully someone else will have something to say on the subject.

Edit: Oh, and the Data partition. Why? I suppose it would make things more organised, but since "Vista" is NTFS anyway, wouldn't it make sense to put all that storage in one partition? Ubuntu can still use any space you don't use on the Vista partition, and you don't have the worry of altering the partitions in the future if Vista gets too big for it's initial partition.

---

### Post by Peter09 on 2009-10-30
During the installation process you can just allocate a chunk of disk to Ubuntu by size. The installer will then decide the sizes of \ and swap. 

By default the home directory is part of the \ partition. 

As a beginner this is the best way to install Ubuntu. Take the automated route as much as possible. 

Note - I am unsure if Vista is already installed on your machine, but you cannot install Vista after Ubuntu as Vista takes no notice of your other O/S and will over write the  boot record.

---

### Post by ChappyHappy on 2009-10-30
Ah, sorry, I had a feeling I left some info out in my rush to post.
Vista is already installed. I currently have 3gb RAM on the lappy and planning to expand to 4gb later.

Thanks everyone, I think I understand it now. I'll go:

Vista  , 70gb  , ntfs (primary)
/home, 150gb, ext4 (primary)
/        , 15gb  , ext4 (primary)
swap  , 4gb   , ?? (logical)

I'll use /home for shared data also.
But the only problem I see is since I'm using /home for shared data also would Vista be able to read ext4? I know there are programs to allow it to read ext3, but google comes up empty for ext4.

---

### Post by John Bean on 2009-10-30
Unless you have a very good reason to do otherwise I stongly advise you to adopt the default installation of a single partition (mount point "/") and a swap partition. Making /home a separate partition on a (single disk) laptop is a bit pointless; had it been a desktop machine with multiple disks it would have made sense.

If you want a shared data partition then NTFS is a good choice since Ubuntu can handle this better (and more importantly reliably) than Vista can deal with LInux partitions.

---

### Post by Marflus on 2009-10-30
> Making /home a separate partition on a (single disk) laptop is a bit pointless

It is? Having a separate /home means that you can install various linux distributions and keep the same /home folder, as well as allowing you to reinstall ubuntu without losing the data in /home should you need to. Of course, you should always keep a backup anyway, but that should go without saying.

---

### Post by ChappyHappy on 2009-10-30
Yea, I plan to have /home so it'll be easier to install a newer version of Ubuntu (or maybe a different distro).

Yea, I was gonna go with NTFS cause of those same reasons, but I couldnt find the option to choose NTFS so I just went with all ext4 and hope a ext4 driver for Vista would be released soon.

Thanks for all your posts!

---

### Post by John Bean on 2009-10-30
> **Marflus said:**
> It is? Having a separate /home means that you can install various linux distributions and keep the same /home folder, as well as allowing you to reinstall ubuntu without losing the data in /home should you need to. Of course, you should always keep a backup anyway, but that should go without saying.

My comment was in the context of this query, the tone and content of which implied the OP was a newcomer to this sort of thing. My advice is basically KISS, that's why it started with the words "Unless you have a very good reason to do otherwise". Multiple installations could be such a reason.

---

