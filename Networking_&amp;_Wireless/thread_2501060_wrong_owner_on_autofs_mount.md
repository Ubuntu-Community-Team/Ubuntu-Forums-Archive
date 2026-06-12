---
title: "wrong owner on autofs mount"
date: 2024-09-21
forum: Networking &amp; Wireless
---

### Post by makitso on 2024-09-21
[SIZE=4]I have been using autofs for a while and it works fine.  However, I just noticed that all files and folders in the mounted directory have a user set to 501.  I tried to change the owner of a file and it won't let me. 
[/SIZE]
changing ownership of 'nfs-rob': Operation not permitted


[SIZE=4] How do I get autofs to set the correct owner?
I have the mount point as /NAS.

auto.master   
[/SIZE]/NAS    /etc/auto.misc   --timeout 60

[SIZE=4]auto.misc
[/SIZE]nfs-rob    -rw,soft,intr,rsize=8192,wsize=8192 192.168.4.205:/nfs/Rob

---

### Post by TheFu on 2024-09-21
So, autofs doesn't have anything to do with owners, groups or permissions.  It isn't SMB/CIFS.  Whatever the permissions are on the NFS server side (local storage there), is what NFS will provide.  

BTW, there's no need to specify rsize=8192,wsize=8192 since those are negotiated for optimal values and have been for about 15 yrs.  You found an old how-to, I guess.  Here are the options that I use for most of my NFS mounts, all using autofs:
```
/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  192.168.33.5:/d/D1
```
Try those, just swap your target and source locations.  The other options you have listed are defaults for over a decade.

But none of these will change the UID/GID of the files on the NFS server.  Any chance that is a MacOS system?

I use centralized user management, which is a completely different barrel of worms, but NFS expects for the UID/GID between the clients and server to match on the files and directories.  You can manually make that happen - change it on the NFS server, as root on clients isn't allowed to chown for NFS storage (remote).

I think there's a UID mapping daemon. I've never used it. **nfsidmap** is likely the name.  Not a GUI, so expect to setup translations on every client.  The manpages says this:
```
NAME
       nfsidmap - The NFS idmapper upcall program
...
DESCRIPTION
       The  NFSv4 protocol represents the local system's UID and GID values on
       the wire as strings of the form user@domain.  The process of  translat&#8208;
       ing  from  UID  to  string and string to UID is referred to as "ID map&#8208;
       ping."

       The system derives the user part of the string by performing a password
       or   group   lookup.    The   lookup   mechanism   is   configured   in
       /etc/idmapd.conf.
...

```
Since NFS is server-to-server, I'd expect some key requirements between the client and the server to be required to ensure that any random client cannot take over another user's files without the server agreeing.  I asked an AI engine how to setup the mapping.
[https://iask.ai/?mode=question&q=how+to+configure+nfsidmap+on+an+ubuntu](https://iask.ai/?mode=question&q=how+to+configure+nfsidmap+on+an+ubuntu) +client+and+server  I think that AI answer is missing the most critical parts of the mapping, but since I haven't tried it, I don't know what they are.  Most of the answer is about setting up NFS, which neither you nor I need help doing.  AI bloat.

Perhaps it would just be easier to manually ensure that the clients and server all have the same uid-username and gid-groupname settings instead?

---

### Post by TheFu on 2024-09-21
Almost forgot, my auto.master doesn't force all autofs mounts under a specific directory.
```
[COLOR="#FF0000"]/-[/COLOR]      /etc/auto.nfs --timeout=60 --ghost
```
Sorry that I forgot that. It matters in the auto.nfs file 1st parameter setting.

---

### Post by makitso on 2024-09-21
Thanks TheFu. The backend device is a MyCloud Ultra NAS device.  This problem came to light while doing an rsync command to back up my home folder..  rsync gave me errors when it tried to chan ge the owner on the NAS device.
I looked at the credentials and everything looks good.  The funny thing is that I have run the rsync command 3 months ago and never got the error.  HOWEVER, since then I needed to completely reinstall 22.04.04.

---

### Post by TheFu on 2024-09-21
Do you understand what I mean by the uid/gid having to match?   Use the 'id' command to see the numbers for each username from each client.  The numbers matter, not the username.

500 is typically for MacOS whereas Linux systems usually start with 1000 for human account uids and gids.  The numbers used by the uid and gid are conincidence only. They aren't related except by the passwd and group DBs.  On Ubuntu, the first username/uid are ????? and 1000.

---

### Post by makitso on 2024-09-22
> Do you understand what I mean by the uid/gid having to match? 

Thanks again for your guidance, I will have to do a little more research on this issue.

---

