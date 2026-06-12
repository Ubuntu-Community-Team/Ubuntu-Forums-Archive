---
title: "Boot problem"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by symmys on 2009-08-05
I had WinXp installed on my primary Hdisk and Ubuntu 8.04 installed on a second disk. Boot loader was on the first disk. 

I have installed Ubuntu 9.04 on the second disk and the (new) boot loader on the second disk. Now I can boot in Ubuntu from the second disk but not in WinXP. When I try to boot in WinXP from the second disk I get the message "Grub Error 13: "Invalid or unsupported executable format". 
 
When I try to boot from the first disk I get Error 22.

Any help? 

My menu.lst:

```
title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro  single
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
```

My fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbad6bad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4dcb4dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9331    74951226   83  Linux
/dev/sdb2            9332        9729     3196935    5  Extended
/dev/sdb5            9332        9729     3196903+  82  Linux swap / Solaris

```

---

### Post by Ji Ruo on 2009-08-05
The following should get GRUB working, booting from the first hard disk. Go into Ubuntu, then navigate to Applications>Accessories>Terminal. Type:```
sudo grub
```then enter your password and you will be in the GRUB editor. Then -```
root (hd1,0)
setup (hd0)
quit
```

restart and see if XP is working now

---

### Post by symmys on 2009-08-05
Thanks!
I've just repair the mbr on the first disk with Windows Recovery Console --> Fixboot --> Fixmbr

Windows still does not boot from the second disk with the grub.

---

### Post by Ji Ruo on 2009-08-05
Those instructions were for getting GRUB to boot from the first hard disk, like you had originally with 8.04. You will need to do it again if you want to do this, as you have just overwritten the GRUB if you tried to repair the MBR. 

If you're able to choose whether to boot from the first or second hard disk, you've confirmed that the repair worked (by booting from first hard disk, XP runs) and you want to boot from second hard disk you would do this:```
sudo grub
root (hd1,0)
setup (hd1)
quit
```It's important to confirm that you've fixed the Windows MBR as it doesn't always work (people often have trouble with it.)

I hope it works for you, I've never had to do this myself. Instructions are from here: [http://www.dedoimedo.com/computers/grub.html]("http://www.dedoimedo.com/computers/grub.html"). If it doesn't, you could always reinstall and choose to put GRUB on the first hard disk. There is also [Super Grub Disk]("http://www.supergrubdisk.org/").

---

### Post by oldfred on 2009-08-05
Is the order of your windows entry in menu.lst important? I always see chainloader +1 as the last line.

I have two 9.04 ubuntu installs old 32 bit upgraded from  6.10 and a new 64 bit clean install in a chainload config - both entries work.

my old win entry
# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

My newer entry from the clean install of 64 bit Jaunty
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

---

