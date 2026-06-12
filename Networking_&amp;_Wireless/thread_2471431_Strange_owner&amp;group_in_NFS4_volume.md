---
title: "Strange owner&amp;group in NFS4 volume"
date: 2022-01-30
forum: Networking &amp; Wireless
---

### Post by zkab on 2022-01-30
I have Ubuntu 21.10 and have mounted a NFS4 volume on a Synology NAS with autofs ... and it seems to work OK 
but a while ago I discovered that some directories in the NFS4 volume have 'owner=1024 & group=users' but inside the directory all the files have the right owner&groups.
I tried to chown for that specific subdiretory but get ... 'Operation not permitted' ... even with sudo.
What is the reason that I get '1024/users' and how do I change it?
I have the same user in the NAS and my Ubuntu box so I don't understand where '1024/users' come from.

---

### Post by TheFu on 2022-01-30
NFS uses the uid/gid numbers, not the usernames or groupnames.  At some point there was a uid of 1024.

NFS doesn't allow the client root account any privileges. To modify owners has to be performed on the NFS server. Do it there.  I have no idea how to do that on a Synology. Sorry.  On a standard linux NFS server, I'd ssh into the NFS server machine and use sudo chown there. The first userid/uid on Ubuntu is 1000, so while ssh'd into the synology, use **sudo chown 1000 path-to-file-or-directory**. I'm assuming sudo works on a synology, but I don't know.  Or you can become root and do it that way on the synology.  Whatever works.  After that, the username with a uid of 1000 will be the owner.

---

### Post by zkab on 2022-01-31
Thanks ... now I understand that privileges have to be changed on the NFS server and not on the client side.
I did what you recommended and it worked perfectly.
Thanks again for your explanation and recommendation.
You saved my day!

---

