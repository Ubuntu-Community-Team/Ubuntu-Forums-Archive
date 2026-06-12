---
title: "Ubuntu 10.10 netbook edition"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Anonymous48 on 2010-10-24
How do I install Ubuntu 10.10 netbook edition on my netbook using Wubi?
I really want Ubuntu netbook edition, however I do not want to risk partitioning my drive by dual booting.
Please help.

---

### Post by bcbc on 2010-10-24
[http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)
Use wubi.exe from there (or another mirror). Last I heard the wubi.exe on ubuntu.com was at 10.04.1 release (which doesn't work with netbook edition as there is no 10.04.1 netbook release).

The 10.10 wubi.exe will download the netbook edition of ubuntu itself. Or if you want to speed things up (especially if you need to reinstall or create a live USB for rescue situations) then download the .iso yourself using bittorrent, place it in the same folder as wubi.exe, and run wubi.exe (and it uses the downloaded .iso).

---

### Post by Anonymous48 on 2010-10-24
Thanks. I will try that.
I was also wondering, when using Wubi, can you still download stuff for Ubuntu? for example, applications and Ubuntu updates?

---

### Post by bcbc on 2010-10-24
> **Anonymous48 said:**
> Thanks. I will try that.
I was also wondering, when using Wubi, can you still download stuff for Ubuntu? for example, applications and Ubuntu updates?

Yes. It's basically Ubuntu with a different interface. You can select the standard gnome-desktop from the signon screen.

EDIT: sorry I thought you meant Netbook-edition, not wubi.
Yes wubi ubuntu is identical to ubuntu except it uses a virtual disk. The updates of packages grub-pc and grub-common have been causing the most problems with wubi installs lately. But I would still install updates - just take a few precautions e.g. backup the c:\wubildr and the c:\ubuntu\disks\root.disk file prior to a big update.

If you like Ubuntu then you can consider migrating to a direct install later.

---

