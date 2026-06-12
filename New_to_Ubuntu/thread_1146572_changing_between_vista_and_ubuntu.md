---
title: "changing between vista and ubuntu"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by jammie72 on 2009-05-02
hi. looking for wise words and wisdom please....
can i download the new ubuntu and run windows vista aswell, so as i can chop and change? i believe this was the case with the 8.10 but don't want to start downloading and it not work now. got a new laptop so don't want to loose all the programmes i have in the vista side. :confused: thanks

---

### Post by freak42 on 2009-05-02
what do you mean by 'chop and change'.

are you looking for dual-boot installation instructions?

---

### Post by Monotoko on 2009-05-02
chop and change is a saying meaning change between them, yes you can, the ubuntu installation will give you an option to do so :)

---

### Post by Delever on 2009-05-02
I found some site with google which has illustrated instructions of everything you may encounter:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by presence1960 on 2009-05-02
> **jammie72 said:**
> hi. looking for wise words and wisdom please....
can i download the new ubuntu and run windows vista aswell, so as i can chop and change? i believe this was the case with the 8.10 but don't want to start downloading and it not work now. got a new laptop so don't want to loose all the programmes i have in the vista side. :confused: thanks

First you want to defrag the hard disk at least once to insure all files are at the beginning of the drive in Vista. Then using Vista's partitioner you want to create your Ubuntu partition. A few people in here have mentioned Vista freaked when they used the Ubuntu Live CD or gparted Live CD to create the partition.

Once that is done you have 2 choices: use the entire new partition for Ubuntu by booting the Ubuntu Live CD and choosing the manual option at the partitioner screen. Select your new partition as the install location and proceed with the install. Or if you want a separate /home partition then use the Ubuntu Live CD to create separate partitions from the new partition. You can then use the manual option at the partitioner screen to choose which partitions are mounted as "/", "/home" and swap. 

You can use BCD from that link provided by Delever, but I am not a fan of that. I would install GRUB to sda.

P.S. i would back up your Vista recovery partition to an external HDD and if your manufacturer gives you the option to burn 1 set of bootable CDs/DVDs from the recovery partition I would do that also. 99.9% of the time partitioning is uneventful. But there is always the chance something can happen. So back up first always!

---

### Post by -kg- on 2009-05-02
> Then using Vista's partitioner you want to create your Ubuntu partition. A few people in here have mentioned Vista freaked when they used the Ubuntu Live CD or gparted Live CD to create the partition.

Oh LORD NO!  Vista's partitioner *_will not_* create a Linux (ext2/ext3/ext4) partition, nor will it create a swap partition.  What you need to do is to shrink the existing Vista partition with Vista's partitioner, leaving free space into which you can install Ubuntu, creating the Linux partitions with GPartEd which is used by the Ubuntu installer.

Then after shrinking the Vista partition, boot into the LiveCD and start the installation process.

All the rest of the information is correct, however.  First defrag your Vista partition at least once (more, if possible), back up the data from the partition (hopefully you have another hard drive, preferably external and definitely larger...otherwise, depending on the size and amount of data on the partition, you will need a ****load of CDs or DVDs), shrink the Vista partition from Vista's Disk Management, then boot on to the Jaunty Live CD and perform the installation.

More information on partitioning operations can be found on the following page:

