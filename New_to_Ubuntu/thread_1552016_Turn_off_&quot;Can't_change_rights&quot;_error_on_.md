---
title: "Turn off &quot;Can't change rights&quot; error on NTFS partition"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-08-13
Hello!

Each time I copy something on the NTFS partition of my computer, I get a "Can't change rights" error message in the end (it copies without problems though). And when I try to delete something, it tells that it can't move it to trash and asks me if I want to delete it directly.

I'm fine with that (probably an NTFS thing), I was just wondering whether I can turn off those error messages for that specific partitions because I know it will be deleted at once or that Ubuntu can't change the rights and don't need that error message all the time.

So is there a way to turn off those two error messages for that specific partition?

I'm using Kubuntu 10.04 64bit, Peppermint One 32bit (which should be based on Ubuntu) and Windows 7 and a NTFS drive to share data between the three.

Thank you very much,

Blutkoete

---

### Post by jtarin on 2010-08-13
You have a file ["/etc/fstab" ]("http://ubuntuforums.org/showthread.php?t=283131")which controls this behavior.

---

### Post by Blutkoete on 2010-08-13
Thank you very much! Especially for understanding my embarrasing translation of the German term "Rechte" with "rights" instead of "permissions".

So it wasn't an NTFS problem at all (I thought that the Linux permission system wasn't compatible).

Now the trash works and the only files complaining when copied are EXEs, which I'm trying to sort out now (won't hurt me do to learn more about permissions and fstab).

---

