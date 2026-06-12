---
title: "Mount permissions"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by briangd on 2010-03-18
Hi folks, done a bit of searching but haven't found this specific issue.
 
I'm using VirtualBox on an OSX host.  This is my first installation. I'm running latest versions of VB and Ubuntu desktop. All the VB extensions have been installed.
 
I'm trying to install a shared folder, i.e. resides on the host but is visible on the client.
 
Created share on VirtualBox called SharedDocs
Mounted on client
 
  sudo mount -t vboxsf SharedDocs /home/brian/Share
 
Share changes ownership from brian to root, so
 
  sudo chown -R brian:brian /home/brian/Share
 
But this does nothing, ownership stays with root. No error message. Tried with and without the  -R option.
 
Am I missing some step or config detail here?  I think I should be able to do this without going near fstab?
 
Any insights appreciated.

---

### Post by quixote on 2010-03-19
Ah yes.  The brilliant default that mounts a *shared* drive so that nobody can use it.  Sometimes I have to wonder what the devs are smoking.

Anyway, after gnashing my teeth way too much, I found the fix.  You have to specify permission during mounting: ```
sudo mount -t vboxsf **-o uid=1000,gid=1000** SharedDocs /home/brian/Share
```-o means options follow.  user IDs and group IDs of a 1000 and up refer to ordinary users.

If you use fstab on your vm to mount the share, you can put uid=1000,gid=1000 in the same section with the other options.

---

### Post by briangd on 2010-03-20
Interesting, thanks.

I did manage to solve it by making an entry in fstab and setting the user there. That was after crashing OSX and corrupting the client.  Think VB has a few issues.

---

### Post by quixote on 2010-03-20
> a few issues
:snort:

---

