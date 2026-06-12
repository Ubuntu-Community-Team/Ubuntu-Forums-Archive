---
title: "GRUB Error 21,   100% Ubuntu,   cant boot"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Ronok on 2009-01-25
hi 
I am new,
my computer is **100% ubuntu,** 
new, fast, has been great with ubuntu for 2 months

here is where by trouble is:

now I cant boot / start computer !! 

1) push power, ok
2) american megatrends...
2a)(pressing .del go to bios, no help)
2b)(pressing F8 go to boot menue, no help)

3) **GRUB Error 21** -----> dead end

4) boot from live CD (it is v. 8.04)
5) chose: "let me try ubuntu dont change the computer"

thats how I got here...
I looked at other threads, google, about fix grub error 21 
but could not find any of:

-grub menu, or  "/boot/grub/..."

also my system is now Ubuntu 8.10, dont want to have to re-install
backwards to 8.04 would that even work, to fix it ?
what should I do considering my predicament ?
**Thanks **

here is some partial info ?

/dev/sdb1 on /media/ShuJu type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
ubuntu@ubuntu:~$ ls -l /media
total 8
drwxr-xr-x 21 root root 4096 2009-01-04 11:24 disk
drwx------  6 1000 1000 4096 2009-01-17 00:25 ShuJu

---

### Post by diablo75 on 2009-01-25
Check these steps out.  You'll probably be able to repair your grub with this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Even though you didn't just install Windows, it should still do the trick.

---

### Post by Ronok on 2009-01-25
Thanks !
that was a good fix, steps #1-5 fixed it for me

---

### Post by diablo75 on 2009-01-25
Sweet!  Glad I could help!

---

