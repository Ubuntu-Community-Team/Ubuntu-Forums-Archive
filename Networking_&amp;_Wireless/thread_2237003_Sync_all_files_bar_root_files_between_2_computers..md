---
title: "Sync all files bar root files between 2 computers."
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by Rytron on 2014-07-30
Hi.

I want to sync all files bar root files between 2 computers.
Both have the same uid and distro. What files should not be synced?
I can think of .ssh (is that supposed to be different for each PC?) but are there others to omit?

Cheers.

---

### Post by TheFu on 2014-07-30
This is an excellent question.

If the computers are not 100% identical, I'd be worried. There are customized files for all sorts of things across the file system. Without installing the packages on both systems to keep those synchronized, (package manager metadata). Different packages will add different userids and groupids, so it isn't just root files to be worried about, there are many others.  It is easier to mirror files for specific users, especially for a home user or on systems with less than 50 normal users.

OTOH, if you want to mirror an install into a replacement system, that doesn't concern me much.  Only the hostname, IP address and network MAC would be a concern to me.  I've migrated HDDs from 1 box to another more than a few times and that works great.

If there are just 2 systems involved, I suppose mirroring /home would be fine.  Other parts of the file system might be needed too, but that depends on which other packages have been installed plus where and what sorts of data those may have.  Apache keeps files in /var/www, mysql keeps databases, pretty much every "service" or daemon has similar data to be maintained.

BTW, I'm not sure I understand fully, clearly, what you mean by "sync all files bar root files" - can you clarify?

I have about 20 different systems to be maintained. None are identical, but the base for the servers **is** identical, as is the base for the desktops.  We store data files that need to be shared on shared storage, so everyone who needs access has it.  Don't know if that helps or if you are trying to just keep personal settings sync'd between systems.

---

### Post by Rytron on 2014-07-31
Hi TheFu.

By "sync all files bar root files" I mean that nothing from / on PC1 will be copied to / on PC2. Just /home/me files.

I think I will play it safe and only copy over to PC2 files such as .mozilla, .thunderbird and such. I will sync all my PC1 files with an external HDD.

Cheers.

---

### Post by TheFu on 2014-07-31
Replicating /home is relatively safe.  Go for it.  I'd use rsync.

---

### Post by Rytron on 2014-07-31
> **TheFu said:**
> Replicating /home is relatively safe.  Go for it.  I'd use rsync.


Nice one! I like Grsync. ;)

---

### Post by Rytron on 2014-08-01
The contents of the '.ssh' dir would be different so syncing them would cause trouble.

---

### Post by TheFu on 2014-08-01
> **Rytron said:**
> The contents of the '.ssh' dir would be different so syncing them would cause trouble.

If the intent is to have 2 separate systems, on at the same time, making ssh/rsync/ and librsync connections then Rytron is definitely correct. 

~/.ssh/ is a special case - there are probably others dependent on the programs used.
If you don't use ssh/sftp/scp/rsync then don't worry ... however - you should.

---

