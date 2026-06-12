---
title: "Rash os install"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-30
Hi,

Ive installed Gnewsense on my sda1 and i no longer have the option to load Ubuntu 10.04 on sda2 at boot. As Gnewsense is ext 3 i cannot access my files in my Ubuntu Home dir. Can i simply switch my boot to sda2 ? It will solve my problem for the medium term.

Thanks for your time.

---

### Post by nnjond on 2010-07-30
Hi,

Ive installed Gnewsense on my sda1 and i no longer have the option to load Ubuntu 10.04 on sda2 at boot. As Gnewsense is ext 3 i cannot access my files in my Ubuntu Home dir. Can i simply switch my boot to sda2 ? It will solve my problem for the medium term.

Thanks for your time.

---

### Post by snowpine on 2010-07-30
Boot with an Ubuntu 10.04 Live CD and reinstall GRUB2 following these instructions:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by nnjond on 2010-07-30
Thanks for your interest.

Ive hit more problems following that advice:



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5a45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240000   83  Linux
/dev/sda2            1275       60290   474038401   83  Linux
/dev/sda3           60291       60801     4104607+   5  Extended
/dev/sda5           60292       60801     4096575   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
mount: /dev/sda2 already mounted or /mnt busy
mount: according to mtab, /dev/sda2 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$

---

### Post by jerenept on 2010-07-30
install GRUB to /dev/sda.

That should fix your problem.

---

### Post by snowpine on 2010-07-30
Change:

```
sudo grub-install --root-directory=/mnt /dev/sda2
```

to:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

as per the example in the help page:

> Example: sudo grub-install --root-directory=/mnt/ /dev/sda 

---