[How To Partition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by presence1960 on 2009-05-02
> **-kg- said:**
> Oh LORD NO!  Vista's partitioner *_will not_* create a Linux (ext2/ext3/ext4) partition, nor will it create a swap partition.  What you need to do is to shrink the existing Vista partition with Vista's partitioner, leaving free space into which you can install Ubuntu, creating the Linux partitions with GPartEd which is used by the Ubuntu installer.

Then after shrinking the Vista partition, boot into the LiveCD and start the installation process.

All the rest of the information is correct, however.  First defrag your Vista partition at least once (more, if possible), back up the data from the partition (hopefully you have another hard drive, preferably external and definitely larger...otherwise, depending on the size and amount of data on the partition, you will need a ****load of CDs or DVDs), shrink the Vista partition from Vista's Disk Management, then boot on to the Jaunty Live CD and perform the installation.

More information on partitioning operations can be found on the following page:

[How To Partition]("https://help.ubuntu.com/community/HowtoPartition")

I know that! But it will shrink the Vista partition and make an unformatted partition which then can be used for Ubuntu. I never said create an ext3 partition, I said create a partition for Ubuntu then use the Live CD to install to that partition or to make "/" "/home" and swap from that one.. I guess I could have been more clear.

---

### Post by bennachie on 2009-05-02
All the original poster has to do to try out Ubuntu in perfect safety is to boot into Vista, download the Ubuntu LiveCD iso, then download the latest version of Wubi.exe from <http://wubi-installer.org/>. He can then run Wubi as a normal Windows application, point it at the iso, and install Ubuntu, in effect, within the Windows environment. once thus installed, Ubuntu can later be uninstalled at any time (not that most people will be tempted to do so unless they plan to move to a dual-boot framework).

Yes, I know that the LiveCD includes Wubi, but a few people have had problems with the earlier version of Wubi that was included at the time of the original release - I'm not sure whether the current iso downloads have been quietly updated.

Partitioning for a true dual-boot environment is appropriate once you know that you like Ubuntu and want to get the maximum possible performance out of the system. That having been said, Ubuntu running under Wubi is a lot snappier than Windows Vista anyway!

---

### Post by presence1960 on 2009-05-03
> **bennachie said:**
> That having been said, Ubuntu running under Wubi is a lot snappier than Windows Vista anyway!

Anything is faster than Vista :lolflag:

I never recommend Wubi because I have never seen it, never used it and therefore don't know how it works or installs. This does not mean it is not a viable option for people, it is just I am not qualified to say anything about it. So now the OP has another option to consider.

---

### Post by -kg- on 2009-05-03
> **presence1960 said:**
> I know that! But it will shrink the Vista partition and make an unformatted partition which then can be used for Ubuntu. I never said create an ext3 partition, I said create a partition for Ubuntu then use the Live CD to install to that partition or to make "/" "/home" and swap from that one.. I guess I could have been more clear.

Either you don't understand some concepts of partitioning, or I'm not understanding what you are getting at.

When you shrink the Vista partition, it does not create an unformatted partition; it frees up space in which you can then create a partition.  The Vista partitioner can create an unformatted partition in that free space (when you create the partition, there is an option that allows you to leave it unformatted), but under other circumstances that would be a hindrance rather than helpful.

If you do create an unformatted partition in that free space, then when you boot to the Live CD and install Ubuntu, you no longer have the option to install it "In The Largest Contiguous Free Space,"  since the free space that would otherwise exist contains the unformatted partition.  You would be forced to use the Manual partitioning option.

Once there, especially if you don't already have a swap partition, you would be forced to shrink the unformatted partition in order to leave room for the swap partition, mark the unformatted partition for formatting to the proper format, and create the swap file.

Nonetheless, I think what you are doing is considering the free space created as an unformatted partition.  It isn't.  A partition can be created in that free space, and it can be left unformatted, if you desire (though for what reason I can't imagine, but it can be done).

Don't believe me?  Launch GPartEd, select some free space and create a new partition then click on the File System drop down box.  At the very bottom is the selection "Unformatted."  Vista has this too.

That's why I reacted so when you said to make an unformatted partition for Ubuntu.  I've been partitioning hard drives for 15 years and more, and when I hear something that is not right (and someone might see that they are able to create an unformatted partition and do it on instruction) it jumps out at me and I react to it.

