---
title: "File Operation not supported on Windows drives"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by flylehe on 2009-11-29
Hi,

My Windows drives are automatically mounted in Ubuntu. File operations on Windows drives had been going well until today when my operation of creating a directory on a Windows drive is denied:
> 
$ mkdir /windows-d/tmp
mkdir: cannot create directory `/windows-d/tmp': Operation not supported


Some permission info is:
> 
$ ls -l / | grep "windows-d"
drwxrwx---   1 root plugdev 229376 2009-11-28 20:28 windows-d


I wonder what's wrong with it?

Thanks and regards!

---

### Post by SunnyRabbiera on 2009-11-29
Install NTFS config, it works for me on my dual boots

---

### Post by flylehe on 2009-11-29
Thank you!
I have enabled write support for internal device as well as for external device via ntfs-config. But my problem still remains.

---

### Post by flylehe on 2009-11-29
How can I unmount and mount Windows drives? I want to see if that could solve my problem.

---

### Post by teward on 2009-11-29
gparted can unmount the drives.  Not sure of your version of Ubuntu, but on Jaunty (9.04) you can just click the little eject button if you show the places sidebar and go to computer in the places menu, and when the drive is mounted.  To remount, after unmounted, just click the drive in the places sidebar, and then you might need to enter the admin password to allow the drive to mount, but then it will mount and you can view the drive(s).

---

### Post by flylehe on 2009-11-29
Thanks, TrekCaptainUSA!
I just unmounted it by gparted, and then tried to mount it again with command 
```

mount /dev/sda5 /windows-d/

```
At first it was mounted but only readable, because I don't know how to make it writeable when calling mount. So I enabled write support for internal device as well as for external device via ntfs-config. Still my problem of mkdir not being supported remains.

---

### Post by flylehe on 2009-11-29
Some update:
Just reboot my ubuntu, but the problem of not supported operation still exists.

---

### Post by teward on 2009-11-29
Does your user account itself have the privelages to write to the other drive(s)?  I know this was a problem with someone I worked with, and I had to fix the user settings to allow it.

---

### Post by SunnyRabbiera on 2009-11-29
you may also want to try to install pysdm, it helps with permissions sometimes.
NTFS can be rough to work with though, but thats microsoft for you.

---

