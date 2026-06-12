---
title: "Incremental backup in Rsync with rollback"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by aireq on 2009-01-14
RSync can do an incremental backup but can it save each increment? Or otherwise "roll back" to where everything was at a point in time?

What i want to avoid is accidentaly messing something like deleting a bunch of files that I need, and then having some backup make the same mistake in the backup before I notice the problem.


Eric

---

### Post by hyper_ch on 2009-01-14
yes, it can... have a look at hardlinks.

---

### Post by .nedberg on 2009-01-14
Also have a look at [rdiff-backup]("http://www.nongnu.org/rdiff-backup/").

I am going to convert from rsync to rdiff-backup soon. It does just what you want.

If you like it you will need the --force switch to make the backup directory that rdiff-backup uses.

---

### Post by Kellemora on 2009-01-14
Hi air

There's a way to do it without having to make incrementals.

I have weekly and monthly mirrors, plus the daily mirror.

I DO NOT use --delete on any of the mirrors automatically.

AFTER each Monthly mirror is made.  I will use the --delete on the daily backup to the first weekly mirror to clean out old junk, then take the --delete OUT of the script again.

Or in practice I just run different scripts is all.  
I don't recycle the Monthly mirrors for a full year!
Which gives us plenty of time to find something that may have been accidentally deleted, or as in most cases, changed in a particular way that didn't quite work out after it was in use for a long time.  Some items are Archived and Locked so they can't change, even if they are deleted from the original.  Just pitches us an error and I can check it out.

A disgruntled employee can wipe out your entire file server and it's backup by simply deleting them from the file server moments before rsync runs, if you have that --delete option in the code.

TTUL
Gary

---

### Post by lucidsystems on 2009-08-25
You may be interested in [LBackup]("http://lucidsystems.org/tools/lbackup").

---

### Post by Cheesemill on 2009-08-25
Take a look at [rsnapshot]("http://rsnapshot.org/") (it's in the repositories). It's based on rsync but provides full incremental backups

---

