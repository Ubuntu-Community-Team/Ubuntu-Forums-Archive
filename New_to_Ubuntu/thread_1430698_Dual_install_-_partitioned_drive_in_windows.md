---
title: "Dual install - partitioned drive in windows"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-03-15
Hi, I am currently using Ubuntu through wubi, but would like to do the dual install. Nothing i have read seems to address the issue i think i have. 

I have two hard drives partitioned in my existing windows setup - C and D with Wubi sitting in D.

My question is when i dual install - probably using the ubuntu default (unless someone tells me that something else is much easier/better (NTFS etc)) - will it make a difference that i have two hard drives currently (will they remain as two (smaller) drives after partitioning for Ubuntu or become one (if so, what will happen to the contents of the one) and is there anything i need to do differently (make sure one is empty etc) because of the set up i have. 

I feel like this is an obvious issue but none of the posts and tutorials that i have read appear to address it - at least no explicitly. Possibly its the convoluted nature of my question that's causing the problem with searches etc.

If this already been dealt with on a post that i couldn't find, sending me a link to the post would be great. Otherwise all info would be greatly appreciated

Thanks.

---

### Post by cerealtx on 2010-03-15
two hard drives does not make a difference, the grub saves the location of where the os is, usually automatically, the only probably i have ever had is Vista overwritting grub, but thats easily fixable

---

### Post by Helkaluin on 2010-03-15
Fact is the automated partitioning is different for different partition setups.

It is always clearer to define what exactly you want and do it manually: Do you want to convert the entire D partition into a Linux area? If so format the entire D into an Extended and divide accordingly into Swap and What-not. Are there files in D that you cannot miss? Then resize D to free up space and make an Extended partition with that space, and then divide into Logical partitions accordingly.

It's much safer to specify the partitioning manually anyway: there's always a fear that hibernation won't work if the swap is somehow too small.

---

### Post by ajgreeny on 2010-03-15
You say you have two drives, but what I think you mean is that you have two partitions on one drive;  this is quite often the way OEMs set up windows on machines.

Can you tell us what is on each partition/drive by running the live CD and using the command ```
sudo fdisk -l
```in terminal.  It is possible this may be run from your wubi install, but I have no real idea about using wubi and don't know if the outcome of that command will be the same from there, so for my peace of mind, the live CD will be best.

Post the output of the fdisk command back here, and I will try to give you my recomendations for how best to proceed.  It could be that the "D" drive as you and windows call it is free and unused and could therefore be used for ubuntu, leaving "C" for windows, but let's see what we get from fdisk first.

---

### Post by MorrisseyJ on 2010-03-15
**Helkaluin**: I am new to all this and still working out what is the best way to partition. Forums and tutorials talk about having home drives and swap drives and i am not sure what is best - hence i was going to go with the ubuntu standard. 

At this point i would like to have a proper dual install of Ubuntu so i don't run into some small issues on Wubi and get to start making the switch to Ubuntu. With this in mind I would also like to be able to access windows in case things go wrong. I would also like to partition the drive in such a way that i do not run into trouble with future updates and settings etc. 

If you know of a good tutorial for achieving all this it would be very much appreciated.

**ajgreeny**: Yes, sorry i mean that i have 2 partitions on my one drive; which windows labels C and D.

The D drive currently has some stuff in it (just photos etc) and the Wubi install. Here is the printout from the terminal after i put i your command:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        5941    45769185    c  W95 FAT32 (LBA)
/dev/sda3            5942        9729    30427110    f  W95 Ext'd (LBA)
/dev/sda5            5942        9729    30427078+   b  W95 FAT32


I am failry sure that my C drive is not large enough to fit all that i have there plus the stuff from my D drive. That said, the free space on both drives is fairly substantial so i could move some stuff off the D drive and free up space for Ubuntu. I could also back up the stuff from C (my docs) and D resize, partition, and reinstall the data in ubuntu. In this regard it would also be useful if you could suggest a good generic way to repartition for a newbie.

Thanks to you all for your input.

---

### Post by ajgreeny on 2010-03-16
As I said I know very little about wubi, which may explain why I am now having to say that I don't know how to help you much more.

You actually have 4 partitions:=-
```
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        5941    45769185    c  W95 FAT32 (LBA)
/dev/sda3            5942        9729    30427110    f  W95 Ext'd (LBA)
/dev/sda5            5942        9729    30427078+   b  W95 FAT32
```
but one of them (sda3) is extended and just a container for another (sda5). It could be that wubi puts the swap of ubuntu onto a fat32 partition, but I just don't know about that, so am a bit baffled.  Neither can I tell from this which is your C drive and which the D drive, in windows terminology.

If you ran the fdisk command from the live CD, perhaps now it would clarify matters a bit more if you did the same from your installed wubi version.  Sorry to be so uncertain about this, but wubi was never very helpful as far as getting whole system information, in my extremely limited experience.

---

### Post by MorrisseyJ on 2010-03-16
Oh, sorry i think that i miss understood you.

That output from the terminal that i posted for the fdisk command was run in Wubi. I thought that your fdisk command just needed the live CD to be in the machine when i ran the command. I know nothing about command lines and thought that the fdisk might be referring to something on the live CD.

Unfortunately i am now at work and so cant run the fdisk command from the live CD. I'll do that when i get in this evening. I'll post the output here.

I think that the two extra partitions that you saw must have been created by the Wubi install.

Since i will uninstall wubi from windows before i defrag, disk cleanup and repartition with ubunutu, is it not possible to just know what will likely happen with my two partitions existing in windows at the moment? Clearly i am missing something of the logic here.

Sorry for having made a number of terminological errors here. The input is all very much appreciated.

---

### Post by MorrisseyJ on 2010-03-16
I appear unable to run the live CD. 

When i reboot with the CD inserted the machine just goes ahead and asks me if i want to run windows or ubuntu - i am not sure if this is supposed to happen, is my CD corrupt? Possibly i would have to uninstall wubi from windows and then reboot with the live CD. I could then run the "sudo fdisk -l" command and see what my hard drive looks like. 

If this is the only way to do this and make sure that i can dual install ubuntu correctly then i'll do it but if there was another way to tell you what my hard drive looks like then that would be greatly appreciated.

---

### Post by oldfred on 2010-03-16
It seems like you are still getting the hard drive boot menu not the CD. Do you have the CD drive set to boot first in BIOS or can select with F12 or other key a one time boot of another device?

Some info on partitions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If you decide to do a shared partition with windows I would use NTFS. Older versions recommend FAT and I used FAT up until Karmic when I converted to NTFS. I had just root, swap and a shared partiiton for windows/ubuntu data that I wanted to access from both like my firefox profiles.

If you have made any configuration settings that you want to save or have data in wubi you can back up your /home in wubi and add the data back into your new install. Defrag windows twice before resizing. You can use gparted to resize XP (Vista & 7 should use windows tools).

The liveCd and wubi should give the same results. Wubi is a full install, but is like the CD but running on the hard drive in a windows file that allows updates. It is better than the CD for testing but once you decide to use it a lot you need to convert to a full install.

---

### Post by MorrisseyJ on 2010-03-16
**ajgreeny**: Here is the output of the fdisk -l command run from the live CD (sorry it took me so long to sort this out):

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        5941    45769185    c  W95 FAT32 (LBA)
/dev/sda3            5942        9729    30427110    f  W95 Ext'd (LBA)
/dev/sda5            5942        9729    30427078+   b  W95 FAT32

I think its exactly the same as that which i got while running under wubi - so correct Oldfred.

**Oldfred: **Thanks for the partitioning advice. I think i have read the psychocats tutorial but wasn't sure if those partitions were best for everyone. Also the tutorial is great in telling me how i need to partition my hard drive, it does less well at telling me how to do it - sorry i am ***** footing around this partition thing as i don't want to mess up something that is too fundamental. 

I take it that i can use gparted to get back to one partition in XP. I imagine that i'll have to empty the partition that i get rid of before i resize.

I am looking to switch to a full install as although Wubi is meant to operate in the same way as a full install i am finding some weird happenings: [http://ubuntuforums.org/showthread.php?t=1429717&highlight=sound+toggle](http://ubuntuforums.org/showthread.php?t=1429717&highlight=sound+toggle). I have also seen that a bunch of forum postings describe either problems with wubi or suggest doing a full install to get rid of problems that are persisting.  In any case i am somewhat taken with this whole thing and so am quite looking forward to a full install. 

Thanks for the help

---

### Post by oldfred on 2010-03-16
Some more info on partitioning:

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

