---
title: "Adding a Windows partition: is this the correct process?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2010-06-17
I've spent the last year without video games, and I think I'm about to change that.  I've just done a backup of all my data and want to make sure that I'm not going to ruin anything.

I've got a / and a /home partition, both of which are EXT4.  The /home partition is 300 GBs  (only about 90 GB of which is actually being used), and I'm going to use Gparted to shrink it to about 200-225GB.  Then I'm going to make the new empty space into NTFS and install Windows on that.  To end it, I'll use my LiveCD to reinstall GRUB and fix my boot process.

Am I forgetting anything?  Will I screw up my Ubuntu install due to something I haven't considered?

---

### Post by waynefoutz on 2010-06-17
That about covers it. 

Here is a pretty good guide to get grub back on so you can dual boot, the windows install will wipe it out and reset your MBR so it will only boot to Windows:


[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

That guide is pretty easy to follow.

---

### Post by Cuddles McKitten on 2010-06-18
Thanks.  Wish me luck!

---

### Post by RJ12 on 2010-06-18
Good luck! :KS

---

