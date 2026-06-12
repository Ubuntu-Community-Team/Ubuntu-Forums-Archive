---
title: "is only 1 partition (for UNR) okay?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by comethalley on 2010-04-19
Umm... so I kind of somehow deleted my Windows and parts of Ubuntu on my EEE pc 1005HA.  Got my live usb stick and ran ubuntu from there, and it miraculously worked.  But not I'm trying to reinstall ubuntu (decided not to bother with windows for now), so I went through the first steps of the install UNR widget.  But for the partitioning, it showed what my partition had been (I had chosen what it automatically did the first time I installed UNR to dual boot with windows), and it had had automatically made like 4 partitions.  This time it wants to automatically make only 1 partition, named UNR.  Is it safe for the computer to only have one partition?  Will I accidently delete something that will cause my computer to brick?  And if so, how should I set up the partitions correctly?  Thanks in advance!

---

### Post by Jon Monreal on 2010-04-19
I'm assuming that nothing else is installed currently?

Just use the "Guided - use entire disk option". It might only show one giant bar with Ubuntu, but you will get two partitions (one being linux-swap).

If you're concerned about what partitions might be there now and possibly deleting data, type
```
sudo fdisk -l
```
in the terminal in the live session, press enter, and copy+paste the output here.

---

