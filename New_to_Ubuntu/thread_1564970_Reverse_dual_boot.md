---
title: "Reverse dual boot"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Phil Binner on 2010-08-31
Hi

I recently installed MythBuntu as a dual boot on my Ubuntu machine. I did this because Mythbuntu is my final objective, and I thought I had to. Now reading the instructions I find I would have been better to install MythTV inside Ubuntu. Is there any way I can un-install Mythbuntu and at the same time restore the partition to Ubuntu, the way it was.

The alternative, to re-install Ubuntu and restore the setup, will not be too traumatic, but there are a few things I've forgotten how I did, so I'd rather not.

I guess there is a third alternative, to un-install Mythbuntu and leave the partition as a library resource for MythTV if I ever succeed in getting it going, but my skill levels are not high and I'm not sure how to do that.

---

### Post by an0dos on 2010-08-31
> **Phil Binner said:**
> Hi

I recently installed MythBuntu as a dual boot on my Ubuntu machine. I did this because Mythbuntu is my final objective, and I thought I had to. Now reading the instructions I find I would have been better to install MythTV inside Ubuntu. Is there any way I can un-install Mythbuntu and at the same time restore the partition to Ubuntu, the way it was.

The alternative, to re-install Ubuntu and restore the setup, will not be too traumatic, but there are a few things I've forgotten how I did, so I'd rather not.

I guess there is a third alternative, to un-install Mythbuntu and leave the partition as a library resource for MythTV if I ever succeed in getting it going, but my skill levels are not high and I'm not sure how to do that.

Boot from a live cd and use gparted to remove the mythbuntu partition and expand the ubuntu partition. If you encounter problems with grub after doing this, check out [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

For more information on partitioning read this: [https://help.ubuntu.com/community/HowtoPartition ]("https://help.ubuntu.com/community/HowtoPartition")

---

