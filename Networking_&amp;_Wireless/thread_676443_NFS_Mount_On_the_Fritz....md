---
title: "NFS Mount On the Fritz..."
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by mobius777 on 2008-01-23
Okay, I've searched the forums and Google, and have found nothing similar to my issue. 

I've been running Ubuntu 7.10 for about 4 months now, both on my server and my daily work PC (was a former Windows user, so please help me and don't make me go back!). Anyway, I set up NFS mount on m daily work PC mapped to my server's exported NFS directors all 4 months ago, and it was all hunky-dory. 

Until last week. Last week weird stuff starting happening. Initially one or two of my NFS mounts would not mount at boot up. There would be a delay on a few of them, but they would eventually mount. There was no pattern -- sometimes they would all mount, other times various ones would mount and others not. Eventually, these past few days, none of the NFS mounts would mount at all. I tried rebooting the server,  tweaking the /etc/exports file (on the server) or the fstab settings on my daily work PC-- I even tried resetting my Linksys router (who knows). And while occasionally an NFS mount would mount, not all would mount, and some times none would mount. Grrrr.

Prior to the various tweaks I made to try to get my NFS mounts to mount, I had made no changes to either /etc/exports or fstab. In fact, I hadn't had to touched a configuration file in 2 months.  I do install all the updates that come through on both computers. So if there was a recent patch for anything that might effect this, that could be a possibility too.

At any rate, I've now gone to SMB mounting my drives, but that's just retarted. Here I am with 2 linux boxes, the server is now SMB sharing, and my daily work PC is SMBFS mounting the shared drives. But hey, it works. It's retarted -- but it works.

I would really like to get NFS working again. And I don't know if the problem is on my daily work PC (the client, basically) or the server.

Here's a sample of my /etc/export file on the server:

/media/data1/archives *(rw,no_root_squash,async)
/media/data1/audio *(rw,no_root_squash,async)  
/media/data1/pictures *(rw,no_root_squash,async)  

And the fstab on my daily work PC that is trying to mount...

192.168.1.3:/media/data1/archives /data/archives nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.3:/media/data1/audio /data/audio nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.3:/media/data1/pictures /data/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

And yes, that is a static IP address (I'm not that dumb).

Oh, yeah, and the server does log some "authentication mount requestsions" (it repeats this over and over and over), but nothing about rejecting anything. 

So.... ideas?

---

### Post by mobius777 on 2008-01-29
Okay, it's been 5 days and no one has replied. Maybe I'm the only one with this problem, but regardless, does anyone even have an idea what I could do to try and resolve this issue?

---

