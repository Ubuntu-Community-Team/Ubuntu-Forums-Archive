---
title: "unable to mount windows share from the command line"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by grebulator on 2008-06-13
When trying to mount my windows share using 'sudo mount -t cifs //flem/Music /mnt/music -o username=mywindowsusername,password=mywindowspassword' i receive the error 'mount error 6 = No such device or address'

I have tried many variations of this including suffixing ',iocharset=utf8,file_mode=0777,dir_mode=0777' I have also replaced flem with the ip of the box but I still get the same error.

I know that I can connect to flem and access the share using nautilus and can ping it from the command line, I have placed and entry in /etc/hosts for flem, I have installed winbind and added edited /etc/nsswitch.conf to include wins.

I have looked trough many different threads but can't find an answer to this problem.

Can anyone help?

Thanks in advance

---

### Post by grebulator on 2008-06-15
**SOLVED**

I've managed to sort this issue out.....was making a dumb noob mistake :(

When sharing a drive in windows the default share name is *drive label (drive letter)* I initially got round this by enclosing it in single quotes like so '//flem/Music (G)' which was fine when mounting it manually, but when i came to include it in /etc/fstab so it mounted automatically this failed, so i went and changed the share name to omit the space, brackets and drive letter.

---

