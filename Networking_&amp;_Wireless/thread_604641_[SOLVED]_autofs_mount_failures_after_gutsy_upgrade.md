---
title: "[SOLVED] autofs mount failures after gutsy upgrade"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by bdk6m2007 on 2007-11-06
I had NIS and autofs working quite nicely on several fiesty boxes.  After upgrading to gutsy I can login as an NIS user successfully, however, it can't find the home directories.  I get the old "Could not chdir to home directory /x/myuser: No such file or directory" message and it drops me into /.

I have verified that both nis and autofs are running.

Poking around the logfiles, I see many entries identical to the following in daemon.log:

```
Nov  6 10:09:47 bk-silver automount[17059]: >> mount: wrong fs type, bad option, bad superblock on server0:/homeXYZ/myuser,
Nov  6 10:09:47 bk-silver automount[17059]: >>        missing codepage or helper program, or other error
Nov  6 10:09:47 bk-silver automount[17059]: >>        In some cases useful info is found in syslog - try
Nov  6 10:09:47 bk-silver automount[17059]: >>        dmesg | tail  or so
Nov  6 10:09:47 bk-silver automount[17059]: mount(nfs): nfs: mount failure server0:/homeXYZ/myuser on /x/myuser
Nov  6 10:09:47 bk-silver automount[17059]: failed to mount /x/myuser
```Per the suggestion I looked at dmesg but there was nothing out of the ordinary there.  None of my nis/autofs config has changed since feisty and I can't figure out what changed or is missing from gutsy. I still have several feisty boxes running just fine with this configuration so I'm pretty stumped.  My googling on the subject has been unproductive.  Any ideas??

---

### Post by bdk6m2007 on 2007-11-06
OK I solved the issue.  After playing around with it for a while I noticed that autofs recommends installation of nfs-common.  With nothing else to go on but a hunch I decided to try it.

```
sudo apt-get install nfs-common
```

Now all is working fine.  Not sure how/why this changed.  nfs-common is not installed on my old feisty boxes, but installing it under gutsy solved my problem.

If anyone has any insight into what changed I would appreciate knowing!

---

### Post by Michael Macalik on 2007-11-08
I experienced the same problem, but with a twist.
The order that the packages are installed might be important.
to get my clients working I performed the following steps:

```

aptitude reinstall nfs-common
aptitude reinstall autofs
```

After that /etc/init.d/autofs restart ran without errors

---

