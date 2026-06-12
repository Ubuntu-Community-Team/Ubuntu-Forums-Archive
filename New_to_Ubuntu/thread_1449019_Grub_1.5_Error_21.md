---
title: "Grub 1.5 Error 21"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by ytecle on 2010-04-07
I'm getting a Grub 1.5 Error 21 after installing Ubuntu on an external hard drive. This problem occurs when I reboot my XP machine without the external hard drive plugged in, if I plugged in the external hard drive where I installed Ubuntu then I am ok I can choose Ubuntu or XP. 
   
  I tried the boot.ini by changing the 2 to 1, that does not help.
any help would be appreciated!

---

### Post by undecim on 2010-04-07
That means that you installed Grub to your internal drive rather than your external.

If you want to fix it, you should first put grub on the external drive, then put Windows' bootloader back on the internal drive.

To do this, boot Ubuntu and open a terminal type "mount" and the first line of output should look something like this:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
```

the /dev/sda1 in that example means that Ubuntu is on the first harddrive (sda) and on the first partition (1). Yours may say "/dev/sdb1" instead, since you are on the external drive.

Now, type "sudo grub-install /dev/sda" where /dev/sda is the hard drive that you need to put grub on. In my example, I would need to use /dev/sda (not /dev/sda1. that's the partition, not the drive), because that's the hard drive with my Ubuntu installation. If you saw "/dev/sdb1 on /" in after typing "mount", then you will need to use "/dev/sdb" instead. This command will require your password. Note that when you are typing, you don't see any characters appearing, but your password is indeed being typed.

Once that's done, you can restore the Windows bootloader with a Windows recovery disk. Have a look her for instructions: [http://www.techzonez.com/forums/archive/index.php/t-3975.html](http://www.techzonez.com/forums/archive/index.php/t-3975.html)

---

### Post by ytecle on 2010-04-07
Hello [undecim]("http://ubuntuforums.org/member.php?u=623644"),
Thank you so very much, your instruction worked for me perfectly! now I have windows and ubuntu get to start as I wish!

Again, Thank You!

---

