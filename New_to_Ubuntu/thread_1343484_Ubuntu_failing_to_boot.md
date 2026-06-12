---
title: "Ubuntu failing to boot"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Pwhdavey on 2009-12-01
Ubuntu (from Windows Installer) has been on my computer for about 2 weeks and in that time I have used it. Before I explain the problem I usually shut down my computer (whether on Windows or Ubuntu) by holding down the power button manually. However I won't be from now on because it seems to have stuffed both my operating systems. When I start Ubuntu the white logo on a black background comes up and says"

> One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/: waiting for (null)
Press ESC to enter a recovery shell

Whenever I press ESC it says:

> General error mounting filesystems
CTRL-D will terminate this shell and retry.
root@ubuntu:~#

And when I press CTRL-D it brings me back to the first part saying to press ESC. It says 'waiting' but I have waited for long and it shows no activity signs of progress. I am using the latest version of Ubuntu, 9.10. Please see if you know what's going on.

---

### Post by sandyd on 2009-12-01
once you get to the promt (root@ubuntu:~# 			 		)
type in 
```

fsck -y

```it is a current bug being debated on.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/58430](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/58430)

---

### Post by Pwhdavey on 2009-12-03
Thanks anyway but it did not work. Entering the command got me the same response going back to the CTRL D thing. Should I reinstall it and if so, how?

---

### Post by ukripper on 2009-12-03
When you reboot if you are on ubuntu 9.10 just hold shift until you see grub menu and select second option which is recovery. Once booted into recovery mode select fsck there.

---

