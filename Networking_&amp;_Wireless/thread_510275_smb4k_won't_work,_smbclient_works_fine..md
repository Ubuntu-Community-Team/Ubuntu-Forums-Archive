---
title: "smb4k won't work, smbclient works fine."
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by provencher on 2007-07-26
smb4k worked for a while, but stopped working.  I was connecting to Windows share without too many problems, the username/passwords were saved in my kdewallet, But then one day it stopped working...   smb4k keeps popping the authentication dialog, which is pre-filled with the correct info anyways. I retype the info to make sure it's correct, but I keep getting the authentication dialog back.  

I know that my setup works, because smbclient connects just fine to the same shares I'm trying to access with smb4k. I test using smbclient from the command line.

Since smbclient is working fine and smb4k isn't, can anyone suggest troubleshooting tips for this problem?  How can I tell where smb4k is choking up trying to authenticate?  My work place uses Active Directory, and again smbclient is dealing with this just fine apparently.

I can provide additional info:

My ip address: 128.144.2.18
The Primary WINS server: 128.144.60.1
Secondary WINS server: 128.144.2.1

The WINS server are all reachable with PING.

The command I use with smbclient is:
```
smbclient -U arc/provencher //JUPITER/Seng
```

I get asked a password, and then it connects, I can use "dir" and "cd" and "get" without problems.

I also tried simply browsing with the file manager, using smb:/, and it works up to the JUPITER server for the example above, but when I try to browse the shares on that server, the authentication dialog pops up again, and I supply arc/provencher for the username, with my password,and it's no go, keeps giving me authentication dialog.
Any help would be greatly appreciated. I'm on the latest Kubuntu version (I think, but how do I tell?)...

The error I get with smbmount is 
```
8537: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
```

Edit: Got smbmount to work by using "-o workgroup=ARC" instead of putting the domain name before my username. Still not able to use smb4k though.
Edit:  Last update, fixed !!!   KDEwallet had way too many entries, deleted a bunch, now works fine.

Thanks

---

### Post by DugieHowsa on 2007-07-27
I have found that smbfs is very buggy.  You may have better luck with cifs.

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

