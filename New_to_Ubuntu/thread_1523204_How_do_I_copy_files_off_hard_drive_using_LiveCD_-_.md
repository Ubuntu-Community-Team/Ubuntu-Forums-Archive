---
title: "How do I copy files off hard drive using LiveCD - permission problem"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Phillip Spencer on 2010-07-03
Hi, Ubuntu does not boot due to an accidental restore of Windows on a dual-boot system. I can see the files on the Linux partition using Nautilus when booting using LiveCD so want to back these up (copy the HOME folder and Evolution email file) to a portable hard drive prior to trying to restore Ubuntu. However, I cannot drag and drop from the Linux partition to the portable drive because the LiveCD user ID does not have the right permissions to copy from the files.

I know this is a basic question but a number of searches using different key words but nothing so far has helped.  I tried using "SUDO NAUTILUS" but this only gives root permission for the LiveCD.

Thanks for any pointers.
Cheers
Phillip

---

### Post by gallifrey on 2010-07-03
First of all, mount all the partitions necessary. Once mounted, press alt + F2 and type gksu natilus, and access your mounted partitions as normal. 

If that doesnt work, do the following:

In the live cd, open a terminal and type sudo passwd root, and hit enter. It will prompt you to enter a new password. Do so, and close terminal. LOG OUT (not shutdown) of the Live Cd session, and log in again, using the username root, and the password you just created. You should be able to access all your files and flders now, and act upon them anyway you want. 

Hope this helps.

---

### Post by gandaran on 2010-07-03
using the live cd type *sudo -i nautilus* in terminal and hit enter, no password required, it will just open root nautilus, you should now have read/write access to any drive.

---

### Post by Phillip Spencer on 2010-07-03
Thanks, Gallifrey!

The first part of the instruction did not work but the second, changing the root password, worked a treat.  >45Gb of my wife's files, including her business records are currently being backed-up.  At least I can then tackle the underlying problem knowing that if all else fails I can restore to a new Ubuntu install.

Really appreciate the prompt response.
Cheers
Phillip

---

### Post by Phillip Spencer on 2010-07-03
Just seen gandaran's note.  Thank you for this.  I will try this method later as it looks very straight-forward.  My Linux knowledge is building up slowly by trial and error... usually the error comes first!
Cheers
Phillip

---

