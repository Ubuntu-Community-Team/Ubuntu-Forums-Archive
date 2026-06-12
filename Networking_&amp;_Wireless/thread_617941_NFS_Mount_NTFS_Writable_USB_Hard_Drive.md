---
title: "NFS Mount NTFS Writable USB Hard Drive"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by Ozzman on 2007-11-19
This is my first post here as this community has been amazing in helping me with all my issues thus far, however this one I seem to be stuck on..

Just as the title says im trying to mount a NTFS External Hard Drive on a remote system using NFS.

I have another folder already shared and mounted so I am aware of the NFS mounting process. However my NTFS based External Hard-drive wont mount on the remote system. keep getting permission denied (exports list is already updated with the same working hostname as the other share, and I have restarted nfs-kernel-server)...

Any Ideas? Im thinking it might be because the external drive is mounted as writeable and is NTFS but am not sure, and dont remember how to make it un writeable to check. (however I would like to keep it writable if possible)

Thanks.

---

### Post by gmh04 on 2007-11-23
Hello, I have the same issue. I would be interested to hear of any ideas

---

### Post by gmh04 on 2007-11-24
I got my external drive to mount:

[http://www.linuxquestions.org/questions/linux-networking-3/nfs-mount-external-drive-601848/](http://www.linuxquestions.org/questions/linux-networking-3/nfs-mount-external-drive-601848/)

---

### Post by borobudur on 2007-12-30
Nice explanation from jschiwal on [www.linuxquestions.org](www.linuxquestions.org) !

I just have one little problem with my remote usb-drive.

I have two users on the client and one of them can't access the mount because the owner after mounting is the user with uid=1000.

I don't understand who sets it to this user?

Here a better explanation of the actual condition:
Server has user X
Client has user Y and Z
After mounting the mounted directory has the owner Y and group Y. 
Z can't access :-(

Any idea??

---

### Post by borobudur on 2008-01-12
Solved my problem with these options in the export file: 

rw,squash_uids=1000-1001,squash_gids=1001

---

