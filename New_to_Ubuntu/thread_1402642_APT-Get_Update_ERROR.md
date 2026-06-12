---
title: "APT-Get Update ERROR"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Cuzimbrownhuh on 2010-02-09
Hello everyone,

I'm very new to this forum so please excuse me.  I have recently upgraded from 8.04 to 8.10.  After installation my linux froze and now although I can sign in and nothing can be seen at my  home screen at all except wall paper and mouse.  I have gone to terminal to fix this by typing apt-get update and I keep getting this error.

[B]W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W:Failed to fetch [http://us.archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.canonical.com'

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have benn ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems
[/B]

PLEASE IF THERE IS ANYONE THAT KNOWS HOW TO FIX THIS I WOULD TRULY APPRECIATE IT!

---

### Post by Cuzimbrownhuh on 2010-02-10
**APT-Get Update ERROR**             
                                                                Hello everyone,

I'm very new to this forum so please excuse me. I have recently upgraded from 8.04 to 8.10. After installation my linux froze and now although I can sign in and nothing can be seen at my home screen at all except wall paper and mouse. I have gone to terminal to fix this by typing apt-get update and I keep getting this error.

[B]W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...id/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg")  Could not resolve 'us.archive.ubuntu.com'

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg")  Could not resolve 'us.archive.ubuntu.com'

W:Failed to fetch [http://us.archive.canonical.com/ubun...id/Release.gpg]("http://us.archive.canonical.com/ubuntu/dists/intrepid/Release.gpg")  Could not resolve 'us.archive.canonical.com'

W:Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg]("http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg")  Could not resolve 'security.ubuntu.com'

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg")  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have benn ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems
[/B]

PLEASE IF THERE IS ANYONE THAT KNOWS HOW TO FIX THIS I WOULD TRULY APPRECIATE IT!

---

### Post by cariboo on 2010-02-10
Please don't create multiple post on the same subject, I have merged your two threads.

That being said, your problem may be caused by corrupted files, when your system locked up. Boot from the Live CD and once at the desktop, go to Applications->Accessories->Terminal and type:

```
sudo fsck -a /dev/sda1
```

Substitute your Ubuntu partition location for the one in the example above. The above command will check and repair corrupted files on the hard drive. Once the process has finished, reboot and you should get back to a working desktop.

---

### Post by nhasian on 2010-02-10
you can choose a different server to download from in System->Administration->Software Sources.

by any chance are you in India?  I read a post yesterday by someone else with the same problem and they were in India.

---

### Post by Cuzimbrownhuh on 2010-02-13
Hey Thank you for helping me out.  Sorry about the threads I couldn't find the old post so I just created a new one.  Once again, still a newbie...   So, I tried the Sudo fsck -a /dev/sdal command and I get this new error message :   

ubuntu@ubuntu:~$ sudo fsck -a /dev/sdal
fsck from util-linux-ng 2.16
fsck.ext2: No such file or directory while trying to open /dev/sdal
/dev/sdal: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

How do I find the partition location on terminal?

---

### Post by Cuzimbrownhuh on 2010-02-13
Hey nhasian, not from india.  Here in Disney town Orlando, Fl.  Hadn't had trouble with 8.04, now upgraded to 8.10 and nothing but trouble... Configure..

---

### Post by paul_in_london on 2010-02-13
Are you sure you have networking? Can you post the output of:

```
sudo /etc/init.d/networking restart
```

---

### Post by Miljet on 2010-02-13
> ubuntu@ubuntu:~$ sudo fsck -a /dev/sdal
That command was supposed to be  sudo fsck -a /dev/sda1. That is a 1 (one) on the end, not l (el). But you need to substitute the actual partition where your Ubuntu resides, such as sda3 or sda5 or whatever. If you do not know which partition Ubuntu is on, try this:

Open a terminal and enter ```
 sudo fdisk -l 
``` and post the output here. And that is an l (el) on the end.

---

