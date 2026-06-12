---
title: "Need help with GRUB"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by chriscross93 on 2009-04-11
I recently installed mythbuntu on my system to try it out.  It is on it's own partition and when installed it recognized my other OSes (Ubuntu and XP).  My problem is that now it's install of GRUB controls booting up, and not my main ubuntu installation.  I need to switch it back to my main ubuntu install because I need to format the mythbuntu partition (need the space). So this is what I have....
PARTITIONS:
-Ubuntu 8.10 - My day to day use OS
-Winodows XP Pro
-Mythbuntu 8.10 - What I need to get rid of, but this is where GRUB is.

What I need....
PARTITIONS:
- Ubuntu 8.10 - My day to day OS (Where I need Grub to be)
- WIndows XP Pro

I can do all the re-partitioning easily, but I don't know much about GRUB.  Hopefully all this makes sense!

---

### Post by supersonicdarky on 2009-04-11
I'd assume that ubuntu's grub is still there but not being used. If that's the case you can just remove the mythbuntu partition, resize, etc. If it doesn't work right off the bat, you may need to (re)add boot flag to the ubutnu partition.

---

### Post by Yvan300 on 2009-04-11
After reading your post all you got to do is grab your ubuntu live cd, use gnome partition editor to delete mtythbuntu, and just follow the instructions on [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to restore grub and your done :)

---

### Post by chriscross93 on 2009-04-11
Cool thanks for the info, I figured it was easy enough but I didn't want to mess anything up. :guitar:

---

