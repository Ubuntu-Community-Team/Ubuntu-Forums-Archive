---
title: "Simple Backup over SSH"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by ZootHornRollo on 2009-05-22
Hi,

I am trying to get Simple Backup running.

I have two PC's running Ubuntu.  My main PC is running 9.04 and my audio server 8.04.

I have Simple Backup installed on both.  I have it backing up my Music folder on the Audio server onto the second hard disk on the same machine.  

I would also like to back up the Pictures folder from my main pc onto the second hard drive on the audio pc.

Using Simple Backup i have entered the address as 'ssh://graham@192.168.0.3/media/disk/Photo Backup'* (i have also tried 'sftp://graham@192.168.0.3/media/disk/Photo Backup'*) which comes up with a tick after clicking test.  But when i click 'backup now' there is some HD activity on my main pc but the back up file never appears in the destination file of the audio pc.

*i have also tried adding my password in after the username

any ideas what i'm doing wrong?

---

### Post by supersonicdarky on 2009-05-22
It would probably be easier if you mounted the other pc's drive on an nfs mount.

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

While you _can_ mount ssh, I would advise against it.

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by Mornedhel on 2009-05-22
You can also run rsync over ssh with the -rsh=ssh option.

---

