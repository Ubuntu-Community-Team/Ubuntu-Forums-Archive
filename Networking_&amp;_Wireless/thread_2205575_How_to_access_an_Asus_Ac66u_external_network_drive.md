---
title: "How to access an Asus Ac66u external network drive using Ubuntu"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by cool-vibes on 2014-02-14
I am using Ubuntu 11.04 with my Asus-ac66u i have an external hard drive pluged into the usb on it. The external harddrive will show up on Ubuntu in Browse Network> Windows Network>Workgroup and i am able to access the content of the drive. I would like to be able to download content to the hard drive but i am not able to find where the drive is mounted in Ubuntu. Could somone give me info on how to make a mount point in a Ubuntu folder.

---

### Post by varunendra on 2014-02-16
> **cool-vibes said:**
> ..but i am not able to find where the drive is mounted in Ubuntu..

Usually in /media/<mount-point>/

The "mount" command (without parameters) shows all currently mounted devices with their mount-points.

If you want permanent mount-point mounting the drive automatically, you must add a relevant entry in /etc/fstab file. Take a look at : [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Windows network means it is a samba share.

For advance permissions regarding mount points (although you don't seem to need it) : [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

