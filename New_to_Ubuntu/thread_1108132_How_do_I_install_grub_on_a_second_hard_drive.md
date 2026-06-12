---
title: "How do I install grub on a second hard drive?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by bwallum on 2009-03-27
I have three hard drives, hd0, hd1 and hd2. I want to remove hd0 but it has grub installed. At the moment it loads a kernel stored on hd2.

I can point the bios to use any one of the harddrives for the boot harddrive. If I point it to hd2 (as I would like as the boot up drive) I just get a flashing cursor. I guess this is because there is no bootloader on hd2.

How can I install grub on hd2?

---

### Post by James_Lochhead on 2009-03-27
Look at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Rather than installing grub on (hd0,0) install it on (hd1,0)

Edit: Had a brain fart. Corrected the disk/partition numbers.

---

### Post by bwallum on 2009-03-27
> **James_Lochhead said:**
> Look at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")


Hole in one! Thanks.

Firstly I ordered the disks in my bios to suit the layout that I wanted.I then rebooted with a live CD. hd2 was designated as the boot up drive in my original question. This meant that Ubuntu now saw that drive as (hd0). I found it got a bit confusing but fortunately all three drives are different manufacture so I could check how the system saw them with```
sudo lshw -class disk
```

Once I found (and was sure of) the drive I then did```
sudo grub
```then```
grub> find /root/grub/stage1
```to confirm the kernel was there, and then```
grub> root (hd0,0)
```followed by```
grub> setup (hd0)
```I got a successful report and closed down the terminal. Bingo! Booting on the correct drive (formally hd2 and now (hd0)). I can now remove the hard drive that originally contained the boot loader grub.

---

### Post by mlentink on 2009-03-27
Opinion:

GRUB is one of the most undervalued pieces of system software around

---

