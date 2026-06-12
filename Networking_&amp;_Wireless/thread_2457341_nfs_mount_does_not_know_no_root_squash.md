---
title: "nfs mount does not know no_root_squash?"
date: 2021-01-31
forum: Networking &amp; Wireless
---

### Post by ch.treczoks on 2021-01-31
Hi!

I have an NFS share on an ubuntu based server, listed in /etc/exports as:
[INDENT][FONT=monospace][COLOR=#000000]/data/Backup   192.168.0.2(no_root_squash,rw)[/COLOR]
[/FONT][/INDENT]
[FONT=monospace]
On my other machine, I can successfully mount it with:
[INDENT][FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]mount 192.168.0.3:/data/Backup /var/lib/autobackup -tnfs -onfsvers=4.0,rw[/COLOR]
[/FONT][/FONT][/FONT][/INDENT]
It mounts, my user can access it, but this does not give root access to the share (as expected).
But if I try to use this instead:
[INDENT][FONT=monospace][COLOR=#000000]mount 192.168.0.3:/data/Backup /var/lib/autobackup -tnfs -onfsvers=4.0,rw,no_root_squash[/COLOR]
[/FONT][/INDENT]
[FONT=monospace]Then mount balks at the "no_root_squash" option.
[/FONT]
I am aware that there is a security risk involved here. But I have no idea how to fix it, as the backup agent must be root to access the files it wants to backup (it needs, among others, access root-owned files here).

As far as I know, the no_root_squash option is old as time - I've used it literally decades ago. Why is it no longer available?

What can I do to give root on the client side access to the nsf share?
[/FONT]

---

### Post by TheFu on 2021-01-31
NFS clients don't get to tell NFS servers about root_squash options.

BTW, I've never seen -tnfs -onfsvers=4.0 options, so it is likely failing silently.

Humor me, try:
```
sudo mount -t nfs     -o rw,proto=tcp,intr    192.168.0.3:/data/Backup     /var/lib/autobackup
``` 
Use that order, spacing and those exact options.

Please.

I've never needed to force NFSv4. It is automatic on Ubuntu 16.04 and later.
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/d/D1                     **nfs4**  3.5T  3.5T   23G 100% /d/D1
```


Can I ask the purpose of this?  Using NFS as a target for backups is a poor security choice. It is best to have the backup server "pull" the backups and not use any networked file system tools. If a client gets a crypto-locker malware, bam, all the backups can be encrypted too. Or just deleted.  "Pull"ed, versioned, backups mitigate that issue.

---

### Post by ch.treczoks on 2021-02-01
> **TheFu said:**
> NFS clients don't get to tell NFS servers about root_squash options.
I've done this for machine generations, actually. The server needs to grant it, or it won't work, but "root_squash" was always mount default regardless of the server settings, so to actually invoke this option, it had to be named on the command line. I have not used this since I started with Ubuntu in '18, but I've used this client option with SuSE and RedHat before that time according to my backups.


> **TheFu said:**
> BTW, I've never seen -tnfs -onfsvers=4.0 options, so it is likely failing silently.
I can assure you, they work fine.

> **TheFu said:**
> Humor me, try:
```
sudo mount -t nfs     -o rw,proto=tcp,intr    192.168.0.3:/data/Backup     /var/lib/autobackup
``` 
Use that order, spacing and those exact options.

Just to humor you, I will. It won't make a difference, though. BTW, "intr" is default anyway, and "proto=tcp" is NFS version 2 or 3, not 4, but ignored silently.

> **TheFu said:**
> Please.

> **TheFu said:**
> I've never needed to force NFSv4. It is automatic on Ubuntu 16.04 and later.
OK, That's new to me. I've always used it since I started to use V4.

> **TheFu said:**
> Can I ask the purpose of this?  Using NFS as a target for backups is a poor security choice. It is best to have the backup server "pull" the backups and not use any networked file system tools. If a client gets a crypto-locker malware, bam, all the backups can be encrypted too. Or just deleted.  "Pull"ed, versioned, backups mitigate that issue.
First of all, this is a local network thing, so the usual attacks on file system mounts are as difficult as I can make them. Second, there is a script (that needs to run as root for a number of reasons) on the client that gathers all the data into that backup directory in it's own smart way, nearly impossible to replicate over the network in a way that would not seriously waste resources. Third, the data in the /data/Backup is taken by the server and stored in a version controlled backup system outside the /data/Backup directory. The /data/Backup is only a temporary storage.

---

### Post by SeijiSensei on 2021-02-01
Just the other day someone posted here with a similar problem. Turned out it was because there were no "fsid" entries in /etc/exports, which NFSv4 seems to require.
```

/home           192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)
/media/external 192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=1)

```

---

### Post by ch.treczoks on 2021-02-01
> **SeijiSensei said:**
> Just the other day someone posted here with a similar problem. Turned out it was because there were no "fsid" entries in /etc/exports, which NFSv4 seems to require.
I added the fsid entries (which are not really well documented, or I'm to stupid to google them), and things did change - in a way.
I had found other NFS issues here before I posted, but somehow I missed the one you probably referred to. The fsid keyword did help the search greatly.

The /etc/export on the server:
```

[FONT=monospace][COLOR=#000000]/export 192.168.0.2(fsid=0,no_root_squash,rw,no_subtree_check) [/COLOR]
/export/Backup 192.168.0.2(fsid=1,rw,no_root_squash,no_subtree_check)

```
I've added the "no_subtree_check" for testing. Documentation states that this improves reliability, and the added security risks are acceptable.
I had "insecure" added, too, but I didn't need it, so I removed it again.
I've moved the export path from /data/Backup to /export/Backup which, using -tnfs4 and fsid, seems to be required/correct/whatever.

Now it works - in an unexpected way. The "no_root_squash" option to mount is still unknown, but it seems to honor the "no_root_squash" option given by the /etc/export config without explicit request.



[/FONT]

---

### Post by SeijiSensei on 2021-02-04
"no_root_squash" is only a server-side option. There is no client-side equivalent since that would grant too much control to the client.

---

