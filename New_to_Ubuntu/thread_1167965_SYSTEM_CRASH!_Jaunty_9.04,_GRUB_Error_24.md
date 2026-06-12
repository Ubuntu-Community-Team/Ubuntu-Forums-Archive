---
title: "SYSTEM CRASH! Jaunty 9.04, GRUB Error 24"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by LyonTamer on 2009-05-23
HELP! My system froze during use (posting a blog entry on MySpace). No warnings, no sound, nothing, jsut suddenly froze in place. The only way to unfreeze was by unplugging and turning back on. I then got this error message:

Fixed optical drive not found.
GRUB loading stage 1.5.

GRUB loading, please wait...
Error 24

The optical drive being the DVD rom. I unplugged again and restarted with my 7.10 disk in the drive, booted in safe graphics mode, and that is what I'm running on now. I had tried restarting after loading the disk but doing so just produced a blank, black screen. Had to unplug again and reboot from the disk in order to use the system and get on here and ask the question. :)

I am on the new Jaunty Jackalope 9.04, upgraded, on a Dell Inspiron 8000. I could reinstall from the 7.10 disk and go through all the upgrades again but I really, really don't want to. It took seven hours the last time. Haven't gotten the Jaunty disk in the mail yet.

Any idea what Error 24 is or how to fix it? Thanks in advance. :)

---

### Post by LyonTamer on 2009-05-23
I found this terminal code to try, in another thread. It gave this...

ubuntu@ubuntu:~$ e2fsck -c -c  /dev/hda1
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: No such file or directory while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

What does this mean? Do I need to reinstall? I don't have any files saved on the hard drive, but all those upgrades will take all day. ](*,) It wouldn't be an issue if I wasn't busy.

---

### Post by taurus on 2009-05-23
Maybe try the /dev/sda1 instead of /dev/hda1.

```
e2fsck -c -c **/dev/sda1**
```
```
sudo fdisk -l
```

---

