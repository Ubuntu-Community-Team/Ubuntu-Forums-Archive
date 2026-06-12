---
title: "Installed Ubuntu, Still boots straight to XP"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Go_Big_Blue on 2010-01-11
I've searched and haven't found a solution for this one yet, but here goes. I took a 160GB hard drive and split it into 4 partitions, 1 for Windows XP, 1 for Ubuntu, 1 for swap and 1 for future use (possible Hackintosh installation??).

I installed Windows XP first, downloaded all my updates, etc. Then, I installed Ubuntu 9.04 and selected the Ubuntu partition. After installing it, when I reboot the machine, it just boots straight into Windows XP, and it doesn't give me the option to choose which installation I want to use.

I wanted GRUB; I know the installation is there because when I boot with the LiveCD, it shows up.

Thoughts, direction, help? :D

---

### Post by synapsys on 2010-01-11
Ubuntu <9.10
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Ubuntu 9.10
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Go_Big_Blue on 2010-01-11
Thank you for the reply.

Following along on the guide, and I came up on a question.

The guide said to type in 
```
grub> setup hd0
```

But my installation for Windows XP and Ubuntu is on /dev/sdc, so would I then enter the following?
```
grub> setup hd2
```

---

### Post by Miljet on 2010-01-11
I would guess that when you installed Ubuntu, the GRUB was installed to the MBR of sdc, which is the disk that it was installed to. However your BIOS is booting from sda and the MBR there is pointing to the Windows boot loader. Therefore, Grub never gets loaded.

Can you point the BIOS to boot from the third hard disk?

---

### Post by Go_Big_Blue on 2010-01-11
Okay, the whole ```
grub> setup (hd2,0)
``` didn't work.  But putting it to ```
grub> setup (hd0)
``` worked like a charm. Thanks for the help.

BTW Miljet, I did have the 3rd HDD set to boot first in the BIOS. :D

---

