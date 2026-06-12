---
title: "Deleted windows recovery partition"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by mcnatty on 2011-01-19
I recently installed ubuntu 10.10 on a new laptop along side windows 7. Everything seemed to be working well, but I decided that i wanted to change the partitions and reinstall ubuntu (from a usb stick). At this point, things started to get a little messed up.

At one point, I ended up getting the grub rescue screen. When re-installing ubuntu, I tried to install alongside another OS, but got an error message. Frustrated, i thought i would just wipe out the windows os and reinstall after getting ubuntu set up. I chose the "use the entire disk" option, forgetting that this would also wipe out the windows recovery partition on my hard disk.

My computer did not come with a recovery disk, but i did create a set before installing ubuntu using the recovery disk program supplied with my computer. (why do i have 4 if it seems like only 1 does something?) I've tried to restore the system image using a recovery disk by changing the boot order. i click through the 'are you sure you want to restore the system image' screens and reach a screen that shows me a progress bar. no progress is ever made, and after one and a half hours, i get an error message. (i've tried this three times.)

this is my first experience with ubuntu and i truly have no idea what's going on, so any help is greatly appreciated!

---

### Post by Quackers on 2011-01-19
Welcome to UF.
Did you verify the discs when they were made? Sadly, if those discs won't restore your system, and if the recovery partition is gone, you can't get your Windows back. It may be worth trying to contact the manufacturer and ask for a set of discs, however, they are likely to charge for them.

---

### Post by Mark Phelps on 2011-01-19
> **mcnatty said:**
> ...(why do i have 4 if it seems like only 1 does something?) 
Because, if they're CDs, it takes more than one to hold all the info needed to restore Win7.
> I've tried to restore the system image using a recovery disk by changing the boot order. i click through the 'are you sure you want to restore the system image' screens and reach a screen that shows me a progress bar. no progress is ever made, and after one and a half hours, i get an error message. (i've tried this three times.)

Would be helpful if you would tell us the details of the error message.

One possibility is that, since you (I'm guessing) repartitioned the drive to install Ubuntu, the restore program won't run if the current OS partition is not the same as the original size.  But, as I said, that's only a guess.

And, even if it DOES run, it's most likely to erase your drive, including the Ubuntu install.

So, you could try booting from an Ubuntu LiveCD, running Partition Editor, unmounting all the partitions, removing the Linux partitions, and resizing the Win7 partition to fill the drive.

But, that's a lot of work and, given how slow GParted is, could take quite a while.

You will probably (as Quackers has said already) have to end up contacting the manufacturer to see if they can help with restore.

---

### Post by mcnatty on 2011-01-19
Yep, $50 for the recovery disk from the manufacturer. Thanks for the help!

---

### Post by mcnatty on 2011-01-19
Yep, $50 for the recovery disk from the manufacturer. Thanks for the help!

---

