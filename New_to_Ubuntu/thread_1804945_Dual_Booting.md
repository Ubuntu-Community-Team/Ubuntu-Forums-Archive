---
title: "Dual Booting"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by orrymr on 2011-07-15
Hi all.

For the last few months I've been using Linux through a Wubi installation. I've decided to now partition my hd and dual boot "properly". I was wondering if you guys had any recommendations concerning which partition tool to use. Should I just use the Disk Management tool that Windows 7 comes with?

Also, does it matter which OS I install first?

---

### Post by Mark Phelps on 2011-07-15
> **orrymr said:**
> Should I just use the Disk Management tool that Windows 7 comes with?
Well, yes and no ... Yes, use ONLY the Win7 Disk Management tool to shrink your Win7 OS partition to make room for Ubuntu.

While you have that tool open, look to see how many partitions are on your drive.  If you already have four, that's the max and you can't create any more.  You will then have a LOT of work ahead of you to do a true dual-boot with separate Linux partitions.

If you STILL then want to go ahead with partitioning, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 Boot Loader.

And NO, do NOT use the Win7 Disk Management tool to create partitions for Ubuntu; let the Ubuntu installer create its own partitions in the unallocated space.

> Also, does it matter which OS I install first?

Yes, it does.  Install Win7 first; then, Ubuntu.  After that, open a terminal in Ubuntu and enter "sudo update-grub".  That will generate a new GRUB menu to include and entry for Win7.

---

### Post by orrymr on 2011-07-15
Thanks for the reply.

Well, I've got another hard drive in my computer that I use for storage (it's got no OS on it). The drive that has my current Windows installation isn't partitioned, so I should be fine.

Thanks again!

---

### Post by amjjawad on 2011-07-15
> **Mark Phelps said:**
> Yes, it does.  Install Win7 first; then, Ubuntu.  After that, open a terminal in Ubuntu and enter "sudo update-grub".  That will generate a new GRUB menu to include and entry for Win7.

During installation, "sudo update-grub" will be issued automatically so it's an extra unneeded step. Never had to do that when it comes to Dual-Booting unless there's something I missed here.

---

### Post by Blasphemist on 2011-07-15
I've seen the recommendation before to only use Win 7 disk management to shrink windows. I do not agree. I have a couple arguments. 

One, is you do the normal first installation procedure of Ubuntu where you let the install of ubuntu make the partitions, it does the shrinking and creates the partitions. This is not done with windows tools.

Two, if you defrag and try to shrink using windows only, you can do that indefinitely as it does a miserable job of moving files from the end of the partition. You will be referred to the windows application log to find the file at issue, will have to take action yourself of some kind to work around the issue with that file, and then you'll just have an issue with another file. You can then use GParted instead and have it shrink the disk right away without issue. You'll then boot into windows, it will run a chkdsk and all will be hunky dorry.

I understand being safe but there is a point where you just have to get it done and if it wasn't normally safe, the ubuntu install wouldn't do it itself.

It doesn't sound like you are doing a shrink orrymr but I for some reason just had to say this. :D

---

### Post by oldfred on 2011-07-16
@Blasphemist
I think you are correct, but I still suggest to use Windows MMC to shrink windows.

The issue was several versions ago when XP & Linux all used sector 63 as the start. Vista & then 7 used sector 2048 as the first sector of the install. Some versions of gparted would auto move the Vista/7 partition to start at 63. Windows PBR had to be repaired to then let windows work again.
Herman said the installer never moved the sector start of the windows partition, so auto installs always were ok.
The last few versions of Ubuntu & gparted now start all first partitions at sector 2048, so there is no current issue.

But, if someone partitions in advance with an old copy of gparted they still can have the problem. We sometimes see users find an old CD and use it.

---

### Post by Mark Phelps on 2011-07-16
> **amjjawad said:**
> During installation, "sudo update-grub" will be issued automatically so it's an extra unneeded step. Never had to do that when it comes to Dual-Booting unless there's something I missed here.

That's news to me.  I dual-boot and have not seen that happen on its own.  Also, we get a LOT of posts here from other folks who dual boot and only end up with access to Ubuntu.

Maybe there's a feature you select that does that for you now?

---

### Post by amjjawad on 2011-07-16
> **Mark Phelps said:**
> That's news to me.  I dual-boot and have not seen that happen on its own.  Also, we get a LOT of posts here from other folks who dual boot and only end up with access to Ubuntu.

Maybe there's a feature you select that does that for you now?

No special feature at all. If Windows is installed first then Ubuntu (or any Linux Distro with GRUB2), then I don't need to perform "sudo  update-grub" at all.

I have done that many times and not even one time that I had to run "update-grub".

The only case I had to is when I Mutli-Boot.

---

