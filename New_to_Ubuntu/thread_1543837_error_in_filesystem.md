---
title: "error in filesystem?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by broshe on 2010-08-01
Hello,
After a friend told me about some problems he had with his ubuntu, I looked at my /etc/fstab file. Here is what I found there:
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda7       /home           ext4    defaults        0       2
/dev/sda8       /home/myfiles   ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0

I noted that there are apparent errors in the /dev/sda5 partition (mount-point /).
Are these errors ?

In order to check, I booted the computer with an ubuntu live-CD and used:
a) sudo fsck /dev/sda5
b) used the Disk Utility from ubuntu system administration menu.

from both I did not get error messages.
I also performed a forced file system check on boot by:
sudo touch /forcefsck
and rebooting.

The error indication in the /etc/fstab file remains.

My questions are:
Does the content of my fstab indicate problems with the file system?
If yes, I will be grateful if someone can give me a recipe for dealing with these problems.

I am using ubuntu 10.04 amd64 on a dell vostro 1310 laptop.

Thanks,
Eli

---

### Post by oldos2er on 2010-08-01
"/dev/sda5 / ext4 errors=remount-ro 0 1"

 errors=remount-ro tells the system to mount /dev/sda5 in read-only (ro) mode if it encounters errors in the file system when it is first mounted when the system is booting; it doesn't mean there *are* errors. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

### Post by broshe on 2010-08-02
Thank you very much Ann

Eli

---

