---
title: "CD corrupt on install - post partition"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-03-22
Just a question to confirm that i am doing the correct thing.

I just went to dual install ubuntu using the live CD. I successfully partitioned the hard drive but then while UBunutu was installing i got a msg telling me that there was a problem with the CD - either a problem with the lens or with the CD. I was then instructed to either write another CD at a slower speed or clean my lens.

After i clicked 'Ok' on this msg the computer ran a DOS-type screen with whole bunch of text - virtually none of which i understood - before hanging. I eventually powered down.

When i restarted, my machine booted straight to windows. When i check the hard disk in windows i see that the available hard disk is the size i set it to post partition.

So now i think that the partition has worked, but that the GRUB installer has not loaded. Clearly Ubuntu has not been installed. I think then that i need to reinstall Ubunutu and recover the GRUB. What i am not sure of is the order in which to do these things.

I am not sure if i can just put a fresh burn of the live CD into the machine and see if i can install to the existing free partition - or will it ask me to partition again? Also if i do this will it reinstall the GRUB or do i need to recover that additionally (using instructions from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)).

I also see that there might be some other options like running  sudo apt-get ubunut-desktop from the live CD to install Ubunut ([http://ubuntuforums.org/showthread.php?t=125339](http://ubuntuforums.org/showthread.php?t=125339)). In this case, again, will the GRUB install and how will i know that this install will install onto the correct partition - or will i get an opportunity to choose my partition.

Ok, sorry to post this issue which looks like it has been dealt with in bits and pieces on other threads but i am not sure about the order of things, nor the best option to take.

Any advice on what exactly to do would be great.

---

### Post by Azrael3000 on 2010-03-22
Well my guess is to just do what Ubuntu tells you. Throw the disk away and make a new one (maybe burn with slower speed as advised).

Then insert it into your drive and reboot. You should get a screen at the start where you can choose to install ubuntu, etc. There should also be an option that reads something like "Check CD", "Test CD" or something similar. Run this program to verify that your disk has been created correctly.
If it did you will end up again at the basic menu and then choose Install. You should be able to choose the existing partition you created last time for your installation.
If the CD is not ok, you should run a LiveCD. There will be a button on the desktop that sais "Install Ubuntu". Double Click and have fun.

HTH,
Arno

---

### Post by theozzlives on 2010-03-22
GRUB don't install until the end of the process. Just install to the partition you created and you should be fine. Oh, burn a new CD and it wouldn't hurt to run an md5sum on the ISO.

---

### Post by MorrisseyJ on 2010-03-22
Thanks for the help. I tried this:

checked the disk: all fine.

I then went to install. Got to the partitioning screen. This time with the dual install radio button checked, the system wanted to make another partition, in addition to the one that i had already created. It would not let me resize the old partition to less than 1.5GB and i was not sure if the old partition could be deleted from that screen.

I then tried the manual (advanced) option and clicked forward. That took me to a screen where i thought that i recognised the partitions i had made previously - with swap partitions created. I then highlighted the partition in which i thought i wanted to install ubuntu and clicked forward. I then got a message telling me that i needed to select a root partition (or something like that), and that i should go back and correct this problem. 

At this point i realised that i did not know what i was doing and have thus retreated here to the forum. 

If anyone can tell me how to solve this that would be great. Otherwise a tutorial on how to do the advanced install would be wonderful. On that note, it was mentioned that i should use the  desktop install option off the live CD. Does that sound like it would be the easiest at this point, and will i run into the same partition problems if i do this?

---

### Post by Azrael3000 on 2010-03-22
I'm not sure. But isn't the dual installation button here for dual Ubuntu installation? In this case you wouldn't need to tick it.

Another option for you would be to boot the livecd. Delete all partitions that are not Windows and then do a normal install. You can delete the partitions using the Gparted tool that you should be able to find under System -> Administration -> GParted.

---

### Post by MorrisseyJ on 2010-03-22
Isn't the install on the whole hard drive system (second radio button) liable to wipe my existing windows partition off the system as well as the existing partition created by the previous failed ubuntu install? Or do i get to choose this? 

Sorry, i am just loathe to wipe out my existing windows partition.

---

### Post by Azrael3000 on 2010-03-22
well did you try the GParted option? (In case you misread, I said, delete all partions that are NOT Windows).

---

### Post by MorrisseyJ on 2010-03-22
No, I had hoped that i would be able to install without having to defrag windows twice and run disk check again.

Regardless, i now find that i can't delete the partition with gparted because it is mounted. I get the message: 

"Please unmount any logical partitions having a number higher than 5"

I also find that the unmount option remains grey on that same partition and so i can't seem to do that. 

I am not sure if you have any more ideas.

This is frustrating because it must be possible to install ubuntu on a pre-partitioned hard drive. Hell, i feel like this is what i am told to do most often, yet all the tutorials only give explicit instructions for the simple install assuming that anyone doing the advanced option must be sufficiently advanced. 

Ideas welcome.

---

### Post by wilee-nilee on 2010-03-22
> **MorrisseyJ said:**
> No, I had hoped that i would be able to install without having to defrag windows twice and run disk check again.

Regardless, i now find that i can't delete the partition with gparted because it is mounted. I get the message: 

"Please unmount any logical partitions having a number higher than 5"

I also find that the unmount option remains grey on that same partition and so i can't seem to do that. 

I am not sure if you have any more ideas.

This is frustrating because it must be possible to install ubuntu on a pre-partitioned hard drive. Hell, i feel like this is what i am told to do most often, yet all the tutorials only give explicit instructions for the simple install assuming that anyone doing the advanced option must be sufficiently advanced. 

Ideas welcome.

In gparted from the live cd right click on swap then turn it off then delete the Ubuntu extensions=partitions including the swap, close gparted. Hit install and choose the open space to install into.

You might give us a post of sudo fdisk -l just so we can see the partitions.

A different OS can be a challenge.

Manual partitioning is really easy once you understand how it is done, and loading a OS into a pre-set partition for installs as well

---

### Post by MorrisseyJ on 2010-03-22
Brilliant, got gparted to work.

sudo fdisk -l (post gparted delete) gives:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        4417    33527655    c  W95 FAT32 (LBA)
/dev/sda3            4418        9729    42668640    5  Extended


One more basic question. When i 'hit install and choose the open space to install into', i do this through which option? dual install, total install or advanced option. If advanced will i have the root problem that i described above?

Thanks again.

---

### Post by wilee-nilee on 2010-03-22
> **MorrisseyJ said:**
> Brilliant, got gparted to work.

sudo fdisk -l (post gparted delete) gives:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        4417    33527655    c  W95 FAT32 (LBA)
/dev/sda3            4418        9729    42668640    5  Extended


One more basic question. When i 'hit install and choose the open space to install into', i do this through which option? dual install, total install or advanced option. If advanced will i have the root problem that i described above?

Thanks again.

So is sda3 the extended partition that was installed by the Ubuntu attempt? If so I would just remove it other wise you will have to do a manual partition which is quite easy and you attempted. If you need a swap so you can have sleep and hibernate you would have to build that to. 

The easiest thing though is just delete all things Ubuntu leaving the open un-partitioned space then hit install choose install in open space. This method will build the extension with a logical and swap partition inside I would go this route. This will give you a template to look at once installed to look at with gparted to understand manual partitioning.

---

### Post by MorrisseyJ on 2010-03-22
Brilliant, solved. Thank you.

I'll have a look at the partition set up now so i can get a feel for manual partitioning.

Thanks again to all for all the help.

---

### Post by wilee-nilee on 2010-03-22
> **MorrisseyJ said:**
> Brilliant, solved. Thank you.

I'll have a look at the partition set up now so i can get a feel for manual partitioning.

Thanks again to all for all the help.

Cool, then you can have fun like me I practiced loading my W7 MBR to my dual booted W7/Lucid setup then reloading grub, just to make sure i could do it.

---

### Post by Azrael3000 on 2010-03-22
Nice to hear that it worked. Have a lot of fun with Ubuntu.

---

