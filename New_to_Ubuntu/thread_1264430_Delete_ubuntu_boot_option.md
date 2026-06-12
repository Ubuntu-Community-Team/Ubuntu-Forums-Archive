---
title: "Delete ubuntu boot option ?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-09-12
I recently installed Ubuntu with Windows option for a friend , now they have decided they want it removed and just boot straight into Windows . Can this be done ? ( and if so how please )

---

### Post by thelegionsplayer on 2009-09-12
uninstall ubuntu?

---

### Post by knepig91 on 2009-09-12
It is impossible.

---

### Post by louieb on 2009-09-12
Sure you can, but not enough info - how did you install Ubuntu (wubi or tradtional)? Which version of windows?

---

### Post by talsemgeest on 2009-09-12
> **louieb said:**
> Sure you can, but not enough info - how did you install Ubuntu (wubi or tradtional)? Which version of windows?
If it is a traditional Ubuntu install, boot from the live cd, delete the ubuntu partitions using the partition manager, then follow my how-to for the version of windows [here.]("http://talsemgeest.doesntexist.com/2009/09/10/bootloader-how-to/")

---

### Post by o0splitpaw0o on 2009-09-12
1. insert the windows CD
2. select off the windows CD to boot to command prompt
3. type in **fixboot**
4. exit
5. insert the Ubuntu CD
6. goto System > Administration > Disk partitioner 
7. Select the EXT 3 > delete it
8. select the Linux Swap > delete it
9. Select the ntfs partition > Select resize
10. tell it to take 100% of the drive space
11. exit & reboot, removing the CD
12. allow Widnows do a Chkdisk > suggest your defrag

Sorry you skippin' on the install, but next time try Wubi install. You can just select add/remove from Control panel if you wish to skip on using it.

o0splitpaw0o

---

### Post by talsemgeest on 2009-09-12
> **o0splitpaw0o said:**
> 1. insert the windows CD
2. select off the windows CD to boot to command prompt
3. type in **fixboot**
4. exit
5. insert the Ubuntu CD
6. goto System > Administration > Disk partitioner 
7. Select the EXT 3 > delete it
8. select the Linux Swap > delete it
9. Select the ntfs partition > Select resize
10. tell it to take 100% of the drive space
11. exit & reboot, removing the CD
12. allow Widnows do a Chkdisk > suggest your defrag

Sorry you skippin' on the install, but next time try Wubi install. You can just select add/remove from Control panel if you wish to skip on using it.

o0splitpaw0o
That will work only for windows XP, not for Vista or Windows 7. All the instructions are on the link I posted.

---

### Post by louieb on 2009-09-12
> **talsemgeest said:**
>  then follow my how-to for the version of windows [here.]("http://talsemgeest.doesntexist.com/2009/09/10/bootloader-how-to/")

Nice redo of catlets post. One thing in the restore XP section. Believe fixboot needs a drive letter... fixboot  c:

fixboot doesn't give an error message. Also most of the time running fixmbr alone is enough to get XP booting again.

---

### Post by talsemgeest on 2009-09-12
> **louieb said:**
> Nice redo of catlets post. One thing in the restore XP section. Believe fixboot needs a drive letter... fixboot  c:

fixboot doesn't give an error message. Also most of the time running fixmbr alone is enough to get XP booting again.
Thanks for that, I will look into it. :)

---

### Post by ex-wirecutter on 2009-09-13
Many thanks for your advice and suggestions .

---

### Post by talsemgeest on 2009-09-13
> **ex-wirecutter said:**
> Many thanks for your advice and suggestions .
No problem, always happy to help :)

---

