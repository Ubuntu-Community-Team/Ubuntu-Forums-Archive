---
title: "Hard drive issues"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by K-D on 2009-02-27
Hi everyone,

I recently installed Ubuntu 8.04 and after two months of bliss everything went wrong.

Whether it was Ubuntun or my computer had just had enough im not sure....

I managed to salvage my two internal hard drives from inside my machine, with the plan of buying a caddy and seeing if I can access the info from my XP machine.

The problem is the my laptop doesn't pick up the drives unless you go via control panel to format the drive.

I was wondering is this due to XP not recognising Ubuntu and would it be worthwhile trying a live cd and the caddy to see if it works.

I would obviously try it but my netbook has no cd drive.

Just wondered if anyone had any suggestions

Cheers:guitar:

---

### Post by tonyh6243 on 2009-02-27
If your laptop supports booting from a usb drive, then boot from one that you have put the OS on.

---

### Post by taurus on 2009-02-27
Are those drives using ext3 filesystem?  If you want to access ext3 in windows, you need the fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Install it and see if you can access your external drives from windows without formatting them first.

---

### Post by whoop on 2009-02-27
your XP will not recognize the file system by default. Could you post what problems you where experiencing with the drives as I can not determine what problems you are having from your post.

---

### Post by K-D on 2009-02-27
i'll give it a blast!

Cheers

---

### Post by K-D on 2009-02-28
ok I have installed the ext3 driver and the drive now appears however it appears it is only the very small windows partition that appears and it shows the size as 2.38gb when it should be 200gb?

Any other ideas would be greatly appreciated!

:confused:

---

### Post by K-D on 2009-02-28
it states in the device management as a healthy 183gb partition....

looks like I cannot read the ubuntu file system

---

### Post by mips on 2009-02-28
First try and access the drives via a Linux OS of some sort, a livecd should also work.

Last case resort, only if your data is lost:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

