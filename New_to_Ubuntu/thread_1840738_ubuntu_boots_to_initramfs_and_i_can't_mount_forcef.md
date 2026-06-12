---
title: "ubuntu boots to initramfs and i can't mount forcefully"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by arjunajith on 2011-09-08
It started when I lost power when I was using ubuntu 11.04 Natty.
And when I turned it back on, I got the initramfs prompt with instructions asking me to run chkdsk from windows, in which i installed ubuntu as a subprogram.
I did, but didn't work.


i tried to mount forcefully using
```
mount -t ntfs 3g/dev/sda1/root -o -force
```
But then I get a 
```
/etc/fstab not found error
```
and it returns to the initramfs prompt.

Can anyone suggest a way out?

---

### Post by Rubi1200 on 2011-09-08
Hi and welcome to the forums :-)

Please download and post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by arjunajith on 2011-09-08
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Please download and post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

Thank you,
But when i tried to boot with my natty live cd I get something like a busy box and the initramfs prompt. 
Saying that they're unable to find a media using live file system...

```
BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a....

(initramfs) Unable to find a medium containing a live file system
_

```

---

### Post by Rubi1200 on 2011-09-08
I recommend downloading and running Slax as a LiveCD and see if you can boot the computer with it.
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

---

