---
title: "Cant change permissions for files on External Drive"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by FrostBlue on 2011-02-09
Hi 
I have an external drive which I have used with Kubuntu before and everything was fine. After using this disk with windows for a while , now I cant change permissions for any file at all. If I copy files from my root disk over to external , I cant touch them at all.

The file system is fuseblk , ntfs as I understand...

I am trying to use this guide 

[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

to change the file to read/write and executables to executables , but I just dont have enough time to try all options could someone please help.

Heres the output of df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4   147550696  21127592 118927936  16% /
none      devtmpfs     1538708       260   1538448   1% /dev
none         tmpfs     1545560         0   1545560   0% /dev/shm
none         tmpfs     1545560       208   1545352   1% /var/run
none         tmpfs     1545560         0   1545560   0% /var/lock
/dev/sdb1  fuseblk   976760032 422796820 553963212  44% /media/Expansion Drive


Thanks a lot.

---

### Post by cariboo on 2011-02-09
NTFS can't use linux permissions, the only thing you can do is set ownership and permissions of the mount point.

---

### Post by FrostBlue on 2011-02-10
Wow...I thot NTFS was fine...What changed my permissions in the first place... I had just loaded the drive on Win 7 for a while and then back on Kubuntu...no executables are working.

Could you give me an example command...how would I set permissions for the mount point permanently ?

Thanks for quick reply.

---

