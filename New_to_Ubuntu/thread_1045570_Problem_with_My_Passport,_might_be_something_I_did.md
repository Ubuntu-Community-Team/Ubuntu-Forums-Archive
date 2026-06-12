---
title: "Problem with My Passport, might be something I did"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by SunnyRabbiera on 2009-01-20
I know this is a duplicate, but just in case I will repost this topic.
Alright I got a WD my passport 250GB external hard drive, but now I have a problem... it wont mount.
Now it did mount before, and when it did I decided to remove the windows drivers as I am not using windows but this might have been a big mistake!
I thought that I could wipe out those files on the WD without hurting it, but no it doesnt allow it to me mounted.
I tried this:
sudo fdisk -l

It didnt see the drive, period!
What should I do?
Take it back because I messed up?

Also, it seems this drive works fine in windows...
Wierd, and I cant find software online for it

---

### Post by AegisTalons on 2009-01-21
What do you mean you "removed the Windows Drivers"? When you got the hard drive, was it completely empty, probably needing a format, or did it come preload with software?

---

### Post by handydan918 on 2009-01-21
I'm assuming that it's a USB drive, so what does ```
lsusb
``` show you ? 

What if you plug in the drive and do ```
dmesg | tail -20
```?

---

