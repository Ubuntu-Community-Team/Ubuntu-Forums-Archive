---
title: "Spash missing"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-01-28
hey everyone,

Not a major problem, but my splash screen disappeared. My Ubuntu boots in text mode and runs great. I tried reinstalling the splash screen via synaptic and no go. I tried to use the startup manager and make sure splash is ticked and no text boot is ticked, still no go.

No biggy, but not as pretty. Any ideas how I can fix this.

Thanks


Info:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**[COLOR="Red"]Searching for splash image ... none found, skipping .[/COLOR]**..
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by Crafty Kisses on 2009-01-28
Have you tried changing the resolution in GRUB? Open the GRUB configuration file by doing the following:
```
sudo gedit /boot/grub/menu.lst
```
Look for the line that says something similar to this:
```
vga=xxx
```
The X's represent numbers, there's only these possible resolutions you can change it to:
```
640x480/vga=785
800x600/vga=788
1024x768/vga=791
1280x1024/vga=794
```
Try and change the resolution and see if that does anything for you.

---

### Post by caljohnsmith on 2009-01-29
Loyaleagle, how about posting the output of the following commands:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by loyaleagle on 2009-01-30
sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd894f49c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299805029   149902483+  83  Linux
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris

Sudo blkid -c /dev/null

/dev/sda1: UUID="d9e4252b-b62d-4362-8362-1c5b4ea7bdd8" TYPE="ext3" 
/dev/sda5: UUID="d521bbe8-e62b-4791-8d5f-824e3d78dff3" TYPE="swap" 

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d9e4252b-b62d-4362-8362-1c5b4ea7bdd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d521bbe8-e62b-4791-8d5f-824e3d78dff3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

cat /etc/initramfs-tools/conf.d/resume

RESUME=UUID=d521bbe8-e62b-4791-8d5f-824e3d78dff3

---

### Post by caljohnsmith on 2009-01-30
So just to clarify, are you referring to losing the Ubuntu splash screen on start up, and not a splash image in your Grub menu, is that right? If that is true, can you think of anything you did in Ubuntu just prior to when you lost the splash screen? Did you change anything with usplash? Install any other significant software?

---

### Post by loyaleagle on 2009-01-30
Yes.... just the Ubuntu Spash Screen (not Grub). Have not really installed any software. Just using Ubuntu regularly.

Thanks....

---

### Post by caljohnsmith on 2009-02-02
How about trying:
```
sudo apt-get purge usplash
sudo apt-get install usplash
```
Then reboot, and let me know if that changes anything.

---

