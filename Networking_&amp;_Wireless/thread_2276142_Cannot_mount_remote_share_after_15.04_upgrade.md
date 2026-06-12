---
title: "Cannot mount remote share after 15.04 upgrade"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by 64mgb on 2015-04-30
Here is my setup:

I have a Xubuntu machine setup to do backups nightly.
My main machine (the one with data to be backed up) is Ubuntu.
I have a share setup on the main (Ubuntu) machine that the backup machine mounts and uses to read the data to be backed up.

A couple of days ago I upgraded the Xubuntu machine to 15.04...everything went fine...no problems.
Last night I upgraded the Ubuntu machine to 15.04.  Now, the backup machine cannot mount the share.  I get "failed: Remote I/O error"

If I enter this command in terminal:
sudo mount -t cifs //<server>/<share> <mount point> -o username=xxxx

I get: 
mount: //<server>/<share> is write-protected, mounting read-only
mount: cannot mount //<server>/<share> read-only

If I enter this command in terminal:
sudo mount --rw -t cifs //<server>/<share> <mount point> -o username=xxxx

I get:
mount: //<server>/<share> is write-protected but explicit `-w' flag given

I I enter the same command but give it an invalid username, it mounts, allows me to write files to the server, but can't edit those files, even after changing permissions and owner/group.

The share is setup with the "Allow others to create and delete files in the folder" checked.

Any ideas?  Thanks,
Rich

---

### Post by 64mgb on 2015-05-02
For anyone that may have this problem in the future, I solved it based on post #3 in this thread:

[http://ubuntuforums.org/showthread.php?t=2127616](http://ubuntuforums.org/showthread.php?t=2127616)

I installed cifs-utils on the Xubuntu machine (the one that was trying to mount a remote share) and all is fine.

Rich

---

