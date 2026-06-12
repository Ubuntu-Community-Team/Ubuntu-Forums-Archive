---
title: "Evolution restore problem"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by chitragurung on 2011-02-22
Hi,

I just installed Ubuntu 10.04 and I did trying to restore my backup of evolution-back-up-tar.gz file but I could not restore. When I try to restore through restore feature of evolution, it gives error message 

please select valid backup file to restore

How to fix it ?

My back up is in evolution-backup.tar.gz

---

### Post by iyas120 on 2011-06-20
Yes, i am experiencing the same problem... when i try to manual extract it says:
gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

Ohh my....i lost all my email now.. please some one help me...:(

---

### Post by chitragurung on 2011-06-22
Best idea is copy all your email folders like inbox, mail, contacts etc to

.evolution folder of your pc. I mean replace new folders with your back up folders.

.evolution is available in your home folder.

But you have to make your folder able to view hidden files which can be done going to edit

---

### Post by brion@cbkidder.com on 2011-10-17
This is ridiculous. I faithfully backed up my Evolution and now when I need it, I get an error message saying the backup file isn't valid. WTH?

Is there a work around for this? Please?

---

### Post by verymadpip on 2011-10-17
I had the same issue when I dropped back to 10.10 from 11.04.

It's a case of copying the individual folders over as chitragurung says.

As far as I can recall (& looking at an old Evolution backup tar.gz) all the bits you will need are in the tar.gz.
I think it may even be possible to just copy the entire .evolution folder over from the opened archive.
As you will only be copying stuff it will all still be there in the tar.gz if it goes a bit wrong the first time.

It's definitely do-able.

Please let us know how it goes.

(I actually opted to migrate to Thunderbird in the end, but that's a whole other story).

---

### Post by brion@cbkidder.com on 2011-10-17
Thanks for the tip. I also am reverting from 11.10 to 10.4 due to performance issues. The file tree of the backup tarball is different to the Evolution 2.8 installed structure; I think the backup is from a newer version of Evolution.

I was able to copy and paste the address book and mailbox folders successfully, but it is frustrating when the restore function doesn't work. Still, I enjoy all this Ubuntu free of charge, so it's a net positive in the end.

---

