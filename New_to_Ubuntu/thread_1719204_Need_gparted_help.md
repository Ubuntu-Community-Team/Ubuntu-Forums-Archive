---
title: "Need gparted help"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by s1baker on 2011-04-01
hi,
I have just cloned a 30 gig HD over to a 160 gig HD.
Now I have have 111 gigs of unallocated space on the 160 gig HD. Should I ( can I ? ) increase the size of sda1 to the full size of the HD, or do I need to make another partition to be able to use this unallocated space?

 Also, I have a live cd that I booted up to see if gparted was on it, and it was. I believe I need to use gparted from a cd in order to move/resize any partitions that are mounted.
 

I have some more questions.

1) As the screenshot shows, I have partitions sda1, sda2 and sda5. Is there supposed to be a sda3 and sda4 partition?

2) I booted up in a live cd and experimented with increasing the size of sda1, but it would not let me increase any larger than it already is. Can I, or should I, increase sda1 or sda2 to use all of the unallocated space?

3) The swap space shows to be about 1-1/2 gigs. Now that I have a much larger HD, should ( or can I ) increase this size? ( I have about 1/2 gigs of ram. )

4) If I make one huge partition out of the unallocated space, cab Ubuntu address all of the space?

thanks


here is a pic of the partitions using gparted.

---

### Post by Fire_Chief on 2011-04-01
So based on your attached image, sda2 and sda5 are only being used for swap related storage. Since this is non-persistent storage, we can safely delete and move it around on the drive. NOTE: you will have to change the settings in Ubuntu to use the new swap location but we'll get to that.

I would delete sda5 and sda2. Create a new partition (sda2) as a primary partition. Make it 2 GB in size and have it be at the end of the free space (end of the drive).
Then select the sda1 partition and expand it to use all of the available space. Once you click apply, GParted will make the desired changes.

After this is done, boot back into Ubuntu and edit your fstab file to correct the location of the swap space. Documentation on fstab in Ubuntu can be found here [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

First identify the new UUID of the swap partition.
```
sudo blkid
```
Then take the UUID identifier (copy it) and replace the one in the fstab file pointing to your swap space. Look for the line that has the word swap for the filesystem type.
```
sudo gedit /etc/fstab
```
Save the file and reboot. Viola!

Cheers!

---

### Post by s1baker on 2011-04-01
About the new 2 gig sda2 partition ... do I move it to the end of the 111 gigs of unallocated space on the HD, or the end of the 35 gig space of sda1?

Is the new sda2 partition that I make where the new swap partition will be placed?

---

### Post by Fire_Chief on 2011-04-01
It would be at the end of the unallocated 111GB space (at the very end of the sda drive) and yes, it is for the swap space.

---

### Post by s1baker on 2011-04-01
thanks, I'll try this and mark solved or add to the post later.

---

### Post by s1baker on 2011-04-01
I can't get the swap partition to show.
 
 I deleted partitions sda2 and sda5 and created a new partition sda2 and put it at the very end of the HD space. Then I increased the size of sda1 to grab the rest of the HD space. But when I rebooted there was no swap partition shown. See the attached snapshot of the partition table after doing this.

Here is what I get when I type sudo blkid:
```
/dev/sda1: UUID="e8d93133-8081-46d0-a959-4149457d3275" TYPE="ext4" 
/dev/sda2: UUID="907130a6-da4c-4567-9dd4-7a9de4a88b55" TYPE="ext4"
```

this is from  sudo gedit  /etc/fstab
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=907130a6-da4c-4567-9dd4-7a9de4a88b55 none            swap    sw              0       0
```



this is what I get when I tried sudo swapon -a
```
swapon: /dev/sda2: read swap header failed: Invalid argument
```

Could it be because there is a 1 megabyte space between partition sda1 and sda2 ?
(also, I have rebooted my machine several times, should I shut down and then restart? )

---

### Post by plucky on 2011-04-01
You didn't create a Linux swap partition,you just created another ext4 partition.
When you create the partition you have to select Linux swap from the drop down list not ext4.

> Could it be because there is a 1 megabyte space between partition sda1 and sda2 ?

No. For some reason,gparted leaves small spaces between ext4 partitions.


Delete the sda2 partition and try again,but select Linux swap instead of ext4.
You should be able to do it when the system is booted from the HDD as long as the sda2 partition is not mounted and you have gparted installed.

Good Luck

---

### Post by s1baker on 2011-04-01
Thanks Fire_Chief & plucky.

Does this look right?
see attached

Also, the new HD is 160 Gigs, but gparted shows only about 150 gigs.
I wonder what happened to the other 10 gigs?

---

### Post by Fire_Chief on 2011-04-04
Yep, that looks great.

The size discrepancy is due the differences in how a manufacturer describes disk size vs how an OS views it. It's a rough average of a 7% loss in what you think you're getting. There are various discussions and articles about this but the short story is you're using all of the space, it's just reported differently.

Cheers!

---

### Post by spielball on 2011-04-04
Thanks a lot for this thread. I was just about to post another thread, but then I found this. Helped me to answer the question whether I should choose 'linux-swap' or 'ext4' as the format for the swap partition.

---

