---
title: "Need to make shortcut to second drive in Ubuntu"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by jacook5 on 2010-06-17
I'm building a media PC for my TV and I'm really excited to us Ubuntu. The problem I'm having is that I have installed a second 1TB hard drive for media storage. I want to create a link to the desktop, but Ubuntu will not let me.

---

### Post by oldfred on 2010-06-17
While the link below is about multibooting, it is about sharing data with multiple installs from a data partition using linking.

You need to create a mount point, add the data partition to fstab and mount it. You could directly mount it or use linking.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by jacook5 on 2010-06-17
Thank you for quick reply, I'll try to work on this tonight. I'm still learning the Ubuntu terminal, but I'm eager to learn more.

---

