---
title: "Synchronize website and local folders"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by kseise on 2007-06-07
I am looking to backup my website onto my desktop.  I want to be able to edit the files locally and have the changes uploaded to my hosted site.  Can someone recommend a good solution?  I have Unison installed and that works well over ssh connections, but my host doesn't seem to allow ssh connections.

---

### Post by kevdog on 2007-06-07
I was going to recommend unison also but see your dilemma. Im not sure what to tell you.  I guess any rsync based tool would be out of the question.

---

### Post by Mr. C. on 2007-06-08
Don't keep us guessing - what does your provider allow ?

What do you mean "your host" doesn't allow SSH connections?  Is that the web provider's system ?

MrC

---

### Post by kseise on 2007-06-08
Sorry, that's a good point.  My site is hosted on Netfirms.  Although they do allow me so ssh into the server (just found that out), when I attempt to have Unison connect, it just sits there and does nothing.  I waited about 15 minutes and nothing happened.  I know that unison would normally take a while to check for versions between changed items, but this happens before I even get to that point.

---

### Post by Mr. C. on 2007-06-08
Have you been successful with a command line SSH connection yet, as in :

```
ssh yourhost.com
```

MrC

---

### Post by kseise on 2007-06-08
Yes, I can get in from the terminal using 

```
ssh hostname
```

I can ls and rm and all the standard bash commands.  It is only when unison attempts to connect.  I am prompted for my password, but then nothing else happens.

---

### Post by Mr. C. on 2007-06-08
Have you checked the troubleshooting tips here? :

[http://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTroubleshooting](http://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTroubleshooting)

MrC

---

### Post by kseise on 2007-06-09
I did not.  Thank you.  I actually realize that my hosting provider does not have unison installed on my server.  That would make using unison difficult to say the least.  I will have to figure something else out.  

I know it is a linux server, but I don't know if I have permission to install a program like Unison.

---

### Post by kseise on 2007-09-17
OK, I got it.  The inspiration came from this post [http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html]("http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html")


Basically, install FUSE and sshfs and mount the file server as a local mount point with ssh acting as the bridge.  Then I can run rsync between the two directories.
```
sudo apt-get install fuse-utils sshfs
```
```
modprobe fuse
```

> Using SSHFS

SSHFS is very simple to use. The following command

$ sshfs user@host: mountpoint

This will mount the home directory of the user@host account into the local directory named mountpoint. That’s as easy as it gets. (Of course, the mountpoint directory must already exist and have the appropriate permissions).

Example

create the mount point

#mkdir /mnt/remote

#chown [user-name]:[group-name] /mnt/remote/

Add yourself to the fuse group

adduser [your-user] fuse

switch to your user and mount the remote filesystem.

sshfs [email]remote-user@remote.serv[/email]er:/remote/directory /mnt/remote/

If you want to mount a directory other than the home directory, you can specify it after the colon. Actually, a generic sshfs command looks like this:

$ sshfs [user@]host:[dir] mountpoint [options]

Unmount Your Directory

If you want to unmount your directory use the following command

fusermount -u mountpoint

I will leave the rsync setup to someone else.  I haven't gotten to that point yet.

---

