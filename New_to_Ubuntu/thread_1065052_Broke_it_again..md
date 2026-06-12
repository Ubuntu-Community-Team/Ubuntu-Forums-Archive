---
title: "Broke it again."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by gandalf2000 on 2009-02-09
I had Windoz and Ubuntu running on a dual boot, windows on the original hard drive and Ubuntu on a partition on the second drive.  So, I finally decided to upgrade my optical drive but when I went to fit it the ribbon was just a little too short.  I moved the connection for the second drive further down the ribbon thinking everything should be the same.

However, when I booted up I got a grub 25 error.  Using SuperGrubDisc, I finally got Windoz back and it would reliably boot Windoz.  But after I did a reinstall for Ubuntu it was back to a grub error.  I have since tried installing SUSE, Fedora and Mandriva, all with the same effect.  I installed GAG bootloader and can get Windoz but nothing else.  Please help me for I know not what I have done and swear I shall repent for my sins.

I should add that the other disc is recognized by Windoz and a live disc OS.

---

### Post by Person98 on 2009-02-09
the two connections on the ribbon cable are different, one is for the master drive and one is the slave, in order for grub to boot off of that hard drive it must be the master, have you tried switching the cable back to see if it will work again that way? i am assuming your other hard drive is on another cable so that would be why windows is still working as normal, hope it helps

---

### Post by gandalf2000 on 2009-02-10
I did switch the ends of the cable back last night after reading your reply but it didn't help.  So one end is marked "CPU board" and the other is marked "Master".  Master is hooked to the new optical drive as it was to the old drive and the connection that I moved down the cable is back on the second hard drive as it was before.  Except for moving the connection down the cable everything is back where it started from.  The only difference is that the old optical drive was IDE and I had to use an adapter to hook up the new SATA drive.  Both drives can be read and used, just can't boot the second hard drive.

---

### Post by wolfen69 on 2009-02-10
Grub error 25:
> Disk read error This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

it could be a bad IDE cable also. try a different one.

---