8-[

---

### Post by presence1960 on 2009-05-03
> **-kg- said:**
> Either you don't understand some concepts of partitioning, or I'm not understanding what you are getting at.

When you shrink the Vista partition, it does not create an unformatted partition; it frees up space in which you can then create a partition.  The Vista partitioner can create an unformatted partition in that free space (when you create the partition, there is an option that allows you to leave it unformatted), but under other circumstances that would be a hindrance rather than helpful.

If you do create an unformatted partition in that free space, then when you boot to the Live CD and install Ubuntu, you no longer have the option to install it "In The Largest Contiguous Free Space,"  since the free space that would otherwise exist contains the unformatted partition.  You would be forced to use the Manual partitioning option.

Once there, especially if you don't already have a swap partition, you would be forced to shrink the unformatted partition in order to leave room for the swap partition, mark the unformatted partition for formatting to the proper format, and create the swap file.

Nonetheless, I think what you are doing is considering the free space created as an unformatted partition.  It isn't.  A partition can be created in that free space, and it can be left unformatted, if you desire (though for what reason I can't imagine, but it can be done).

Don't believe me?  Launch GPartEd, select some free space and create a new partition then click on the File System drop down box.  At the very bottom is the selection "Unformatted."  Vista has this too.

That's why I reacted so when you said to make an unformatted partition for Ubuntu.  I've been partitioning hard drives for 15 years and more, and when I hear something that is not right (and someone might see that they are able to create an unformatted partition and do it on instruction) it jumps out at me and I react to it.

8-[

I think we are just talking semantics here. Maybe I am using terms differently than you. I have shrunk a vista partition. Now whether it was free space or unformatted seems to be the sticking point. Thinking back it may have been free space. Nevertheless once this partition or free space was created I then used the Ubuntu live CD to install Ubuntu using the manual option of the partitioner. I always use the manual option. This was way back in August and I haven't used Vista since. I was going from memory which isn't always the best thing to do. But I do take note of what you said and always appreciate critique from community. I only use Windows for work, and I was so glad to "downgrade" to XP, I really didn't like Vista.

---

### Post by Megrimn on 2009-05-03
Nice convo we have going, here.


Well, I am dual booting Vista and Hardy, and here is how I did it:

-Yes, it is a very good idea to defrag Vista before you do anything else.  

-Then boot the liveCD.

-open the partition editor, and resize the Vista partition to your liking. Don't touch the recovery partition, if you have one. Most if not all Vista machines do.

[note] on my 250gb HDD, the recovery partition takes up 10gb.  I gave Vista 170gb because I was already using at least 70gb and Vista is a gig-sucking vampire.  There was 60gb left for ubuntu, and I still have 44gb left.

-So when you are done resizing vista, install ubuntu.  the installer should have an option where ubuntu just fills the free space on your HDD.

If you need more help, just ask. :)

---

### Post by Noise... on 2009-05-03
> **jammie72 said:**
> hi. looking for wise words and wisdom please....
can i download the new ubuntu and run windows vista aswell, so as i can chop and change? i believe this was the case with the 8.10 but don't want to start downloading and it not work now. got a new laptop so don't want to loose all the programmes i have in the vista side. :confused: thanks

Yes - it's very, very easy to set up a dual boot with Vista. 

Simply follow the install instructions on the Ubuntu disk to get started. Resize Vista's partition, then select to automatically partition the free space for Ubuntu. This should automatically make the \ partition as well as the swap partition for Ubuntu.

Proceed through the install, and the two new partitions will be used. Also, GRUB Bootloader will be installed, which will allow you to choose which OS to boot into. 

If your computer has a recovery drive, you have to be careful when booting into Vista. The recovery partition CAN be booted, which will cause the recovery partition to boot. In my case, the recovery partition is first on the drive, so it's the first "Windows Vista" that is bootable, while the second "Windows Vista" is my actual Vista install.

---

