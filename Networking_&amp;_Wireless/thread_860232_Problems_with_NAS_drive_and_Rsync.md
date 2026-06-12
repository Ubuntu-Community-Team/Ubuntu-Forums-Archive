---
title: "Problems with NAS drive and Rsync"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Krydahl on 2008-07-15
I've been using a NAS drive for backups with rsync for a while now with no problems.

When I upgraded to Hardy, there were some issues mounting the NAS because smb is now depreciated and I had to switch to cifs, however I got this working ok.

Recently, however, I've been having problems with rysnc. It will create new files without problem. It detects changed files ok, but when it tries to update them it fails. It seems to be creating a new hidden file with the filename of the changed file plus a hash of some kind. I'm guessing that it is then meant to delete the old version and change the name of the new file. It doesn't seem to be reporting any errors, it's just leaving the old version in place and leaving the hidden file on the drive.

I'm guessing this is something to do with permissions, but everything looks ok. (The drive is fat32 for Windows access so it doesn't really support permissions properly). I think it may be connected to this bug:

[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

which I'm also seeing.

Anyone got any suggestions on how I can proceed?

---

### Post by Krydahl on 2008-07-19
Bump??

---

### Post by Scunge on 2008-08-22
This may or may not work for you, because I haven't run with my change for long enough to see if other problems have arisen, and I don't know if this will break anything else in Hardy - anyone care to comment on that?

I use BackupPC and it uses ssh and rsync for it's backups. I had a machine using Ubuntu Dapper Drake 6.06.2 and all was well. I did an upgrade to Hardy Heron using the Update Manager and suddenly I kept getting "fileListReceive() failed" and no backups were being done.

I determined that ssh was still fine, so I guessed that it had to be something with rsync.

By doing ```
rsync --version
``` I saw that Hardy gave version 2.6.9, but on another machine still running Dapper it gave 2.6.6.

So I simply copied the rsync out of /usr/bin from the Dapper machine and replaced the one on the Hardy machine (after moving the existing Hardy version of rsync to a savefile, just in case), making sure it ended up with the same ownership and permissions as before.

Now BackupPC is happy again.

You could try doing a similar reversion of Hardy's /usr/bin/rsync to whatever was installed before you did your upgrade, but I repeat, I don't know if this will break something else in Hardy which might rely on v2.6.9.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Krydahl on 2008-08-22
Interesting. 

I'll have a look around and see if I can find an old copy to install, thanks.

---

