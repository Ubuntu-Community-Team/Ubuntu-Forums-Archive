---
title: "file system check problems"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by BLoB626 on 2009-02-12
Hell  o

I run Ubuntu 8.10 
While I was booting up I recieved the following message

/dev/sda1: Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
Checking drive /dev/sda1: 5% (stage 1/5, 43/592)
fsck died with exit status 4
*An automatic file system check (fsck) of the root file system failed. 
A manually fsck must be performed,then the system restarted. 
The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
*The root file sytem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password to maintenance
(or type control-D to continue):

now when I type in the root password it just tells me "Login incorrect". But it is the correct root login as I set it and used it the last time I managed to use my computer properly.

The only thing I can do is to press control-D. This however gets me nowhere as it just restarts the system which then runs the file system check again.

Thank you for your time

---

### Post by amac777 on 2009-02-12
If you can't get the root password correct, you could try booting from a live CD and then running fsck manually on the hard disk that way.

---

### Post by BLoB626 on 2009-02-12
Ok I just tried that and it doesnt want to boot from disk the live cd is in and I select boot from CD/DVD and it says that the boot record is not found and boots from the normal drive

---

### Post by geirha on 2009-02-12
How did you install Ubuntu? Did you boot an Ubuntu liveCD or maybe liveUSB? Or did you install it inside Windows (wubi)?

---

### Post by BLoB626 on 2009-02-12
I installed it a while back, I think it was Edgy, from a live cd and i've used the internal upgrades ever since

---

### Post by geirha on 2009-02-12
Is it the same CD as you installed from that you are trying to boot from?

Once you do manage to boot a live CD btw, you can either run in a terminal ```
sudo fsck /dev/sda1
``` or start System -> Administration -> Partition Editor, right-click the partition and choose check.

---

### Post by BLoB626 on 2009-02-12
No its not the same cd its an Intrepid Ibex cd

---

### Post by geirha on 2009-02-12
Perhaps the CD has defects and need to be burned again. Do you have any way of testing it on another computer? Does the edgy CD still boot (if you still have it)

---

### Post by BLoB626 on 2009-02-12
Ok the cd had a defect now buning a new one

---

