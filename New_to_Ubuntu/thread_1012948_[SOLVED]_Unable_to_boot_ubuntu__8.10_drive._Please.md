---
title: "[SOLVED] Unable to boot ubuntu  8.10 drive. Please help"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by SandyM on 2008-12-16
I am using a Backup and restore software called Acronis true Image 2009. When I was using hardy I used to restore my Linux drive with a great success.

But since I started using intreprid, restoration of drive from disk image created with this software, was although successful but I was unable to boot the Linux and received the following message

[B]Boot Part 2.60 Boot sector (c) 1993-2005 gilles vollant [http://winimage.com/bootpart.htm](http://winimage.com/bootpart.htm)
Loading new partition
Boot sector from C.H Hochstatter cannot load from hard disk
Insert system disk and press any key [/B]

And when I enter any key, following text appears....

**No bootable device - insert boot disk and press any Key**



PLEAS HELP AS I HAVE VERY IMPORTANT DATA STUCK WITH THE IMAGE.

---

### Post by shifty_powers on 2008-12-16
looks like you need to restore the grub boot loader/

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

---

### Post by sandy8925 on 2008-12-16
I heard that the inode size or something like that has changed from Hardy to Intrepid.

I think that when Acronis restored the drive it must have used the old inode size or something like that whereas Intrepid expects the new inode size.  Thar just might be what's causing the problem but I don't know for sure.

---

### Post by SandyM on 2008-12-16
I alread installed grub with NeoSmart Easy BCD butthat was of no use too.

---

### Post by caljohnsmith on 2008-12-16
If you can boot your Ubuntu Live CD, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And for whichever is your Intrepid partition, please post:
```
sudo dumpe2fs /dev/[COLOR="Blue"]sdaX[/COLOR] | grep -i "inode size"
```
So change "sdaX" to whichever is your Intrepid partition. And lastly, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sudo sh ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by SandyM on 2008-12-18
It is not working either

---

### Post by _noob_ on 2008-12-18
What kind of image? If it's an ISO image you may have to burn it to a disk. If that is at all possible

---

