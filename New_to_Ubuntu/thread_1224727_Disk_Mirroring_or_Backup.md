---
title: "Disk Mirroring or Backup"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by sharkllama on 2009-07-27
Hi, 
  A bit of a noob here so please bear with me if I ask some very simplistic questions.  I just put together a new computer on which I am dual booting ubuntu and windows 7.  There are two hard-drives installed and I had planned on using one as a mirror (let's call this the backup disk) or some other redundent form of storage where backup(s) from what I'll call the primary disk are stored.  So I would like the two disks to either be identical (within some reasonable timeframe let's say a day or so), or for the backup disk to contain incremental backup information about the primary disk.  So to recap a basic description of my primary disk shows 4 partitions:

[LIST]
[*]Windows (ntfs)
[*]Ubuntu Filesystem (ext4)
[*]Ubuntu Swap (?)
[*]Extra Storage Space (fat32)
[/LIST]

Without implementing RAID, which I understand is a hassle, what would be a good method to create/maintain the backup disk?  I have briefly looked into using bacula and running a client in both OS's that would be scheduled to create backups on the extra disk but was pretty confused and a little overwhelmed by the configuration.  Other options I've considered involve using rsync to essentially mirror the hard-drive.  This was a sub-optimal as if I use windows for an extended period of time (please no snide remarks here xD ) I lose my backup capabilities.  Any thoughts?  Anyone else encountered this problem or perhaps can point me to someone who has set up a bacula (or similar software system) for dual boot backups?  
Thanks Guys,
Brant

---

### Post by mapes12 on 2009-07-28
Hi 

Welcome to the forum.

IMHO you will struggle to achieve your objective without deploying some form of RAID 1 configuration. Linux has built in software support so no new hardware is needed. This HowTo describes "fakeRAID" and how to set it up with a dual boot machine:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Mark

---

