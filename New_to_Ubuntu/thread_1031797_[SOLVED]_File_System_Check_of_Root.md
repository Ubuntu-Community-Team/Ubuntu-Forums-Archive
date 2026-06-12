---
title: "[SOLVED] File System Check of Root"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mity on 2009-01-05
Hello,

on the boot up i receive the following error messages:

" unexpected inconsistency; run fsck manually
  fsck died with exit status 4

  Automatic file system check of root filesystem failed
  manual FSCK must be performed. then the system restarted.
  the FSCK should be performed in maintaince mode with the root filesystem mounted in read-only mode

the root filesystem is currently mounted in read-only mode.
a maintance shell will now be started.

after performing sysrtem manitance, press control-d to termonate the maintance shell and restart the system. 

give root password for maintance"

when i enter my password ( the one i have to enter everytime i install something), i recieve an invalid login error. 

what should i do?

---

### Post by jerome1232 on 2009-01-05
Hmmm, I would try booting into recovery mode and tell it to fsck the disks from there.

Just select the newest recovery kernel from you grub menu (if you don't get this menu then hit esc when you see grub loading)

There should be an option to check your disks in there.

---

### Post by mity on 2009-01-05
Thank you for a response.

i get the same error when i boot into recovery mode.

---

### Post by gn2 on 2009-01-05
You can run fsck from a booted live CD.

In a terminal run: ```
fsck /dev/sda1 (where sda1 is your / partition)
```

---

### Post by mity on 2009-01-09
i finally got a hold of a live cd. 

when i type that command into terminal it tells me that i need to have root access. 

should i just preface this command with su to be a root user?

thanks

---

### Post by taurus on 2009-01-09
You need to include the sudo in front of the command.

```
sudo fsck /dev/sda1
```
Assuming /dev/sda1 is the one you want to fsck.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mity on 2009-01-09
that did the trick. thank you all.

---

