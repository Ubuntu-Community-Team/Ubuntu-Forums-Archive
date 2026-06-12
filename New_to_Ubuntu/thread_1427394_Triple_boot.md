---
title: "Triple boot"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by just4u on 2010-03-11
Hello
I'm trying to setup a triple boot option in grub leagacy, I have XP on my  IDE drive (hda) and Debian and Kubuntu (Karmic Koala) 9.10 i386 on my 2nd drive (SATA) Debian's root is sda1 and Kubuntu's root is sda10.

I've edited grub menu.lst and all three show up in the boot loader opening screen and I can start XP or Debian but Ubuntu gives me a error 15 file not found. I've loaded rescue thru Kubuntu cd and mounted sda10 and checked that the vmlinuz and initrd are there, also they are linked from the root of sda10.

I'm missing something but don't know what any help would be appreicated.

Here is a copy of my menu.lst  

title                  Debian GNU/Linux, kernel 2.6.26-2-amd64
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd                /boot/initrd.img-2.6.26-2-amd64

title                  Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd                /boot/initrd.img-2.6.26-2-amd64


title                   Kubuntu GNU/Linux, kernel 2.6.31-14-generic
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.31-14-generic root=/dev/sda10 ro quiet
initrd                /boot/initrd.img-2.6.31-14-generic

title                   Kubuntu GNU/Linux, kernel 2.6.31-14-generic (single-user moder)
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.31-14-generic root=/dev/sda10 ro single
initrd                /boot/initrd.img-2.6.31-14-generic


Here is fdksk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007703d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          43      345366   83  Linux
/dev/sda2              44       36483   292704300    5  Extended
/dev/sda5              44         651     4883728+  83  Linux
/dev/sda6             652        1016     2931831   83  Linux
/dev/sda7            1017        1580     4530298+  82  Linux swap / Solaris
/dev/sda8            1581        1629      393561   83  Linux
/dev/sda9            1630       19185   141018538+  83  Linux
/dev/sda10          19186       35920   134423856   83  Linux
/dev/sda11          35921       36483     4522266   82  Linux swap / Solaris

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/hda2           19123       36480   139428135    f  W95 Ext'd (LBA)
/dev/hda5           19123       36480   139428103+   7  HPFS/NTFS
Purelight:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             327M  129M  182M  42% /
tmpfs                 755M     0  755M   0% /lib/init/rw
udev                   10M  840K  9.2M   9% /dev
tmpfs                 755M     0  755M   0% /dev/shm
/dev/sda9             133G  195M  126G   1% /home
/dev/sda8             373M   11M  343M   3% /tmp
/dev/sda5             4.6G  2.2G  2.2G  51% /usr
/dev/sda6             2.8G  530M  2.1G  20% /var
/dev/sr0              4.4G  4.4G     0 100% /media/cdrom0

---

### Post by srs5694 on 2010-03-11
> **just4u said:**
> Hello
I'm trying to setup a triple boot option in grub leagacy, I have XP on my  IDE drive (hda) and Debian and Kubuntu (Karmic Koala) 9.10 i386 on my 2nd drive (SATA) Debian's root is sda1 and Kubuntu's root is sda10.

I've edited grub menu.lst and all three show up in the boot loader opening screen and I can start XP or Debian but Ubuntu gives me a error 15 file not found.
...
Here is a copy of my menu.lst  

title                  Debian GNU/Linux, kernel 2.6.26-2-amd64
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd                /boot/initrd.img-2.6.26-2-amd64

title                   Kubuntu GNU/Linux, kernel 2.6.31-14-generic
root                 (hd1,0)
kernel              /boot/vmlinuz-2.6.31-14-generic root=/dev/sda10 ro quiet
initrd                /boot/initrd.img-2.6.31-14-generic


Unless you've copied your Ubuntu vmlinuz-2.6.31-14-generic file from Ubuntu's /boot to Debian's /boot, you should specify "root (1,9)" on your Ubuntu stanzas (groupings of GRUB configuration lines for booting a kernel or OS), not as "root (1,0)". The "root (hdx,y)" option tells GRUB where to look for the files you reference in that stanza. Note that this is entirely independent of the "root=/dev/sdx" option on the "kernel" line.

---

### Post by just4u on 2010-03-11
> **srs5694 said:**
> Unless you've copied your Ubuntu vmlinuz-2.6.31-14-generic file from Ubuntu's /boot to Debian's /boot, you should specify "root (1,9)" on your Ubuntu stanzas (groupings of GRUB configuration lines for booting a kernel or OS), not as "root (1,0)". The "root (hdx,y)" option tells GRUB where to look for the files you reference in that stanza. Note that this is entirely independent of the "root=/dev/sdx" option on the "kernel" line.

Ok I changed root in menu.lst to (1,9) and got error 15 file not found.
I then tryed root as (1,10) and recieved the error 17 unable to mount partition.

The reason I tryed (1,10) is Kubuntu installed on sda10, should sda10 be bootable?  Can linux boot from a logical drive ?

---

### Post by coffeecat on 2010-03-11
Edit: Error - need to re-read your first post and rewrite this post.

Edit2 - what confused me at first was your having both hda and sda - I guess that fdisk output is from Debian. I haven't seen a hda reference for about three years. Ubuntu and most other distros are now using the libata kernel drivers for both SATA and PATA, so that both types appear as sdx. So my guess is that that is the clue to the solution.

Kubuntu is going to see those two drives as sda and sdb - I guess the ide as sda, and the SATA as sdb. So - if I'm right - the stanza for Kubuntu would need to be:

```
title                   Kubuntu GNU/Linux, kernel 2.6.31-14-generic
root                 (hd1,9)
kernel              /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb10 ro  quiet
initrd                /boot/initrd.img-2.6.31-14-generic
```The root reference in the kernel line is for the kernel to read - that is why it needs to be sdb10, which is how the Kubuntu kernel will see it - if my guess is right.

If you want, you could boot up with the Kubuntu live CD and run 'sudo fdisk -l' before you edit menu.lst to see how Kubuntu sees the two drives.

Edit3: yes, Linux can boot from a logical partition. :)

---

