---
title: "Looking for a good amazon s3 incremental backup solution"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by allspiritseve on 2009-01-02
Hello all,

I'd like to be able to store a daily, weekly, and monthly backup of my home directory on Amazon s3. Preferably I'd like these backups to be incremental, so only the differences between the three are updated. I'd rather not store three whole versions of my home directory if at all possible. Can anyone recommend a good, trusted application to do this with? I was looking at duplicity, but it looks like it can only store one copy (though with incremental backups). 

Thanks,

Cory

---

### Post by Kellemora on 2009-01-02
Hi ASE

Any reason why you want to use Incremental Backup instead of just simply Mirroring or Mirroring and Compression if space is an issue?

A Backup needs restored, along with all the increments that were saved after the primary backup.

You still end up with the same damaged file as the Backup is restored unless you restore without adding the incrementals back to it.

If you mirror your drive daily, it goes very quick after the first time as only files that changed are replaced.
Then for redundancy it's wise to mirror a copy off-site as well.

Here, all of our working drives are mirrored to externals 4 times a day, then the externals are mirrored off-site during the night.  A copy of the off-site mirror is made once a week and stored in the vault, just in case!

Rsync handles this quite well and fast too.
GRsync is a GUI version of the same program.

I prefer a Mirror, because I can chunk that hard drive in any machine or view it online and have all the same files in their same locations right now.

Whereas with Backup Sets, you have to locate the particular BackupSet you want, RESTORE that Backup to the location it was made from, let all the increments install themselves, then finally you can find the file you are after.

It's like RAID 1 without the danger of a controller failure!

TTUL
Gary

---

### Post by allspiritseve on 2009-01-02
Any chance you could explain the difference between mirroring and incremental backups?

---

### Post by allspiritseve on 2009-01-04
Has anyone successfully installed s3fs on intrepid? I can't seem to get it to work.

---

