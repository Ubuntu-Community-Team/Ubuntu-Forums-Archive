---
title: "Cant install GRUB2...help?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-06-24
> ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
sudo: grub-install: command not found
ubuntu@ubuntu:~$ 
Im trying to install grub from the live CD (USB in this case) to the other USB..which has the full install on..

in a previous post i mentioned wanting to install 10.04 to another USb stick, but everytime  I do it, no matter how, it wont load grub..It just says something about the boot record not found.

please help me =[.

---

### Post by JamesParnell on 2010-06-24
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
??

root@ubuntu:/home/ubuntu# grub-setup /dev/sdc
Segmentation fault (core dumped)

---

### Post by jtarin on 2010-06-24
> Im trying to install grub from the live CD (USB in this case) to the other USB..which has the full install on.

If you have a full install of already, why are you trying to reinstall GRUB? Where does your GRUB reside now?

---

### Post by oldfred on 2010-06-24
Duplicate thread see

[http://ubuntuforums.org/showthread.php?t=1516752](http://ubuntuforums.org/showthread.php?t=1516752)

---

### Post by JamesParnell on 2010-06-24
[color=red]please lock, i moved this question to my original thread.

Thank you.
[/color]

---

