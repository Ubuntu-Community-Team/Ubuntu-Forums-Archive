---
title: "Accidentally my whole pictures folder"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Lexyboy on 2010-08-20
Hi All,

(begin rant)

So, I was browsing to a folder of photos in Gnome, selected my "Pictures" folder and then pressed return... except that I hit delete by mistake (stupidly close on my keyboard).  No Pictures folder any more.  OK, I'll just open Deleted Items...

Not there either.  Not anywhere (did a shell 'find')

All I can think is that I must have hit delete and enter in rapid succession, first deleting the folder then confirming permanent deletion since it's too big for the bin (>10GB).  Any other ideas?

Anyway, have most of it backed up - just a bit of a rant that it should be so easy to do this!  Surely the confirmation should default to 'cancel'??

Doesn't seem to be any easy way of getting my files back... (on ext4 if it helps).

---

### Post by Paul820 on 2010-08-20
Photorec: [http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")
EDIT: Search synaptic for testdisk, photorec comes with it.

---

### Post by sikander3786 on 2010-08-20
Hi.

Not so easy to recover deleted data from the HDD on any OS. If you have a back up, stick to it. Still if you want to try to recover that folder, a few useful links are mentioned in [this]("http://ubuntuforums.org/showthread.php?t=1552088") thread.

Regards.

---

### Post by LowSky on 2010-08-20
> **Lexyboy said:**
> 
Anyway, have most of it backed up - just a bit of a rant that it should be so easy to do this!  Surely the confirmation should default to 'cancel'??
  

The standard practice is for Yes to be highlighted , even in Windows and Mac. Sorry for your bad luck. 

If you are afraid of this happening again change the permissions for the folder to only allow read access. This way only sudo or another user you apply will have writing access to the folder and deletion will not be possible.

---

### Post by David Andersson on 2010-08-20
Open *Synaptic*, quick search for *recover files*. About seven of the matching packages appears to be about recovering deleted files. (Search > Description and Name for slightly other seven packages to do the same.)

Note, there is no guarantee, if the disk has been used since the delete, or if it is fragmented.

> **Lexyboy said:**
> 
Anyway, have most of it backed up - just a bit of a rant that it should be so easy to do this!

I know. I just wanted to rant at #2 about going out on the internet to get software.

---

### Post by Paul820 on 2010-08-20
> I know. I just wanted to rant at #2 about going out on the internet to get software.
Yeah, well go rant somewhere else, there was an edit in there, or didn't you happen to notice that?

---

### Post by Rubi1200 on 2010-08-20
There are different options mentioned here as well:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Good luck!

---

### Post by uRock on 2010-08-20
Don't download anything within the OS, you may write over the location where some of the photos are.

---

### Post by Lexyboy on 2010-08-27
Thanks for the advice - I'd already looked into Testdisk and Photorec, but seemed like a lot of hassle when I had most of the files backed up.  (Also I got an error when using Testdisk which I couldn't be bothered to get to the bottom of)

In fact I've just tested it with another big folder and it didn't even ask for confirmation - just deleted the lot without trace :(  Need to have a look at how to get Gnome to mollycoddle me a bit...

---

