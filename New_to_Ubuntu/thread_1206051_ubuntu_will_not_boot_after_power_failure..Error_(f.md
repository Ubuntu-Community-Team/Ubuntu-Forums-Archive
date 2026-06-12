---
title: "ubuntu will not boot after power failure..Error (fsck died with exit status 4)"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by drdave69 on 2009-07-06
Please help !!!
I had a power failure & when I tried to reboot the system it says "unclean shutdown, checking drives /dev/sda1...", the disk check fails and this comes up on my screen:

*an automatic file system check (fsck) of the root file system failed.
a manual fsck must be performed, then the system restarted.
the fsck should be performed in maintinence mode with the root filesystem mounted in read-only mode.
*the root filesystem is currently mounted in read-only mode.
a maintenence shell will now be started.
after performing system maintenence, press control-d to terminate the maintinence shell and restart the system.
give root password for maintinence
(or type control-d to continue)


I type in my root pass, then fsck starts and tells me there is an error, skip or continue, I continue & the same error keeps coming up, then fsck fails.
I am TOTALLY LOST......Please Assist.
Thanks

---

### Post by drdave69 on 2009-07-06
anyone???

---

### Post by lukeiamyourfather on 2009-07-06
The hard disk may have been damaged in the power failure. I'd try booting with the installation disc and using the recovery option try to see if the hard disk still shows up with fdisk -l or another hard disk tool. Or if you have another system, pop the drive in there and try to mount it (another Linux system that is). Cheers!

---

### Post by DCGStudios on 2009-07-06
What was the power surge caused from? 
Were you connected to a surge protector?

---

### Post by drdave69 on 2009-07-06
> **DCGStudios said:**
> What was the power surge caused from? 
Were you connected to a surge protector?
not sure what caused the failure, breaker tripped
yes, connected to a surge protector

---

### Post by drdave69 on 2009-07-06
> **lukeiamyourfather said:**
> The hard disk may have been damaged in the power failure. I'd try booting with the installation disc and using the recovery option try to see if the hard disk still shows up with fdisk -l or another hard disk tool. Or if you have another system, pop the drive in there and try to mount it (another Linux system that is). Cheers!

trying now

---

