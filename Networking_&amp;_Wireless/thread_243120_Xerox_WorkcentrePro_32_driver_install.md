---
title: "Xerox WorkcentrePro 32 driver install"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by eg-maverick on 2006-08-24
I am trying to install a driver for our office printer but can't seem to get off of square one. I download the correct driver from Xerox. the Readme in the tar file says "run setup within the install directory as root to install the driver". This is what I try and this is what I get:

user@ubuntu:/tmp/Linuxi386XpxxInstall$ sudo ./setup
Password:
...............ERROR: No such file or directory
user@ubuntu:/tmp/Linuxi386XpxxInstall$

it seems like the setup file is there (doing an ls):
user@ubuntu:/tmp/Linuxi386XpxxInstall$ ls
disks         isize       pkg_tar.z2  pkg_tar.z4  pkg_tar.z6  pkg_tar.z8  setup
installf.rom  pkg_tar.z1  pkg_tar.z3  pkg_tar.z5  pkg_tar.z7  readme      tsize

Any thoughts?
Thanks,
Craig

---

### Post by eg-maverick on 2006-09-27
I figured out that the script was looking for gzip in /usr/bin instead of /usr. Once I fixed that it worked fine. Just FYI for anyone heading down the same path.

---

### Post by hellomatts on 2007-02-09
Hey eg, 

I was so happy to find your thread, cause that's my exact problem! ... But I'm a complete newbie, and can't find gzip in either one of those directories!! Can you let me know EXACTLY how I can go about changing the path of the gzip or whatever I need to do to resolve this?

Thanks a million!
-matt

---

### Post by hellomatts on 2007-02-09
Ok, I seem to have gotten a little bit further now... 

now half way through the install, I get the following message: lpstat: No destinations added.

Can ANYONE please help me resolve this?

---

