---
title: "Windows 7 upgrade, grub2 fix didn't work"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Kilarin on 2009-12-06
I have messed up BIG TIME.
I've got an HP G60 441US laptop.  Running Ubuntu 9.10 and Windows Vista, dual boot.

I upgraded to windows 7, and it wiped out the grub2 boot, of course.
BUT, since there are very simple instructions for correcting this here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
And since my installation looks very much like the example, I thought this would be no big problem.   I duplicated the instructions on that page, and here is a cut and paste from my terminal window:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a127dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18715   150327213+   7  HPFS/NTFS
/dev/sda2           37488       38913    11451392    7  HPFS/NTFS
/dev/sda3           18716       37487   150786090    5  Extended
/dev/sda5           18716       36720   144625131   83  Linux
/dev/sda6           36721       37487     6160896   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sda5/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
ubuntu@ubuntu:~$ 

```

And everything looks great to my ignorant eyes.  But when I reboot, I get the sh:grub> prompt.    YIKES!!!!!

Please, any help would be greatly appreciated.  What have I done wrong, and what do I need to do to fix it?!?  

thanks in advance!

---

### Post by Kilarin on 2009-12-06
Aha!  I may have figured one important detail out.  
This computer did not START with grub 2, it first had ubuntu 9.04 installed, and was then upgraded later to ubuntu 9.10.  That does NOT automatically upgrade grub, right?

BUT, does that mean that by doing the grub-install command I've wiped out something important needed for grub?

---

### Post by oldfred on 2009-12-06
You can see what version you have:

Grub version
grub-install -v

If grub2 try this more complete version of reinstall, if grub legacy go back and reinstall per instructions in your first post:
Try reinstalling grub2 per these instructions, you probably do not have to edit /etc/default/grub

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Kilarin on 2009-12-07
Yes indeed, that was it.  

I had to [uninstall grub2](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
And install grub legacy.  followed those instructions up through the "sudo update-grub" step, and then skipped the "sudo grub-install /dev/sdX" step and followed the instructions for legacy grub from my first post.

Now I can boot into Ubuntu OR windows 7 again.   The grub menu still thinks its windows vista, but selecting that option boots windows 7 just fine.  Everything works.

Thank you very much!  I appreciate the help!

---

