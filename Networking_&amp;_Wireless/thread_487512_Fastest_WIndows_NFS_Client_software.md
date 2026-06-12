---
title: "Fastest WIndows NFS Client software"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by rzj on 2007-06-29
Which windows NFS client software is fastest?

I need to get decent network file sharing between windows and an ubuntu server. I've been using Samba, but it seems that the protocol overheads are a disaster for large data volumes accessed by an application like winrar that wants to take many bites at the data. I don't know if samba performance would be better if the whole file was pulled in one go, but it doesn't seem to be, and anyway I want flexibility to use linux shares as my bulk file storage for my windows machines (XP home primarily, possibly Vista and ideally 2k as well)

It seems that NFS may be the better solution, and I'm going to have to wade through howto's for the ubuntu side of that.

My search for windows NFS client has turned up a few options, and since the efficiency of the code at handling large volumes, gigabit data rates and possibly smallish individual read and write operations is critical and likely to vary between packages I'd like to know if anyone has experience of this and can recommend which is the best (free) package?

TIA,

Ray

---

### Post by darkog on 2007-06-29
> **rzj said:**
> Which windows NFS client software is fastest?

I need to get decent network file sharing between windows and an ubuntu server. I've been using Samba, but it seems that the protocol overheads are a disaster for large data volumes accessed by an application like winrar that wants to take many bites at the data. I don't know if samba performance would be better if the whole file was pulled in one go, but it doesn't seem to be, and anyway I want flexibility to use linux shares as my bulk file storage for my windows machines (XP home primarily, possibly Vista and ideally 2k as well)

It seems that NFS may be the better solution, and I'm going to have to wade through howto's for the ubuntu side of that.

My search for windows NFS client has turned up a few options, and since the efficiency of the code at handling large volumes, gigabit data rates and possibly smallish individual read and write operations is critical and likely to vary between packages I'd like to know if anyone has experience of this and can recommend which is the best (free) package?

TIA,

Ray

Have you tried optimizing & tweaking Samba conf/settings?

Why do you think NFS would be faster?

---

### Post by rzj on 2007-06-29
> **darkog said:**
> Why do you think NFS would be faster?

Because Samba is running so slowly there must be performance problems somewhere in the software chain. When I run NFS from ubuntu to ubuntu I get very high speed - 800Mbytes in about 15 seconds which is over 400mbits/sec of actual data before allowing for any file system protocol overheads or tcp/ip overheads.

I have just installed Microsoft's own tools for unix which includes NFS and that is also pretty slow - initiated from the ubuntu end I got a little under 2 minutes to pull it down to ubuntu, and close to 4 minutes to push it back. 

> **darkog said:**
> Have you tried optimizing & tweaking Samba conf/settings?

What settings might affect the speed significantly?

I have USER mode security set, the shares I'm testing are ext3 fast ATA133 and SATA drives, telling XP which username to use. My impression is that there is a big delay each time windows tries to initiate a read or write operation.

The physical connection is identical to the 15 second ubuntu test. I haven't retested the link with samba to get a direct comparison with my 800Mb file. Will try that tonight.

I'm wondering if ubuntu in a virtualbox inside XP would deliver the speed. I don't want to have to reboot to transfer files and I'd prefer to be able to use the ubuntu server as a genuine file server and not have big disks on the XP machine, and not have any data on XP so that I don't have to back it up except for a full system reinstall image.

Ray

---

### Post by darkog on 2007-06-29
> **rzj said:**
> 
What settings might affect the speed significantly?



[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")

Though you may want to check the client settings settings as well.

---

### Post by rzj on 2007-06-29
OK, thanks, I'll have another play with Samba when I get a chance.

Ray

---

