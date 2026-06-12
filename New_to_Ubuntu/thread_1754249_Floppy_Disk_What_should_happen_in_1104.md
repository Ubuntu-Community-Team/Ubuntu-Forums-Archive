---
title: "Floppy Disk: What should happen in 11:04?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by marvin_littlewood on 2011-05-09
Hello!
 
I installed XUbuntu 11.04 Natty Narwhal on an old laptop and almost all is working fine. One minor issue remains: what should happen when I insert a floppy into the built-in drive?
 
Should it be auto-detected and mounted automatically?
Should an icon appear?
 
FWIW My USB memory sticks and external USB hard-drive all work as expected: an icon appears notifying me of their existence and providing me with the option of ejecting them. 
 
Note: I can mount the floppy with: ```
udisks --mount /dev/fd0
``` When I do this, the disk is available via: /media/floppy. So reading/writing a floppy is not the problem.
 
Thanks for any help you can give.
 
Marv

---

### Post by stlu on 2012-01-01
I think the bigger problem now is that floppy support is becoming less and less.

However, I don't think that floppy disks ever did "auto-detect" on i386 machines, regardless of whether you were running Linux or windows.  I only recall old macs which actually detected floppy disks automatically.

In Ubuntu 9.04, you could click on the floppy drive icon and it would then mount the floppy.  It worked for FAT formatted floppies, but oddly enough, encountered an error with ext2 formatted floppies.

I haven't been able to do that with 10.04.0 or 11.10, using the graphical icons.  If you are mounting the disk successfully in the terminal, that's pretty much what you can expect to have to do in the default install.

---

### Post by coffeecat on 2012-01-01
The OP has not logged in for more than 6 months. Although the thread is less than 1 year old, I'll close it. If anyone needs help with mounting floppies in recent versions of x/k/l/ubuntu, please start a fresh thread.

Thread closed.

---

