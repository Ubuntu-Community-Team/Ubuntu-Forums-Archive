---
title: "Networking via Command Line"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Mr Wrath on 2007-02-23
I have been doing so much through via the command line and have become very comfortable with using it on a regular basis.  I have been looking around, but I can not seem to find how one would move files from one computer to the other over a network.

My network consists of a Debian Fileserver and 2 Ubuntu back-up servers.  How would I move files from one computer (Debian) to the other (Ubuntu) [and vice versa] via the command line, using TCP/IP static addresses.  I have been using Ubuntu's GUI to pull files from my Debian server.  I would like to advance my command line skills by adding this to my list of command line abilities.

Later, I will use this information to create a script to have the fileserver do automatic back-ups.  Please, I am open to all forms of being capable of connecting to my servers by command line.  Any help will be greatly appreciated.

Lord Wrath

---

### Post by koenn on 2007-02-23
scp
uses ssh to copy between machines, usualy in the form scp /path/file server:/path/file.
man scp or [http://www-hep2.fzu.cz/computing/adm/scp.html](http://www-hep2.fzu.cz/computing/adm/scp.html)

rsync
seeing you're interested in backup to a remote location, you should check out rsync. It doesn't just copy, it synchronises.
[http://www.hmug.org/man/1/rsync.php](http://www.hmug.org/man/1/rsync.php)
this is a mac man page but rsync also exists for ubuntu, ant it works the same.

---

### Post by incubus on 2007-02-23
I use scp all the time and it gets the job done.

I would also recommend using sshfs, which allows you to "mount" the remote directory through ssh.  It's not perfect yet (it doesn't follow soft links), but it can increase productivity a lot.

Just remember to
```

$ sudo adduser <username> fuse

```

in order to get your user to mount directories without using sudo.

incubus

---

### Post by netztier on 2007-02-24
> **incubus said:**
> I use scp all the time and it gets the job done.


SCP for "single" things or scripted file transfers, by all means, yes! Occasionally SFTP has also it's right to be, especially if you need to browse the remote computer's directories to locate a particular file.

*To the OP:*

To keep directories synchronised, also take a look at **unison** from the universe repositories. I use it to keep copies of my file server's data directories on other systems. Unison can work via SSH, and so it turns out yet again that having a working SSH connection between two systems will allow for an immense number of things that can be done between these two. 

Unison can also make use other ways of making a remote file system visible to the local system, including Unix' native **NFS** and the Windows compatible **Samba** (SMB protocol) which will let you share files between systems. To use these, all involved computers are best located within the same administrative domain, and manageability will profit a lot from having a common user database (LDAP, NIS, Windows AD...).

Of course, once there is an NFS or Samba mount, you can configure your scripts and tar jobs etc directly as if on the local file system...

best regards

Marc

---

### Post by Mr Wrath on 2007-02-26
Thank you very much for the input.  I have started looking at all of these and they are what I was looking for.  Thanks again everyone.

---

