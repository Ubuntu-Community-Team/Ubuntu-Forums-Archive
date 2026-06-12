---
title: "Cannot read a CD?"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-03-13
Hi, I was on my windows pc and dropped some files onto a fresh CD, on the format menu I clicked on the portable option and not an audio CD and dropped the files on so I could use it again and again, so I put it on my ubuntu laptop and its giving me this error, I just want the files on the disc, so why is it mounting! #-o



Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thank you!

---

### Post by vnpifhf on 2011-03-13
Heres a screenshot.

---

### Post by sandyd on 2011-03-13
> **jahangir99 said:**
> Hi, I was on my windows pc and dropped some files onto a fresh CD, on the format menu I clicked on the portable option and not an audio CD and dropped the files on so I could use it again and again, so I put it on my ubuntu laptop and its giving me this error, I just want the files on the disc, so why is it mounting! #-o



Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thank you!
```

sudo mkdir /mnt/cdrom89h
sudo mount -t udf /dev/sr0 /mnt/cdrom89h 
ls /mnt/cdrom89h
```see if that works.

---

### Post by vnpifhf on 2011-03-13
jahangir@jahangir-Aspire-M1610:~$ sudo mkdir /mount/cdrom89h
mkdir: cannot create directory `/mount/cdrom89h': No such file or directory
jahangir@jahangir-Aspire-M1610:~$ sudo mount -t udf /dev/sr0 /mount/cdrom89h 
mount: mount point /mount/cdrom89h does not exist
jahangir@jahangir-Aspire-M1610:~$ ls /mount/cdrom89h
ls: cannot access /mount/cdrom89h: No such file or directory
jahangir@jahangir-Aspire-M1610:~$ 

Its not worked

---

### Post by sandyd on 2011-03-13
> **jahangir99 said:**
> jahangir@jahangir-Aspire-M1610:~$ sudo mkdir /mount/cdrom89h
mkdir: cannot create directory `/mount/cdrom89h': No such file or directory
jahangir@jahangir-Aspire-M1610:~$ sudo mount -t udf /dev/sr0 /mount/cdrom89h 
mount: mount point /mount/cdrom89h does not exist
jahangir@jahangir-Aspire-M1610:~$ ls /mount/cdrom89h
ls: cannot access /mount/cdrom89h: No such file or directory
jahangir@jahangir-Aspire-M1610:~$ 

Its not worked
finger slipped.
try again.

---

