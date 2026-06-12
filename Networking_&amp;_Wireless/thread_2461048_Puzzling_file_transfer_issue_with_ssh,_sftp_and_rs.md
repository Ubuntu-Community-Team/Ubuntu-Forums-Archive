---
title: "Puzzling file transfer issue with ssh, sftp and rsync."
date: 2021-04-23
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-04-23
I am attempting to set up a remote archive of my offices data file and user home directories, primarily as a disaster recovery option.

I have a machine in a location outside our office connected to the Internet and plan to create crontabs to copy the current contents of our data and home directories there. My intention is to use rsync to accomplish this. I have been attempting to make the initial copies and have run into a puzzling problem. The resync copies freeze after a period of time. But I can log into the remote machines and maintain an ssh session for days at a time. I have ssh keys set up to authenticate the user. One copy operation was freezing on the same file every time. The file is large (several gigabytes) but it never completed. I decided to try see if something in the connection was causing the problem so I decided to use sftp to copy the file and it worked except fo the ownership and date..

The rsync command line command is in the form:

 ```
rsync -avz /home user@remote.domain.com:/backup/remote
```

The crontab omits the "v" as I don't see the need for that.

I have ssh keys set up to authenticate the user.

The sftp was simply on the command line.

I'm wondering why the sftp works and the rsync doesn't.

---

### Post by TheFu on 2021-04-23
Up the verbosity level?

Generally, syncing a single user's HOME that way is fine, but really it would be best to follow backup standard practices.
3 - copies
in 2 - locations
1 remote.
```
rsync -avz /home/[COLOR="#FF0000"]user[/COLOR] user@remote.domain.com:/backup/remote
```
This assumes the current userid is "user".  If any other userid is involved, it probably won't do what you want. You'll need root to be used on both sides - or ... root-equiv accounts.

I use rdiff-backup for local versioned backups. Those are "pulled" by the backup server from each client. This is a security thing.  Then the rdiff-backup directories are rsync'd to a remote location. It is almost a clone.  It doesn't write into "live", in-use systems, but to backup storage there.  This captures all the versioning and removes the older backups as they are removed from the local rdiff-back system.  Because we have some systems that use sparse files, the rsync option to handle sparse files is used.  Before I added that, we kept running out of storage on the remote system as the sparse files exploded in size from 5MB to 80GB.

Another bonus is that rdiff-backup knows how to exclude "special files" which cause problems with backups. Devices, fifos, named pipes, sockets, etc.

---

