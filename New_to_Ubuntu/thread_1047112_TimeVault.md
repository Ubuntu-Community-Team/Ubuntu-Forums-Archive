---
title: "TimeVault?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Archmage on 2009-01-22
I did read about TimeVault. But I didn't find it in my packagemanger. Isn't this in the stable Ubuntu already?

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by ChildOfMana on 2009-01-22
You can get it form [here]("https://launchpad.net/timevault/+download"). Please note that it is still in Beta at the moment.

Alternatively you can also try [Back-In-Time]("http://www.le-web.org/back-in-time/").

---

### Post by Archmage on 2009-01-22
Thank you for this information. But are there any nice gui-backup-desktop program in the normal repros? I don't want to install some extern software that migh have security holes that won't be fixed that soon.

---

### Post by ChildOfMana on 2009-01-22
To be honest I don't know the answer to that so, er... bump?

I've been using Back In Time for a while now and all seems to be okay with it.

Are you backing up to a network location? Because if you're backing up to an internal or USB/FireWire external drive then security *shouldn't* be a problem.

Obviously a network (or off-site) location may carry a small security risk as Back In Time will have to send data over a network.

**EDIT:** [this]("http://ubuntuforums.org/showthread.php?t=1047364") thread might help you out.

---

### Post by scotty64 on 2009-01-26
> **ChildOfMana said:**
> To be honest I don't know the answer to that so, er... bump?

I've been using Back In Time for a while now and all seems to be okay with it.

Are you backing up to a network location? Because if you're backing up to an internal or USB/FireWire external drive then security *shouldn't* be a problem.

Obviously a network (or off-site) location may carry a small security risk as Back In Time will have to send data over a network.

**EDIT:** [this]("http://ubuntuforums.org/showthread.php?t=1047364") thread might help you out.

How did you install Back In Time? I have added the hardy repo and installed it from there, but it shows very strange behaviour:
When I try to create a snapshot the program creates the "backintime" directory on my external 1Tb Maxtor Hd plus the "snapshotxxx" and "backup" subdirectories but it does not store a single byte on the disk. It starts two rsync processes that scan my machines internal HD madly and these processes consume more and more memory over time. I wonder if rsync has a memory leak or if Back In Time tries to store the entire directory in SHM before writing anything to disk?

---

### Post by ChildOfMana on 2009-01-26
[quote="scotty64"]How did you install Back In Time? I have added the hardy repo and installed it from there, but it shows very strange behaviour:
When I try to create a snapshot the program creates the "backintime" directory on my external 1Tb Maxtor Hd plus the "snapshotxxx" and "backup" subdirectories but it does not store a single byte on the disk. It starts two rsync processes that scan my machines internal HD madly and these processes consume more and more memory over time. I wonder if rsync has a memory leak or if Back In Time tries to store the entire directory in SHM before writing anything to disk?[/quote]

I'm using the Intrepid version and haven't encountered anything like the problems you mention above so can't help you I'm afraid. Don't know what would cause the program to behave like that.

Perhaps starting a dedicated thread on the topic might net you some answers? I'd be interested in the answer just out of curiosity.

**Edit:** I've just thought; are you the owner of the external drive and do you have read/write permissions? Back-In-Time runs under your user account and not as root so you need to be the owner of, and have read/write permissions for, the media you are backing up to. This may possibly be why no data is being written to your external drive. Just a thought.

---

