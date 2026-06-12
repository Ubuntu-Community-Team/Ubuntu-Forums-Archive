---
title: "Can't mount unallocated partition..."
date: 2010-06-30
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-30
I have a partition that I never formatted during the initial install of Ubuntu. Now I'm running into a problem formatting it. I tried booting to a LiveCD first and formatting it that way. When tried to format just that partition (/dev/sda12 in my case), it wouldn't let me. It kept telling me something like "/" had not been defined (or something to that effect).

When I try to format it using gparted, my only options (when I right-click that partition) are New and Information. If I choose New, it tells me "It is not possible to create more than 4 primary partitions."

So, how can I format this unallocated space? It's over 21 GiB. 

Thanks,

Andy

---

### Post by jayceekay on 2010-06-30
Try to make an extended (logical) Partition and not a primary. As the message says, the number of primary partitions on one disk is limited to 4.

---

### Post by Leppie on 2010-06-30
boot off a livecd, then using gparted you can expand the extended partition (sda3). as you already have 4 primary partitions assigned and the free unallocated space is outside the extended partition, you wouldn't be able to create a new partition unless you expand the extended partition.
once the unallocated space belongs to the extended partition, you will be able to create a new partition (extended partitions almost have no limit).

---

### Post by JKyleOKC on 2010-06-30
You need to extend the size of the extended partition (sda3) to include this unallocated space. You'll then be able to format it.

All PCs using the standard Master Boot Record layout are limited to only four primary partitions. The "extended" type was created to overcome this limitation; it's simply a container that holds the additional partitions. To go into possibly too much detail, the extended partition directs the system to another area of the disk where the additional partition information is stored.

I note that you have quite a few smaller unallocated areas in sda3, as well. You might be able to move the existing allocated partitions there so as to merge these areas into one, and gain even more space. However moving partitions is always risky, so be sure you've backed up any data that's important, just in case something goes wrong and loses everything on the disk!

---

### Post by akelsall on 2010-06-30
Thanks to all who replied. I'll have to go back and look at that again I guess. I must have missed where it allowed me to specify an extended partition. I'll repost once I've tried it out.

Thanks,

Andy

---

### Post by ankspo71 on 2010-06-30
Hi,
Actually, you already have the extended partition created, you only need to maximize the size of the one you already have. The [COLOR="DeepSkyBlue"]light blue box[/COLOR] in the diagram in gparted is the extended partition. Once you get that resized, you can then add another logical partition inside the extended partition.

I attached a pic so you graphically see what needs to be done. The light blue box (extended partition) needs to be expanded to the right. Then you can create another logical partition inside it.

---

### Post by Leppie on 2010-06-30
> **akelsall said:**
> Thanks to all who replied. I'll have to go back and look at that again I guess. I must have missed where it allowed me to specify an extended partition. I'll repost once I've tried it out.
just boot off an ubuntu livecd and launch gparted, then expand sda3 to cover the unallocated space.

PS: don't forget to hit the "Apply" button :lolflag:

---

### Post by akelsall on 2010-06-30
> **ankspo71 said:**
> Hi,
Actually, you already have the extended partition created, you only need to maximize the size of the one you already have. The [COLOR="DeepSkyBlue"]light blue box[/COLOR] in the diagram in gparted is the extended partition. Once you get that resized, you can then add another logical partition inside the extended partition.

I attached a pic so you graphically see what needs to be done. The light blue box (extended partition) needs to be expanded to the right. Then you can create another logical partition inside it.

ankspo71, can I do this without booting to the live CD?

thanks,

Andy

---

### Post by Leppie on 2010-06-30
> **akelsall said:**
> ankspo71, can I do this without booting to the live CD?
you cannot resize the extended partition as long as there's a partition which is in the extended partition is mounted. so basically, yes you can do that from your normal install as well.

---

### Post by ankspo71 on 2010-06-30
> **akelsall said:**
> ankspo71, can I do this without booting to the live CD?

thanks,

Andy

You won't be able to resize the extended partition with the Ubuntu installer (ubiquity) I'm afraid, if that is what you meant, because it doesn't have a way to configure the extended partitions. Ubiquity automatically creates those for us when we create the logical partitions instead. For example, if I wanted to create 3 20gb logical partitions while I'm installing Ubuntu, it would automatically create a slightly larger than 60gb extended partition for me to house those logical partitions in.

Your best bet is to go boot the live CD and use Gparted. In gparted, right click on your extended partition (dev/sda3), then select "Resize/Move", then when the next window opens, drag the right edge of the blue box on top to the right side, so it will use up the remaining space. (you can also adjust the size my using the boxes below that with the sizes in it). Then click on "Resize/Move" below at the bottom of this window, then that window will close, then click on "Apply" in the main window of Gparted. 

