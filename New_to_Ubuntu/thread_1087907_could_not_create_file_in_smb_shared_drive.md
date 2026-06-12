---
title: "could not create file in smb shared drive"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by EnterTheDarkSide on 2009-03-05
i mounted a windows shared drive in ubuntu like this:

sudo mount -t smbfs //winxp_pc_addr/share_drive /mount_point -o user=user,pass=pass,rws

the drive was mounted successfully, however when i tried to save something into the share_drive i get a permission denied error. the user/pass i provided was the administrator info and the share_drive in winxp was setup to recognize the user/pass(i've done it from a xp-to-xp environment). 

could anyone help me and tell why i can't write to the share_drive

---

### Post by Iowan on 2009-03-05
Check the permissions for /mount_point.
BTW, smbfs has been deprecated in favor of cifs. [This]("http://ubuntuforums.org/showthread.php?t=288534") How-To has extensive information.

---

### Post by EnterTheDarkSide on 2009-03-06
Hi Iowan, the permission for mount_point is 777. i specifically did a chmod to it after mounting but still could not write to the shared drive. i will read up the link you provided and see if i can find an alternate solution. thanks for the reply.

---

