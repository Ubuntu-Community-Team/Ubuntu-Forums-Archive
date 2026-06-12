---
title: "Error: out of disk.  Grub rescue&gt;"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by imjoewhite on 2010-06-16
ok so i just installed Ubuntu 10.04 LTS on my older i dont know how old it is. pc. it came with xp ran 7 for a while but 7 keeps messing up. so i tryed to install Ubuntu 10.04 LTS but after it installs and im to reset it. i get this screen full of errors and 0's and 1's i hit enter and it resets. 

I then get. 

Error: out of disk.  Grub rescue>

I have Ubuntu 10.04 LTS installed on this pc  a dell dimension 9100 and it works greight.

So please help. 

Thank you!

---

### Post by drascus on 2010-06-17
I Think you should boot from the disk and check the integrity of the hard drive. If there is problem sectors or your hard drive is failing you might be running into constant problems. If the drive is fine just try reinstalling.

---

### Post by briancfletcher on 2010-09-19
Yeah, I spent a lot of time with this one.  My hard drive was bad.  Went to System>Administration>Disk Utility, clicked on my hard drive icon and SMART data showed that I had thousands of bad sectors on the disk.  I plugged a new hard drive, installed Ubuntu 10.04.1 LTS and all is now fine.  Then used the old disk as a slave drive and retrieved my old files.  Hope this helps.

See also [http://ubuntuforums.org/showthread.php?p=9866320#post9866320](http://ubuntuforums.org/showthread.php?p=9866320#post9866320).

---

