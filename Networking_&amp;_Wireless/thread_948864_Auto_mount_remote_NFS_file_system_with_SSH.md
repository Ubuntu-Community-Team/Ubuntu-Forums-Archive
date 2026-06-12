---
title: "Auto mount remote NFS file system with SSH?"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by myth0s2000 on 2008-10-15
Hello all,

I'm quite new to linux / unix so I need help doing something that I assume is not so hard, or that I could do by myself if I had more experience.

I am trying to "replace" my local home directory by some remote directory on a NFS server that I can access via SSH. I am pretty sure that it's possible.

I tried a lot of stuff. I read the man for mount and sftp. I can connect via sftp and it appears to be mounted automatically when I connect, but I wanted sftp to remember my password. I searched a bit and I found on google that I should be using ssh-agent to create a "pre-autorization" thing on my home directory on the server and in my home directory on my local machine.

I am not sure that I'm going in the good direction here.

If I want to use a folder on a remote file system accessible via SSH, should I be using ssh-agent? If so, I'll try to figure out what it does and how to use it ;)

Thanks,
Alexandre

---

### Post by hamsandwich on 2008-10-15
it's quite easy via the command line:

sudo apt-get install ssh sshfs

sudo sshfs username@ipaddress:/remote/directory /local/directory

---

### Post by myth0s2000 on 2008-10-15
> **hamsandwich said:**
> it's quite easy via the command line:

sudo apt-get install ssh sshfs

sudo sshfs username@ipaddress:/remote/directory /local/directory

Ohhhh, I did something very wrong.

I tried :
sudo sshfs [email]leveille@address.kept.secr[/email]et:/folder/subfolder/myhome ~/ -o nonempty

I guess it an obvious beginner's mistake, but now nothing is working :( I'll try to repair what I broke and get back to you guys after...

---

### Post by ilrudie on 2008-10-15
I think they are talking about key based ssh authentication.  Searching on google or the forums will likely pull up lots of existing post about how to setup ssh with and rsa key instead of a password.  Its not too hard.  Once you have ssh you can tunnel NFS if you want or simply use ssh-fs as the last poster noted.  If you can't find anything I can guide you through it or look for a tutorial later but the info shouldn't be too hard to find at all.

You never want to use a remote file system for a directory that is required.  /home is important under Ubuntu because the only user that does not require /home in order to login is root which can only be accessed via recovery mode.  My advice would be to make a mount point (just an empty directory) in your home folder or /media where you can mount the remote filesystem.  This was you can still login without a network connection if you need to.

Once final word of caution.  When auto mounting remote file systems always make sure there is a soft mount option and use it.  If there is no soft mount option choose a different method or don't auto mount.  This will prevent the auto-mount process from failing if no network connection is available so you can still boot without a network connection or in the event the remote host is unavailable for some other reason.

---

### Post by myth0s2000 on 2008-10-15
Okay, with a simple reset my home directory is back to the default... phew!

ssh-agent is working well. I now have a bookmark under Places that brings me right to my home directory. I think I'll live with that. As long as I can access all my file without having to type my password, I'm happy.

PS : As for changing the home directory of hard vs. soft mount, I don't care much. I'm setting up a virtual machine to access my stuff at the university. If for some reasons I cannot connect, then my Ubuntu machine is useless and may fail, I don't care ;)

But I understand that normally I should not proceed that way!

---

