---
title: "Mounting and unmounting drives"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Oz-1313 on 2008-12-24
Hi There, I had this problem today which seems to have now fixed itself however I just want to check a couple of things since im new to ubuntu (Im using a dual boot).

I was transferring a file from an external hard disc onto the desktop when the system crashed.  I had to pull out the hard disk and then I forced the computer to shut down (holding the power button).  A couple of attempts to boot up ubuntu didnt work as it got to the loading screen and then would stop before text appeared saying that it would not load properly (words to that effect) and it advised me to boot up windows and run a check on the partition.

I booted windows a couple of times but wasnt sure how to check the partition and tried ubuntu a couple of times with no progress.  Then on one more try ubuntu loaded itself!  Which is great but i still dont know what happened.  The external hard disk seems fine to me as ive moved files from it onto my laptop since no problem.

Anyone have any ideas what happened?  i realise its not the most detailed of problems but i cant see what the error messages said exactly as i dont get them now!

Also i take it for all USB sticks and external hard drives you must unmount before you pull them out them?

Thanks

---

### Post by halitech on 2008-12-24
was the external hard disk formated ext3 of ntfs or fat32?

yes, all drives (external, thumb, cd/dvd) must be unmounted before removing them

---

### Post by Oz-1313 on 2008-12-24
I dont know in what format the external was im afraid.  What are the differences between the different types?

---

### Post by halitech on 2008-12-24
NTFS is what windows 2000 and up uses, FAT32 was win ME and below, ext2/3/4 is what linux uses. natively windows 2000 and up can read ntfs and fat32 but not ext2/3/4 where linux can read ext2/3/4 and fat32 but has some issues with ntfs.

---

### Post by Oz-1313 on 2008-12-24
It came bundled with a vista PC so i imagine that its the first one.  Hope it hasn't damaged it!  It is working ok and transfering files to other PCs etc no problem

---

### Post by ajgreeny on 2008-12-24
I suspect the drive was probably formatted as ntfs which if not removed properly from the computer mayl refuse to mount in Ubuntu unless you use the -force option.  In any case you must always unmount drives before pulling them out of a usb port, or you may find data has not even copied to or from them properly and could cause you big problems.

---

### Post by Oz-1313 on 2008-12-24
Hi Ajgreeny,

Yeah I always made sure that when using windows i did "safely remove hardware" before unplugging and i would have done the same in ubuntu had the system not froze up on me.  I had to do a bit off digging to make sure that "unmount" definitely meant unplug as i had a horrible feeling that it would wipe the dick to blank!!

Still its working fine now so i take it that if the external works now then no harm done?
  I see loads of people just pulling out drives, ipods and sticks etc and have always thought, there must be an option for unmounting there for a reason!!

---

