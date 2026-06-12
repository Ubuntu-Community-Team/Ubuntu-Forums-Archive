---
title: "Advice for a small compute cluster"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by toddpedlar on 2007-07-24
Hi all -

Back in the day (ok, well not that long ago - 1993-1999) I was a graduate student who took care of network administration for my advisor's research group - and we did things back then on Digital alpha unix machines - a cluster of seven machines that had all their disks cross-mounted within the cluster, and a single user database.  People had home disks on the particular machines they normally sat at, but with the disk cross-mounting, such things were transparent.  We also had several data drives attached to the various machines in the cluster for common use - also all cross-mounted.  So this wasn't your traditional server/client setup, but a more modular approach.  The disks were all served by NFS, and the users administered their accounts by what was known then as NIS/yellowpages.   

I'm intending to set up the same sort of setup at my lab at my current institution, with 6 Ubuntu machines running (right now) Feisty Fawn - I'll also have a laptop that I want to be able to add
to the mix when necessary.  Again, I've got a lot of disk storage (2TB) that are attached to various of these machines, and I want it all accessible from everyone.  I'll have about 4 users at any one time.

What would you suggest for doing this in Ubuntu?  Samba seems to be a linux/windows service, which I don't need at all.   Any help/pointers/questions appreciated.

Todd

---

### Post by toddpedlar on 2007-07-24
More on the laptop that I've got.  

I'd like the laptop I have to be able to be part of this cluster - but also standalone when
I'm not at work - clearly I'd only then have access to data stored on its disk.  Is this going
to be problematic?  I gather when I've got it hooked into the college wireless I should be
able to remount all the disks in the cluster (hopefully manual isn't necessary but it's fine
if it is) but I don't want it to freak out when it's disconnected from the rest of the world.

I assume all this is *de rigeur*, but I am just getting back into this sysadmin kind of
thing and it's been too long (and I never did it with Ubuntu, not that it makes much 
difference).

Thanks,

Todd

---

### Post by tutomlin on 2007-08-10
Hi,

I'm a little new to linux but I have been looing at putting together a compute cluster for personal use and I have run across something that might help you out.  I know it's not quite the system you're envisioning, but you might have a look at NFSroot.  As I understand it all your computers would boot from the network and run diskless.  To be honest the system you describe sounds a lot more elegant, but you might find some helpful info looking at NFSroot forum posts etc.

Cheers

Tucker

---