Now you are free to add a new logical partition or resize/rearrange your existing ones. Be sure to backup your important data before doing these changes though, just in case.

I'm not sure if this has been mentioned already or not, but I'' try to explain it anyways. You probably noticed that you have 3 primary partitions "/" "/Home" and "swap", but gparted complained that you can't have more than 4 primary partitions. This is because the extended partition counts as a primary partition too as to why the error message occured. 
Hope this explains a bit more.

---

### Post by Leppie on 2010-06-30
you [COLOR=Red]*don't have*[/COLOR] to boot off a live cd. but you will have to unmount all the partitions hosted by the extended partition. as these partitions aren't system partitions (like the root partition '/'), you could just unmount all of them and then do the operation and once done remount them.

---

### Post by ankspo71 on 2010-07-01
Right - the live cd isn't necessary when the partitions in question can be unmounted. :p

---

### Post by Leppie on 2010-07-01
it generally is easier for people who don't have much experience with partitioning to use the live environment.

---

### Post by akelsall on 2010-07-03
OK, getting closer. I followed ankspo71's advice and was able to expand the extended partition. I now see /dev/sda12 and it's formatted as ext4. The problem now is it won't automount after booting. 

I tried running the LiveCD and try to setup a mount point that way, but I ran into the same problem as before. When I click on the existing partitions (when I get to the point in the LiveCD to partition the drive), I see they're all set to "do not use the partition", so I tried setting this one the same way. No dice. Kept saying "No root file system is defined." What am I doing wrong here? 

I ran into problems with ureadahead today (that was definitely related to manually adding entries into fstab), so I want to avoid that headache again. Any ideas?

Thanks,

Andy

---

### Post by Leppie on 2010-07-03
could you post your fstab with the entry for the new partition?

---

### Post by akelsall on 2010-07-03
> **Leppie said:**
> could you post your fstab with the entry for the new partition?

Leppie, I guess I didn't explain this too well. I expected Linux to detect the new partition (as it did when I first defined the original partitions when I initially installed Ubuntu). When I tried using the LiveCD to go back and create a mount point for this one new partition, I ran into the problems I described.

I can try to add it manually to fstab, but I'm afraid I'll run into the ureadahead problems during boot again (which is what happened when I tried to manually add partitions of a secondary drive into fstab).

Any other ideas, or will I have to add this manually?

Thanks,

Andy

---

### Post by Leppie on 2010-07-03
> **akelsall said:**
> Leppie, I guess I didn't explain this too well. I  expected Linux to detect the new partition (as it did when I first  defined the original partitions when I initially installed Ubuntu). When  I tried using the LiveCD to go back and create a mount point for this  one new partition, I ran into the problems I described.
 
 I can try to add it manually to fstab, but I'm afraid I'll run into the  ureadahead problems during boot again (which is what happened when I  tried to manually add partitions of a secondary drive into  fstab).
 when you create partitions after you have installed the system, you will  have to create mount points manually. it's actually not that very  difficult once you get to know it.
the fstab entry could be as simple as:
```
/dev/sda12 /JUNK ext4 defaults 0 2
```
though you will have to create the folder /JUNK as well:
```
sudo mkdir /JUNK
```

---

### Post by akelsall on 2010-07-03
Leppie, that's good to know. I assumed you could somehow go back and get the new partition to automount. Looking at my fstab file, it's using the UUID, so I used the command **sudo blkid /dev/sda12** to pull the blkid for that partition. I also copied the other parameters being used by the original partitions. Works great now. Thanks to you and others who helped out with this.  This is why I went with Ubuntu....the active support group and knowledgeable and helpful people. 

Below is a sample of my fstab. The first listing is my /home (that I had put on a separate partition) and the last line is my new partition. 

# /home was on /dev/sda2 during installation
UUID=4a71ba55-c0cd-4083-909f-8ce1622f9134 /home           ext4    defaults        0       2
# 
UUID=e61239d5-bbde-4479-8388-e5d4dede1fe8 /JUNK           ext4    defaults        0       2

---

### Post by Leppie on 2010-07-03
glad it's all working out.
ah, one last thing. don't forget to change the ownership, unless you want root to be the only user with write acces to your newly created partition.
you can change the owner like this:
```
sudo chown <username>:<usergroup> /JUNK
```
<username> and <usergroup> usually have the same name.
if your username for instance is akelsall, then the usergroup should be akelsall as well.
so the command would be:
```
sudo chown akelsall:akelsall /JUNK
```

---

### Post by akelsall on 2010-07-05
Leppie, I did remember to do that, but thanks for pointing it out for others. That's one step that could have someone scratching their head if they forget to do it.

Andy

---

### Post by Leppie on 2010-07-05
well, glad it all worked out well :)

---

