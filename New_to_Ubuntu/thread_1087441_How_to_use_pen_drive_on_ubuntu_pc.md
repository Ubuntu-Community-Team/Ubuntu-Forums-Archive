---
title: "How to use pen drive on ubuntu pc?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by atulbamne on 2009-03-05
Dear ubuntu community,

I am a new user to ubuntu and forgive me for my simple question. Previously I used windows XP. When we insert a pen drive in XP the same is automatically detected. After use we click the pen drive icon at right bottom and click safely remove hardware. After this the pen drive is closed by the windows and it says you can safely remove the hardware.

While in ubuntu, detection is very fast. However after the use I don't know the command by which the said pen drive can be closed by OS. Shall we remove it while it's light is on? Or there is any command to remove the pen drive from OS?

Please help for which I'll be grateful.

Thanks.

---

### Post by Lod on 2009-03-05
One way to do it is to right click on the drive its icon on the desktop and select unmount. The icon will disappear from the desktop and it's save to remove it (even when the light is  still on).

---

### Post by sazan on 2009-03-05
use -> ```
umount /mnt
``` to umount your pen drive, else no data will be written in your pen drive.

---

### Post by atulbamne on 2009-03-05
Thanks a lot. In short, I can remove my pen drive even when the light is on.

---

### Post by atulbamne on 2009-03-05
Thanks for immediate help.

---

### Post by sazan on 2009-03-05
yes it is safe to remove even if your light is on after you have unmounted the disk.

Cheers

---

### Post by sgosnell on 2009-03-05
The easy way for me is to just click on the eject icon in Nautilus file manager.  That unmounts the drive.  If there's an icon for it on the desktop, you can right-click on that and select Unmount Volume, as Lod said.

---

### Post by abhishek.malhotra35 on 2009-03-05
I faced an issue when I was trying to unmount by right clicking on pen drive icon. It was mounting again. Its better you unmount the pen drive by command line. 
umount /dev/sdb1(if your pendrive is sdb1).

---

