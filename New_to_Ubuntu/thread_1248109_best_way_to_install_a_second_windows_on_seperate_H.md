---
title: "best way to install a second windows on seperate HD"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by whitethorn on 2009-08-23
Hi,

I have windows 7 64-bit installed on a raid 0 in my pc, and ubuntu is installed in a partition afterwards, dual boot works gr8 I use windows only for gaming. The problem I have a couple games that just don't run well on the 64-bit platform.  I want to install a 32-bit version on a 80Gb harddrive, I was wondering what's the best way to go about it.  

I was thinking I could unplug my other two hdds and install windows to the hd, then edit my grub to include the new installation. I think this is the easiest way because I don't want grub to get overwritten, it was a little complicated getting grub on my raid 0 in the first place. Any suggestions?

---

### Post by nhasian on 2009-08-23
whatever happened to that windows 7 compatibility mode?  that does work in that instance?

the only problem i see with your plan is that if you remove the other hard disks from your setup when you install windows 7 32bit then when you try to boot windows 7 32bit it will expect to be HD0 when its gonna endup HD3 or whatever.  

another good idea is backup your grub!

---

### Post by mikewhatever on 2009-08-23
I think it best to ask at a proper place.
[http://www.microsoft.com/communities/forums/default.mspx](http://www.microsoft.com/communities/forums/default.mspx)

Best of luck.

---

### Post by whitethorn on 2009-08-27
Since I didn't want to lose my raid 0 by unplugging my other two hds, so I just ran the installer and installed it to the extra hd.  Luckily it didn't touch grub, so all I had to do was add an entry to grub and it works.

---

