---
title: "Can't mount samba share"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Notclive on 2007-07-15
I'm trying to mount a samba share from another pc in my network and it works perfectly from the command line but doesn't work on bootup. My /etc/fstab line is 
//192.168.2.2/Share     /mnt           smbfs           password=        0  0
When I try accessing /mnt from nautilus it crashes and I can't do ls /mnt that gives an error.
If I do "sudo mount -a" It works and I get "Anonymous login successful" (I have to umount /mnt first)

---

### Post by DugieHowsa on 2007-07-16
Try using cifs instead of smbfs.  smbfs can be buggy.  Try checking out this link below and see if that helps:

[http://ubuntuforums.org/showthread.php?t=485443](http://ubuntuforums.org/showthread.php?t=485443)

---

