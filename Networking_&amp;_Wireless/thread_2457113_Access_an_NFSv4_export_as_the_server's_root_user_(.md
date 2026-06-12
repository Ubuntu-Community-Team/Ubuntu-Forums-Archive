---
title: "Access an NFSv4 export as the server's root user (no_root_squash not working)"
date: 2021-01-26
forum: Networking &amp; Wireless
---

### Post by kennbr34 on 2021-01-26
I want to mount an NFS export on my server as root from my desktop. The purpose for this is to use my faster desktop system and borg to backup the filesystem on my server, as well as a couple of my other systems, via NFS exports of their root directories. For this reason I need the NFS client to have the same privileges to read any file that the root user on the NFS server would be able to.

In the past (wayyyy back in the 6.04 days) I've just used the 'no_root_squash' option but this appears to no longer work since it now uses kerboses.

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1733101](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1733101)

I tried that OP's method and started rpc-gssd with '-n' but that didn't work either.

I also found this suggestion on how to configure idmapd: [https://serverfault.com/questions/526762/root-access-to-kerberized-nfsv4-host-on-ubuntu](https://serverfault.com/questions/526762/root-access-to-kerberized-nfsv4-host-on-ubuntu)

I'm not sure how to create the configurations needed when I don't actually use domain names, and doing this entirely local with my local LAN addresses (192.168.0.0/16). Here's an example of an idmapd.conf configuration that's supposed to work, but I'm not really sure how to configure the domain sections. Can I just fill in any random domain names and pretend they're fully qualified? Using my system's home-names (i.e. 'ryzen' for the desktop and 'AMD' for the server) doesn't seem to work.

I would *really* rather prefer just to disable whatever kerboses and idmapd stuff is going on and just enable the simpler no_root_squash option to work. I've read this Ubuntu How-To and tried setting NFS to not use GSSD security, and using the 'sec=sys' option as mentioned, but this doesn't work either.

[https://help.ubuntu.com/community/NFSv4Howto#NFSv4_without_Kerberos](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_without_Kerberos)


I've tried these two export options...

```
/        192.168.1.22(ro,sync,no_subtree_check,all_squash,anonuid=0,anongid=0)
```

and the classic...

```
/        192.168.1.22(ro,sync,no_subtree_check,no_root_squash)
```

But as you can see, I'm unable to access certain directories if owned by root

```
kenny@ryzen:~$ sudo mount 192.168.1.2:/ /mnt/phenom_root/
kenny@ryzen:~$ ls -lah /mnt/phenom_root/etc/ | grep borgmatic
drwx------   2 root      root    4.0K Sep  5  2019 borgmatic
drwxr-xr-x   2 root      root    4.0K Sep  5  2019 borgmatic.d
kenny@ryzen:~$ ls -lah /mnt/phenom_root/etc/borgmatic/
ls: cannot open directory '/mnt/phenom_root/etc/borgmatic/': Permission denied

```

This is despite NFS on the server being configured explicitly not to use GSSD as described in the HOW TO above

```
kenny@AMD:~$ cat /etc/default/nfs-kernel-server 
# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS="--manage-gids"

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD="no"

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=""

# Options for rpc.nfsd.
RPCNFSDOPTS=""
```


This is becoming super frustrating and confusing and I'm not sure if I'm barking up the wrong tree, overlooking stuff, etc. so if someone could hold my hand and ELI5 I'd be grateful.

Desktop and Server details:

Server
Hostname: AMD
Local Address: 192.168.1.2
System: Xubuntu 16.04.7 LTS

Desktop
Hostname: ryzen
Local Address: 192.168.1.22
System: Xubuntu 18.04.5 LTS

---

### Post by TheFu on 2021-01-26
Sorry, I'm not any real help, as you'll see below.  Just a few thoughts ... 

NFS shouldn't be used for any backups any more than CIFS should. There is a risk of malware (crypto-locker) making it to the backup system when networked file systems are used. Rather, use the client/server methods leveraging ssh to "pull" the data to the server. With ssh-keys, this should be fast and painless for automatic backups that run as root.  Bonus points for using LVM/ZFS snapshots to quiesce the storage being backed up, otherwise data corruption is possible.

I don't know much about Borg, been using rdiff-backup for about a decade now. Used many other methods over the last 25+ yrs as an admin. Heck, even used tar over network pipes to tapes in the beginning.

You probably know this already, but regular support for 16.04 Server ends in a few months. Time to migrate.  The last few weeks, I've been migrating my last 16.04 servers to 18.04. Most of those migrations went smooth. It was only the desktop migrations that had problems. I don't use DEs, just an extremely stable WM setup.

Also, doesn't support for Xubuntu 18.04 end in April of this year, so it is time to move to 20.04 for that system. Yep: [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/)
> End of Life
    April 29, 2021

[https://borgbackup.readthedocs.io/en/stable/deployment/pull-backup.html](https://borgbackup.readthedocs.io/en/stable/deployment/pull-backup.html) explains to use sshfs (yuck!).

BTW, NFSv4 doesn't require the use of Kerberos, that is just the preferred method for greater security. I've never allowed remote-root access over NFS. That always seemed like a bad idea to me, but I'll admit not having an exact reason in mind now. Some things just "feel" wrong. I follow my gut.

The idea that deduplication is more *storage efficient* than other methods of versioned backups would depend on the data. I admit to being intrigued by the idea, in the same way I was intrigued into use hard-links for versioning with rsync/rsnapshot/rbackup tools. Practical requirements and a failure with rsync forced me to change backup tools. I ended up with rdiff-backup after playing with about 15 other tools first.

rdiff-backup is far from perfect, but the performance of the tool and flexibility are what got me to keep using it.  Between 18.04 and 20.04, rdiff-backup moved from python2 --> python3. This broke the transfer compatibility. I had to port the older python2 rdiff-backup version and a few dependencies to 20.04 to keep using my older rdiff-backup server.  That happened previously between the 12.04 and 14.04 releases too. On disk, the backup files don't care which rdiff-backup version is used. The format of the data hasn't changed. It really is just a python3 vs python2 data serialization thing outside rdiff-backup's control.

Anyways, as you can see, I don't have any answers for you. Sorry.

---

### Post by kennbr34 on 2021-01-26
> **TheFu said:**
> Sorry, I'm not any real help, as you'll see below.  Just a few thoughts ... 

NFS shouldn't be used for any backups any more than CIFS should. There is a risk of malware (crypto-locker) making it to the backup system when networked file systems are used. Rather, use the client/server methods leveraging ssh to "pull" the data to the server. With ssh-keys, this should be fast and painless for automatic backups that run as root.  Bonus points for using LVM/ZFS snapshots to quiesce the storage being backed up, otherwise data corruption is possible.

I don't know much about Borg, been using rdiff-backup for about a decade now. Used many other methods over the last 25+ yrs as an admin. Heck, even used tar over network pipes to tapes in the beginning.

You probably know this already, but regular support for 16.04 Server ends in a few months. Time to migrate.  The last few weeks, I've been migrating my last 16.04 servers to 18.04. Most of those migrations went smooth. It was only the desktop migrations that had problems. I don't use DEs, just an extremely stable WM setup.

Also, doesn't support for Xubuntu 18.04 end in April of this year, so it is time to move to 20.04 for that system. Yep: [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/)


[https://borgbackup.readthedocs.io/en/stable/deployment/pull-backup.html](https://borgbackup.readthedocs.io/en/stable/deployment/pull-backup.html) explains to use sshfs (yuck!).

BTW, NFSv4 doesn't require the use of Kerberos, that is just the preferred method for greater security. I've never allowed remote-root access over NFS. That always seemed like a bad idea to me, but I'll admit not having an exact reason in mind now. Some things just "feel" wrong. I follow my gut.

The idea that deduplication is more *storage efficient* than other methods of versioned backups would depend on the data. I admit to being intrigued by the idea, in the same way I was intrigued into use hard-links for versioning with rsync/rsnapshot/rbackup tools. Practical requirements and a failure with rsync forced me to change backup tools. I ended up with rdiff-backup after playing with about 15 other tools first.

rdiff-backup is far from perfect, but the performance of the tool and flexibility are what got me to keep using it.  Between 18.04 and 20.04, rdiff-backup moved from python2 --> python3. This broke the transfer compatibility. I had to port the older python2 rdiff-backup version and a few dependencies to 20.04 to keep using my older rdiff-backup server.  That happened previously between the 12.04 and 14.04 releases too. On disk, the backup files don't care which rdiff-backup version is used. The format of the data hasn't changed. It really is just a python3 vs python2 data serialization thing outside rdiff-backup's control.

Anyways, as you can see, I don't have any answers for you. Sorry.

Don't remind me 16.04 is EOL, I'm *dreading* migrating. I've  got quite a lot of highly-configured stuff running on that and  expecting it to break in a lot of wonderful ways. Not to mention I *detest* NetPlan.  Really I detest change in general.

I'm actually hoping these backups will help somewhat with the process by using the Borg backups as sort of 'snapshots' I can roll back to if migrating one service goes awry, so that I don't have to start all the way back at square one but can just start at the last working state. I've also been considering getting acquainted with btrfs or ZFS as my system partition for that purpose, but that seems like kind of a steep learning curve.

There's basically two reasons I'm using Borg. I can quickly and easily mount a backup from a previous date and restore files that may have been changed, and can keep repositories from several different points in time. Secondly, I want to mirror these backups to Google Drive or some kind of cloud storage, and so want to use encryption. I'm not sure but from what I've read rdiff doesn't allow me to do either of those?  

I didn't really like the idea of mounting the systems as read-write over NFS for the same reasons you mentioned, so honestly the idea of using SSHFS with Borg might be the best idea since I can't get NFS working anyway and it would satisfy security issues.

Anyway, bit off topic there...

If NFSv4 isn't required to use Keberos, I think maybe that bug just lead me down a wild goose chase with that. Must be something simpler I'm over-looking, but it also seems like I might not need/want to work too hard at it versus the SSHFS pull-method alternative. That might also help with other things I was going to take care of later ( such as making sure other hosts were up before backing up from them so I wasn't just backing up a blank directory where the NFS was usually mounted).

---

### Post by TheFu on 2021-01-26
My /etc/network/interface files migrated and are still being used on 18.04.  Happy surprise.

I don't think either btrfs or zfs are ready for the OS/boot partition.  Snapshots aren't backups. They are frozen blocks for a specific time. If the disk fails while they are frozen, we are still screwed.  snapshots are handy tools, for specific needs, not real magic. ;)

The last backup with rdiff-back appears as a mirror. Older backups are just diff.gz off the most current version. That means to restore a file or directory from last night, just copy the files back ... or more likely, use rsync since having the backup storage mounted to the client would be a security failure.

**rdiff and rdiff-backup ARE NOT THE SAME.**

sshfs is really slow and doesn't provide the full compliment of features that file systems expect.

There are a number of detailed posts in these forums about rdiff-backup.  
[LIST]
[*]aljames2 script w/ LVM snapshots: [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
[*]Simplified Script for desktop users: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)  
[*]Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[/LIST]
The discussions have what AND why.

BTW, I'm 100% positive that NFSv4 doesn't require Kerberos.
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/d/D1                     **nfs4**  3.5T  3.5T   25G 100% /d/D1
```

---

### Post by kennbr34 on 2021-01-26
Well, I can *mount* the share just fine

```
192.168.1.2:/                 110G   93G   12G  90% /mnt/phenom_root
```

But it's just when trying to read that one directory that's owned by root that I get permission denied even though it should be mapping my user ID to root.

Edit:

Okay I figured it out. I had another export that's used for network storage.

```
/mnt/vraid    192.168.0.0/16(fsid=1,rw,sync,no_subtree_check)
```

I needed to add 'fsid=0' to the export for / for it to work. I'm not really sure why that's the case, but it's definitely working now so that seems to have been the issue.

---

### Post by TheFu on 2021-01-26
fsid= is how NFS keeps separate exports ... er ... separate. I've only needed it when having the same location shared, but with different options.  Any uniq number can be used, don't think they need to be sequential or of any special size. I've never seen those numbers larger than 20.

---

### Post by kennbr34 on 2021-01-27
> **TheFu said:**
> fsid= is how NFS keeps separate exports ... er ... separate. I've only needed it when having the same location shared, but with different options.  Any uniq number can be used, don't think they need to be sequential or of any special size. I've never seen those numbers larger than 20.

Yeah I have only needed it before to see file-systems that were mounted within a subdirectory of another export, otherwise they would show up blank. I think the fact that I could see the directory contents gave me the false impression it was configured properly, where in fact it was using the options of the other export.

---

### Post by SeijiSensei on 2021-01-27
> **kennbr34 said:**
> I needed to add 'fsid=0' to the export for / for it to work. I'm not really sure why that's the case, but it's definitely working now so that seems to have been the issue.

fsid is unique to NFSv4 from what I can tell. I had a v3 server that worked fine, but when it was upgraded to v4 it stopped working until I assigned fsid numbers.

---

