---
title: "[SOLVED] Crap, I have screwed up my install."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Desert Sailor on 2008-12-14
Been running 8.10 for a while now, loving it, but still a noob.  Today I deleted a little ex3 partition on the hard drive, (Not my main install) and when I tried to boot back up to Ubuntu,there was no grub and an error 15.  (PANIC) So I used Win-2000 to C:\fixmbr.  Now I can boot my windows partition and I can see the Linux partition and swap partition, but I can't get to them.  How can I get back to them??? 

I have ONE 140 gig hard drive, Win-2000 is 25 gig and Ubuntu and swap is the rest.  Well, techincally it looks like this
Partition 1  20 gig NTFS Windows-2000  (now working as well as windows can). 
Partition 2  2.8 gig Ex3 (former Ubuntu screw up) This is what I deleted today and now shows as unformatted space.
Partition 3  115 gig Ubuntu file system.  (this is the partition I want to be able to load.
Partition 4  3 gig Linux swap.  This partition is visible in Fdisk. 

I need help getting back to my beloved Ubuntu without having to totally reinstall.  

Failing getting back, is there any way to save the /home directory with e-mail, documents, and music?  (Please don't tell me I have to start over). 

Thanks...

---

### Post by taurus on 2008-12-14
That little ext3 partition didn't happen to be /boot?  Maybe this link helps, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

### Post by sneeks on 2008-12-14
> **taurus said:**
> That little ext3 partition didn't happen to be /boot?  Maybe this link helps, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

seems like it was

---

### Post by logos34 on 2008-12-14
boot the ubuntu live cd and post the output of 

sudo fdisk -l

Sounds like partitions got renumbered after you deleted the 2.8 gb [edit: or else it was /boot like taurus says]...While you're on the live cd try restoring grub (see link in my signature).  But you likely have to edit menu.lst as well.  So mount your 'main install' (root?) and post the contents of /boot/grub/menu.lst (the path will ne something lie '/media/disk/boot/grub/menu,lst'

---

### Post by logos34 on 2008-12-14
> **taurus said:**
> That little ext3 partition didn't happen to be /boot?  Maybe this link helps, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

that makes sense...should have thought of that

---

### Post by Desert Sailor on 2008-12-14
Oh thanks so much.  I have been posting here off the live CD.  But I was able to follow the instructions, and I think I may have GRUB back on the boot sector.  I am going to reboot right now.  I'll be back in a few minutes if I have grub back, then I can go edit it and clean things up. 

Thank you, thank you, thank you!!!

---

### Post by Desert Sailor on 2008-12-14
Thanks again...  I am back to my beloved Ubuntu with all my settings, files and music. The documentation was perfect and worked, unlike some of the other suggestions I found when I searched.  

I will mark this thread closed and solved.  Thanks again for all your help.

---

### Post by logos34 on 2008-12-14
edit

---

