---
title: "Samba suddenly stop? Check here"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by chronusdark on 2007-07-25
i had a problem where nautilus suddenly stopped letting me browse samba shares.  It seemed to have happened for no reason. I could still browse if i had the IP, the solution was i had changed my DNS to point to the OpenDNS servers. So i switched back, after switching back to my ISP DNS it worked fine.

hope this helps lots of people

---

### Post by DugieHowsa on 2007-07-27
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

### Post by dmizer on 2007-07-28
to fix this problem resolve wins before dns by doing the following:

```
sudo gedit /etc/nsswitch.conf
```
change this line 
```
hosts:          files dns mdns [COLOR="Red"]wins[/COLOR]
```
so that wins appears before dns like so:
```
hosts:          files [COLOR="Red"]wins[/COLOR] dns mdns
```

this will allow you to continue to use opendns servers, but still allow you to browse your local network.

---

### Post by borisattva on 2007-12-01
hi dmizer

i have the same issue as reported above, but my nsswitch looks like this:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

wins is not present at all, i tried it with wins right infront of dns to no avail but i dont feel comfortable removing/altering other instances. can you advise?

---

