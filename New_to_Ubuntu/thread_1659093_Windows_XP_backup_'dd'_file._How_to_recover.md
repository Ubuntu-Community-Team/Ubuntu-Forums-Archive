---
title: "Windows XP backup 'dd' file. How to recover?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by e-San on 2011-01-03
Hi!

First of all - i did not know where to put my topci, so it lands here.

Before formating my drive to install Ubuntu 10.10 i made 'dd if=/dev/sda2 of=./windows.dd' copy.

Today i am trying to recover it, made some (a little bigger) partition (sda2, bootable too) and dd-copied partition file on sda2 device.

It wont boot at all. Partition seems to be filled with all my files.

What to do?

Regards!

---

### Post by bananas4370 on 2011-01-03
Boot off the windows cd and get into the recovery console. Run fixmbr and then fixboot. That should fix the situation.

Cheers
Patrick

---

### Post by e-San on 2011-01-04
Forget to mention i won't install new windows beacose i do not own CD-rom in my laptop.

Thanks for answering.
I made it with help from this topic: [http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146), thanks for Autor.

---

### Post by e-San on 2011-01-05
to delete

---

