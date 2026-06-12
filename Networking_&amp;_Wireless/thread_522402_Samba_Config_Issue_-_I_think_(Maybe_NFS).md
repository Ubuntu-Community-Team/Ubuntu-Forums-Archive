---
title: "Samba Config Issue - I think (Maybe NFS):"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2007-08-10
All,

noob here on Ubuntu.  I installed Samba on my machine.  I can click "Places" + "Network".

I see the windows shares and click, which opens with domain, which I click and shows all the windows shares,
but when I try to open a share, get an "Authentication Required" dialog to enter UID, Domain and PWD to access
the win share, and reqardless of the combo given, that blows.

What is needed to fix this problem?

Thanks!

OMR

---

### Post by OldManRiver on 2007-08-10
All,

Had a guy at IRC help me and we found that smbfs was not installed.  Now U box sees wind just fine and even have fstab mounts.  One errors but that is minor, can fix later.

Right now need to get Win to see U box shares.  Not working!  Need help and any suggestions.

Thanks!

OMR

---

### Post by DugieHowsa on 2007-08-15
--------------------------------------------------------------------------------

I have found that smbfs is very buggy. You may have better luck with cifs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

