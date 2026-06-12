---
title: "error: no such partition. grub rescue&gt;"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by captgadget on 2010-11-06
OK, I wanted to remove lucid on my dual boot windoseXP. I used my computer>manage>disk manager>removed the linux partions. Then I booted to the XP disc,selected repair. Don't quite remember what happened after that because when the computer rebooted I got this error message. Now, I can not reboot from any cd/dvd even though in my BIOS I have boot from CD selected first.

Appreciate any help I might get.

thanks

---

### Post by captgadget on 2010-11-08
finally got it used this website: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by clulelessness on 2010-11-16
> **captgadget said:**
> finally got it used this website: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
 
Hey, could you give a quick walkthrough of how you did it?
I have the same problem but don't know what to do/how to use testdisk

---

### Post by drs305 on 2010-11-16
> **clulelessness said:**
> Hey, could you give a quick walkthrough of how you did it?
I have the same problem but don't know what to do/how to use testdisk

If you have deleted Ubuntu and can't boot Windows, but still have the LiveCD:

Boot to the desktop and install *lilo*. Then run the second command:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This assumes Windows is on the sda drive and it's files haven't been corrupted.

As you install lilo it will issue several warnings; don't worry about them as you aren't fully installing lilo - you are just using it to write to the mbr.

---