### Post by -kg- on 2009-05-03
> **presence1960 said:**
> I think we are just talking semantics here. Maybe I am using terms differently than you. I have shrunk a vista partition. Now whether it was free space or unformatted seems to be the sticking point. Thinking back it may have been free space. Nevertheless once this partition or free space was created I then used the Ubuntu live CD to install Ubuntu using the manual option of the partitioner. I always use the manual option. This was way back in August and I haven't used Vista since. I was going from memory which isn't always the best thing to do. But I do take note of what you said and always appreciate critique from community. I only use Windows for work, and I was so glad to "downgrade" to XP, I really didn't like Vista.

Yes, now that I've seen this post, I think it was semantics.  But I always try to use absolute semantics when I post (and it takes me time to compose my posts because of this), because someone who doesn't really know what they're doing will screw up if you don't (and I've seen it happen too often...here and elsewhere).

Yes, most certainly you freed up space and then installed Ubuntu in that free space.  The only reason I jumped is that you *can* create an unformatted partition in that free space, and if you aren't absolutely clear on that, there are some that will do that! #-o

I hear you on not liking to use Vista, and I will extend that to Windows in general.  Jaunty has been a major upgrade for me.  I was previously using Hardy, and I was having numerous issues that I was having major problems resolving.  To this point, they have all been resolved under Jaunty.

YouTube (and other) streaming videos seem to have been totally resolved for me.  There were several streaming videos that I was forced to boot into Vista in order to view...not so now.  Everything that I was having problems with seems now to be resolved (for me).  I'm impressed!

I apologize for the misunderstanding, but recognize my position that when proffering help on a help forum, I assume that who I'm helping is a complete idiot with computers until they prove otherwise, and will follow advice to the "semantic" letter, and they will find that option to create an unformatted partition.

The link that I provided above is to the Ubuntu Community Wiki page that I substantially re-wrote because the former page was lacking in some details that I thought was needed.  I need to re-write it again, since Jaunty has the ability to create and run from ext4, but I need to get used to it myself, before re-writing it, because ext4 is still relatively new and there are issues still being resolved with it.

Once again, have fun!

---

### Post by presence1960 on 2009-05-03
> **-kg- said:**
> Yes, now that I've seen this post, I think it was semantics.  But I always try to use absolute semantics when I post (and it takes me time to compose my posts because of this), because someone who doesn't really know what they're doing will screw up if you don't (and I've seen it happen too often...here and elsewhere).

Yes, most certainly you freed up space and then installed Ubuntu in that free space.  The only reason I jumped is that you *can* create an unformatted partition in that free space, and if you aren't absolutely clear on that, there are some that will do that! #-o

I hear you on not liking to use Vista, and I will extend that to Windows in general.  Jaunty has been a major upgrade for me.  I was previously using Hardy, and I was having numerous issues that I was having major problems resolving.  To this point, they have all been resolved under Jaunty.

YouTube (and other) streaming videos seem to have been totally resolved for me.  There were several streaming videos that I was forced to boot into Vista in order to view...not so now.  Everything that I was having problems with seems now to be resolved (for me).  I'm impressed!

I apologize for the misunderstanding, but recognize my position that when proffering help on a help forum, I assume that who I'm helping is a complete idiot with computers until they prove otherwise, and will follow advice to the "semantic" letter, and they will find that option to create an unformatted partition.

The link that I provided above is to the Ubuntu Community Wiki page that I substantially re-wrote because the former page was lacking in some details that I thought was needed.  I need to re-write it again, since Jaunty has the ability to create and run from ext4, but I need to get used to it myself, before re-writing it, because ext4 is still relatively new and there are issues still being resolved with it.

Once again, have fun!

No apology necessary, besides as I said I like feedback or critiqueing from the community. It helps me be better at this.

---

### Post by Capitolman on 2009-05-20
the way i did it was to use the free disc from CANONICAL and select to install in vista using WUBI. on startup you then have the choice of vista or ubuntu.the only problem i have is that the screen settings are not right, and so far i have not found out how to change them, the choices given do not fit my laptop.

---

