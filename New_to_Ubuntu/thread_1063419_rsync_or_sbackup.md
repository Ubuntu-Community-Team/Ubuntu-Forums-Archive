---
title: "rsync or sbackup?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Dark006 on 2009-02-07
Hello, I am wondering which would be better to use, rsync or SBackup? I just did a backup to my external drive by doing:
```

sudo rsync -avx --exclude='/.gvfs'(because it kept giving me an error) /home/blake/ /media/disk-1/Backup-2009.02.07/

```

Now I've heard that rsync will only backup what has changed or been added/removed from the host machine. Is there any parameters/flags that have to be used with rsync to accomplish this? Or does it do its on its own? 

After doing this I downloaded SBackup and it seems to work really well, but will it do the same as rsync (as mentioned in paragraph above). If not I'll just use rsync and make it automated.

Sorry if that sounded confusing, I can clarify further if needed. Thanks for any help.

---

### Post by RealPSL on 2009-02-07
sbackup can take full backups and incremental backups (things changed since the last backup). I prefer sbackup because you can restore to any one of your backups. rsync is good to keep things insync but sbackup is a pure backup tool and provides more flexibility.

---

### Post by Dark006 on 2009-02-07
Should I just use the recommended settings for SBackup then? Because I don't see an option for incremental otherwise.

---

### Post by hyper_ch on 2009-02-08
realpsl: with a little scripting you can do that just as easily with rsync. Power of hardlinks :)

---

### Post by Kellemora on 2009-02-08
Hi Dark

I prefer using Rsync and MIRRORING the drive!  It's called Duplicate in Rsync.

Backups create Backup Sets and add-on increments to it.  They grow larger and larger in most cases.  And can take a long time to restore from a backup as well.
Whereas doing it as a Mirror, the backup is identical to the original as far as files go.
In other words, you could just cut n paste to get a file back.

However, a word of CAUTION is in order when performing backups OR Mirroring a drive using the DELETE command in the script.

In our case, with all employees using the File-Server, any one of them could delete numerous files that would not be caught until it's too late.  If you have DELETE turned on, those files will be REMOVED from your Mirror as well!!!!!

Because of this possibility, we will make a full mirror of the File-Server for permanent storage.  Archives and Permanent Data are also Mirrored to permanent storage.  Then a different file is used for hourly and daily backups WITH DELETE turned ON.  Once a week the File-Server folder is backed up with Delete turned off.  And again once per month with Delete turned off.
Because of the Permanent Mirror in storage, should a file or files come up missing, we still have them hidden away for recovery.  But it's not that hard to compare a Monthly Backup to the Yearly to see if something shrunk that shouldn't have.  When files are purposely deleted, as in we lost that client.  We can easily remove those files from the Permanent Mirror since it is a Mirror and NOT a Backup Set.........

You can also have different files for Permanent Data, Archived Data, etc. and leave DELETE OFF for those files, and only use the DELETE function for Daily Workfolders.

If you have critical data and don't have a separate building you can store that data in via LAN.  And don't want to use internet connections for storing data elsewhere.  I've done something here that was cheap and at least keeps one copy of our data fairly secure.  I purchased a fireproof safe, bolted it to the floor and placed a cool running USB external hard drive in it.
After burning one out because it didn't shut down between usages, I installed an exhaust fan in the safe and a tube that runs from the safe to outside the room where it's cooler.  A cheap WalMart RF-Tech thermometer shows the temp inside the safe currently at 86.5 degrees, which is good considering it's 73 outside this room where it draws it's air from.
We do use offsite storage too!

Just food for thought my friend!

TTUL
Gary

---

