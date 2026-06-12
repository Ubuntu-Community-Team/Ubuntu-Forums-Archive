---
title: "Clients with NFS mounts to servers never shut down"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by mattlach on 2014-07-20
Hey all,

I googled this, but the solutions I found were old, and I'm not sure if they are still the proper way to solve this.

I have a FreeNAS server that handles all my storage.  All my clients (all 14.04 based, some mythbuntu, others straight up Ubuntu or Linux Mint)  just use small SSD's and store all files remotely via NFS.

I mount the NFS shares in fstab using the following line:

```

xxx.xxx.xxx.xxx:/location/to/share/on/server /mount/location/on/client nfs    rsize=8192,wsize=8192,timeo=14,intr,rw,user

```

Whenever I shut down the clients, they just sit forever on the shutdown screen, forcing me to hard poweroff, occasionally resulting in file system corruption.

What is the current best solution for this problem?  I'd rather avoid using soft mounts if at all possible.

Appreciate any suggestions.

---

### Post by TheFu on 2014-07-20
I don't have this issue, but I use autofs and the automounter for all NFS mounting, NOT the fstab.  I don't know if it is "better" or not.  My NFS server is running 14.04 (1 week old), upgraded from 12.04 recently. No issues with either. Clients are a mix of 12.04 and 14.04.

Also, I do not mount /home from NFS, rather, I mount /D and keep mainly large files there. Been tempted to mount /home over NFS, but I recall the issues in the mid-1990s at work doing that and decided against it.

Doesn't 14.04 default to NFSv4?  Does forcing it to v3 help?

---

### Post by mattlach on 2014-07-20
> **TheFu said:**
> I don't have this issue, but I use autofs and the automounter for all NFS mounting, NOT the fstab.  I don't know if it is "better" or not.  My NFS server is running 14.04 (1 week old), upgraded from 12.04 recently. No issues with either. Clients are a mix of 12.04 and 14.04.

Also, I do not mount /home from NFS, rather, I mount /D and keep mainly large files there. Been tempted to mount /home over NFS, but I recall the issues in the mid-1990s at work doing that and decided against it.

Doesn't 14.04 default to NFSv4?  Does forcing it to v3 help?


I don't mount home either.   How does automount using autofs work?  Where do you define the mounts if not in fstab?

---

### Post by TheFu on 2014-07-21
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) - lots of good stuff on that site.

---

### Post by sedawk on 2014-07-21
What happens if you first do a "umount /mount/location/on/client" on a client and then
run the shutdown? Does it work then?
BTW: I think that "intr" is a deprecrated option.

---

### Post by mattlach on 2014-07-21
> **TheFu said:**
> [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) - lots of good stuff on that site.

Thank you.   

I will have to try this.

It's funny.  Been using linux primarily for more than 10 years, and had never heard of autofs before.

---

### Post by mattlach on 2014-07-21
Well, I tried autofs using the linked guide, but couldn't quite get it to work.

The sample files I have look a little different than in that guide.  I wonder if something has changed since that guide was created.

Anyway, I'm not sure I'm a fan of the solution where the mountpoints don't show up until the location is mounted.   Makes it difficult to tab to autocomplete!

---

### Post by TheFu on 2014-07-21
> **mattlach said:**
> Thank you.   

I will have to try this.

It's funny.  Been using linux primarily for more than 10 years, and had never heard of autofs before.

Home users rarely use NFS like large enterprises/governments do. Until you see 1,000+ high-end workstations working together in a combined effort, it is hard to learn this stuff.

It used to be called "automounter" and the daemon was "amd" - it had "spongy" mounts, which behave like hard mounts, unless there is an issue, when it behaves like a soft mount (i.e. doesn't lock up the entire system). Not sure what happened to those - there was about a decade where I didn't use amd at home and wasn't hands-on running any servers at work.

I have huge gaps in my knowledge too.  Not to mention all the things I once knew well and have forgotten.  It is hard to know what we don't know, right? ;)  

I use autofs for some USB storage and all nfs and cifs mounts.  Even use it on laptops for data storage - works great as long as I don't attempt to access the data when on a different network. 

Anyway, I hope it works for your stuff too.

---

### Post by TheFu on 2014-07-21
> **mattlach said:**
> Well, I tried autofs using the linked guide, but couldn't quite get it to work.

The sample files I have look a little different than in that guide.  I wonder if something has changed since that guide was created.

Anyway, I'm not sure I'm a fan of the solution where the mountpoints don't show up until the location is mounted.   Makes it difficult to tab to autocomplete!

I don't think so.

On the nfs server, 
* use the /etc/exports as normal. I always specify IP addresses and don't allow root/suid.

On the nfs clients, 
* add a line in /etc/auto.master to include the auto.nfs file.
```
/-      /etc/auto.nfs
```
You can use '-' if the mount to / is desired, or use /media or /long/path/for/mounts, if you like.
* update the auto.nfs file with the mount location.```

/D -fstype=nfs,hard,intr,rw,async,vers=3    istar:/D
```
Because I specified /-, the mount on the client will be /D.

Hope I haven't confused more than I helped.

---

