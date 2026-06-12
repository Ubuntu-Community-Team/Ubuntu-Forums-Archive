---
title: "Windows Networking - Use cifs, not smbfs"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by DugieHowsa on 2007-06-26
Hey all.  I just wanted to do a quick post in the hopes to that others can avoid the pain I have gone through this last week.

I had been having trouble mounting a Windows Share.  I tried to mount using smbfs.  I tried to mount using cifs.  In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary:  "smbfs is unmaintained and known to be severely broken."  That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary:  USE CIFS.  DO NOT USE SMBFS.

---

