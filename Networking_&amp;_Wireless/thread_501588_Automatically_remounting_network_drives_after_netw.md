---
title: "Automatically remounting network drives after network error?"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Rich99 on 2007-07-15
I'm running Dapper, and connect to a netware volume via ncpfs, to which the machine backs up every night.  I have the drive listed in fstab & it mounts & umounts fine.  However if the remote machine has a temporary problem, then comes back up, the mounted share in dapper doesn't recconnect.  If I try & run a command in the mount, I get an IO error.  I have to umount & remount it.  Not  huge issue, but often I don't know about it till the next morning whem I see that the backup to the remote share failed.  Is there a way to force it to remount automatically?

---

