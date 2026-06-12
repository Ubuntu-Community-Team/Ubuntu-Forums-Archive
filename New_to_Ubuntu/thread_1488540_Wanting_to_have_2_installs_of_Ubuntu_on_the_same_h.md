---
title: "Wanting to have 2 installs of Ubuntu on the same hard drive."
date: 2010-05-20
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-20
I have a friend who has his hard drive divided into three partitions:  one for /, on for /home and one for the swap.

He is wanting to shrink his home partition to make some unallocated space, then install a second copy of Ubuntu on the same hard drive and have it use the new free space for its /, and share the /home partition with the first install.  The idea behind this is to have a backup OS available in the event something goes wrong with the first install.

I have a feeling that doing this isn't really all that hard, but the questions that come to my mind are:

What's the best way to get GRUB2 setup for this?  What will happen to its boot menu after upgrades to either OS?  Is it easy to keep the primary system primary after a kernel update to the second system?  What's the best way to distinguish between the two?

---

### Post by Drenriza on 2010-05-20
From a security point of view this is a bad idea.

To have the normal system + the backup on the same disk?
What if the whole disk brakes down? bye bye backup.

If i was him i would backup system files that are responsiable for restoring the system if it should break down.

and then upload it to a server or an external drive.

I would use this guide.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Paqman on 2010-05-20
It's not hard to set up at all. One thing to be aware of is that you can only have four primary partitions, so with two /'s, a /home and a swap, that's the drive maxed out unless some or all of them are inside extended partitions.

> **diablo75 said:**
> 
What's the best way to get GRUB2 setup for this?


When you install the second system it will spot both installs. All you need to do is boot into the original system and run:
```
sudo update-grub
```

It will spot the second install and add it to Grub.

> What will happen it's boot menu after upgrades to either OS? 

Part of the install process for new kernels is to update the Grub menu, as above. So that will sort out the systme you're running. To keep the other one in sync, boot into it and run the update command.

> Is it easy to keep the primary system primary after a kernel update to the second system? 

Kernel updates won't change the default boot in Grub, they just add an entry so you can boot that kernel.

---

### Post by diablo75 on 2010-05-21
> **Paqman said:**
> 
Kernel updates won't change the default boot in Grub, they just add an entry so you can boot that kernel.

Actually, I just tested this out in Virtual box.  I installed Ubuntu across two partitions (root and /home) plus the swap, leaving a gap of space to install a second root partition for the second instance.

After installing the second instance, grub moved the original down near the bottom of it's menu and added the phrase "(on /dev/sd1)" after the name.  To differentiate the two, I also installed the OS's with slightly different user names so I could tell them apart.

So I booted into the first install and applied all updates, which included a kernel update.  After restarting, it modified the GRUB menu, making the original install the first item on the list.  It also removed the "(on /dev/sd1)" notation from the name/label, but then applied a "(on /dev/sd7)" to the second install, which was moved down to the bottom of the menu.

So it would appear that for any kernel update applied to either side results in grub automatically shifting whatever you happen to be running to the top of the menu, reclassifying it as primary (top/default).

I know it's not hard to just keep this sort of behavior in mind when booting after updating the secondary install and running sudo update-grub within the primary to rearrange the menu so the primary is put back at the top... but I was kind of hoping for something a little more elegant.  Like, instead of calling one "(on /dev/sda1)" it could just be called "(Primary)" and the secondary called "(Backup/Secondary)".  Is there any way to do this?

---

