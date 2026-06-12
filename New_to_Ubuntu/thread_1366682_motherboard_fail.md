---
title: "motherboard fail"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by moz oz on 2009-12-28
Hi I am using  9.10
my motherboard just died
I installed a new motherboard and used the old HDD 160 G
I have the user and psw
how can I get it to work on a the new hardware
I have booted from CD have no disk permission to access files for recovery

Mr Moz

---

### Post by gordintoronto on 2009-12-28
You have "a new computer."  Use the LiveCD to back up your data and do a fresh install.  It's easiest if you have enough space on another networked computer.  Don't forget your email folders and browser favorites.

---

### Post by moz oz on 2009-12-28
Thank You
I will try it
regards
Moz

---

### Post by falconindy on 2009-12-28
> **gordintoronto said:**
> You have "a new computer."  Use the LiveCD to back up your data and do a fresh install.  It's easiest if you have enough space on another networked computer.  Don't forget your email folders and browser favorites.
This isn't Windows. Linux doesn't care if you completely change the hardware out from under it between boots as long as it can find sufficient drivers to bootstrap the kernel. In a distro such as Ubuntu, robust driver support is something they strive for.

OP doesn't necessarily need to reinstall -- he needs to further describe the problem.

---

### Post by gordintoronto on 2009-12-28
> **falconindy said:**
> This isn't Windows. Linux doesn't care if you completely change the hardware out from under it between boots as long as it can find sufficient drivers to bootstrap the kernel. In a distro such as Ubuntu, robust driver support is something they strive for.

OP doesn't necessarily need to reinstall -- he needs to further describe the problem.

And yet, I often see messages from users who have grievous problems just from changing video cards.

---

### Post by falconindy on 2009-12-29
> **gordintoronto said:**
> And yet, I often see messages from users who have grievous problems just from changing video cards.
Likely because they decided not to uninstall the current video drivers before dropping in the new card. Still not something you need to reinstall over.

---

### Post by Cheesemill on 2009-12-29
> **falconindy said:**
> This isn't Windows. Linux doesn't care if you completely change the hardware out from under it between boots as long as it can find sufficient drivers to bootstrap the kernel. In a distro such as Ubuntu, robust driver support is something they strive for.

+1
Just boot up the new machine with the old drive, it will work fine.

---

### Post by sandy8925 on 2009-12-29
> 
Just boot up the new machine with the old drive, it will work fine.


Only as long as you connect it in the same or similar way. Since grub uses uuid from jaunty onwards it will probably still boot if you changed the hard disk from primary to secondary or vice versa.

---

