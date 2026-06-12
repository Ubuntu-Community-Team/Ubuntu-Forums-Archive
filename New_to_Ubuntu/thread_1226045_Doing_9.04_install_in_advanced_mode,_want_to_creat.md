---
title: "Doing 9.04 install in advanced mode, want to create extended partition"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by swarup on 2009-07-29
I am setting up a multiple boot laptop, and currently have my Jaunty 9.04 install disc booted up as a livecd install, and am at the partition screen. I would like to create an extended partition, and have the Ubuntu and Swap partitions inside it. But at the advanced partition screen, when creating a new partition, under partition type there is no option for "extended". One has to choose ext3, swap, etc. How can I create an extended partition here? This is critical for me, in order to have enough allowed partitions left over for the other OSs. How do I create an extended partition?

---

### Post by ranch hand on 2009-07-29
On your live CD go to System->Administration->Partition Editor.  Click on that and you will have gparted up.

This is the place to do basic partitioning of you drive.  I have most of my HDDs formatted to juat one extended partition.  On one of my internals (320Gb) there are 14 logical partitions plus 1 swap and there is still 92Gb free space.

I install on 2 partitions (/ and /home) so that drive has 7 OS' on it with room for 2 or three more.

---

### Post by swarup on 2009-07-29
Hey, great idea. Thanks!
Now, one more question on this: they say that the swap partition should be twice the size of one's RAM. And that on the other extreme, if the swap is less than the size of the RAM, then the system will not be able to go into hibernate mode. I've got 4 GB RAM. Do I really need a swap partition of size 8 GB? Will 4, 5 or 6 GB do?

---

### Post by AndyCee on 2009-07-29
Unless you decide to hibernate while utilising 4 Gig of RAM, 4 should do fine.

---

### Post by swarup on 2009-07-29
I see-- but I would indeed like to have full functionality, including hibernate (by the way, is suspend different-- does suspend need less swap?). And I'm not that strapped for space. Would 6 GB give me full performance including hibernation, or would you say I'd need the full 8 GB.

Also, are there other performance factors at risk here, such as general computer functionality, speed etc?

---

### Post by ranch hand on 2009-07-29
I never use anything except either on or off so I may be wrong but I would think that 6Gb would do fine.  The twice the size stuff is left over from the time when 512Mb was big stuff.  I think that if you have more swap than ram the kernal will be happy and everything will work.

I format my drive and install the swap at the end of the drive.  When you make your partitions for OS', they go on the beginning of the drive (or should).  That being the case, if your swap is not big enough you can always make it bigger (gparted in fun).

Never try to fool with the drive that you are running gparted from, do it from a differnet drive or a LiveCD.  Backing up is a good idea although I have never lost anything I wanted to keep.  Stuff happens.  You could (I know it is a remote possibility) even make a mistake and format the wrong thing.  Back ups on a different drive make me feel better.

Have fun.

---

