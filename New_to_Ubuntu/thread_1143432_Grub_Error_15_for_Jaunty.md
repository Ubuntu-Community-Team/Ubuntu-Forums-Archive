---
title: "Grub Error 15 for Jaunty"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by paullyjunge on 2009-04-29
Hi guys,

Did a fresh install and now my machine won't boot without the error 15.

I have attached the results.txt after running the script from [here.]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

Not sure if it matters, but sdb is an IDE drive set as master on the primary IDE and sda is a SATA drive.  In my BIOS I have primary IDE as the first boot, I would have thought that Ubuntu would then make sdb be sda and vice versa.

Any thoughts on how to fix this?  I have been trying things for hours, but haven't made any headway! Please and thank you!

---

### Post by fenian on 2009-04-29
You need to be sure the drive with Ubuntu on it is set to boot first in the Bios.Seeing as you probably don't need the XFS drive to be bootable I would remove it from the boot sequence in the Bios.

---

### Post by paullyjunge on 2009-04-29
Hello, 

It is set as the first bootable drive, that is why this is confusing.

---

### Post by fenian on 2009-04-29
What happens if you start up from the Ubuntu Live CD and choose boot from first Hard Disk?

---

### Post by paullyjunge on 2009-04-30
got it figured out, I went into grub and did setup (hd0) and then setup(hd1).  I am assuming by doing so I installed grub to whichever drive boots first.  At first I disliked the UUID, but I guess this way it doesn't really matter which drive boots first!

:guitar:

thanks for the help!

---

