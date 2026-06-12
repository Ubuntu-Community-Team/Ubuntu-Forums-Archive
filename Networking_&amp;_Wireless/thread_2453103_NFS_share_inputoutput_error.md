---
title: "NFS share input/output error"
date: 2020-11-03
forum: Networking &amp; Wireless
---

### Post by kruemelprinz on 2020-11-03
Hi
I have an old NAS running debian 7 (no updates for the CPU architecture available) and tried to set up a NFS share so I can access server side folders from my kubuntu laptop. Server side is running NFS v4.
Added the following line to my /etc/exports on the server side
```
[FONT=monospace][COLOR=#000000]/home/storage           192.168.1.*(rw,sync,all_squash,anonuid=1000,anongid=1000)[/COLOR]
[/FONT]
```
And mounted the share from the client side to /nfs/b3server/
```
[FONT=monospace][COLOR=#000000]sudo mount 192.168.1.xxx:/home/storage /nfs/b3server/[/COLOR][/FONT]

```
and made the following entry to my client /etc/fstab
[FONT=monospace][COLOR=#000000]```
192.168.1.50:/home/storage /nfs/b3server nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

```[/COLOR]
[/FONT]I can access and browse the folders and was able to copy files to from the client to the server without problems and also delete files on the server side, however I cannot open or copy any file from the server to the client.

Example:
```
[FONT=monospace][COLOR=#54ff54]**me@mysystem**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cp /nfs/b3server/music/rsync.sh ~/Downloads/ [/COLOR]
cp: cannot open '/nfs/b3server/music/rsync.sh' for reading: Input/output error
[/FONT]
```

What am I doing wrong?

---

### Post by TheFu on 2020-11-03
NFS Server /etc/exports:
```
/TV     regulus(rw,async,root_squash)
```

/etc/fstab on the client (I actually use autofs):
```
istar:/TV  /TV    nfs   proto=tcp,intr,rw,async  0 0
```

regulus and istar are in the local DNS, so they resolve.  You can use IP addresses.

Restart the nfs-server on the server-side after any change to the exports.
Reload the fstab using  **sudo systemctl daemon-reload** whenever the fstab is modified, thanks to systemd.

From a client:
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
istar:/TV                         nfs4  294G  101G  193G  35% /TV
```

Both systems are running ubuntu 16.04, but 18.04 and 20.04 clients are working too.

Ensure the uid and gid numbers all match between all the clients and the server for the users. In theory, there's a way to setup NFS uid mapping. My attempts to use that about 8 yrs ago failed. Maybe it works today, but IDK.

---

### Post by kruemelprinz on 2020-11-05
Thanks for your description. I have tried your settings, but the issue remains.
To specify my problem a little more in detail:
I  can copy files from the client to the server. However, the same files  from the same client cannot be copied back or opened. So even if there  were uid/gid issues, in theory, the user that has created the copy on  the server should be able to access them - but they aren't.
The same applies to all other files that have been copied from my earlier computer (Mac) using the afs protocol.

---

### Post by SeijiSensei on 2020-11-05
Any interesting messages in /var/log/syslog?

---

### Post by TheFu on 2020-11-05
**nfsiostat**  and  **nfsstat** may be useful. I don't know how.

---

### Post by kruemelprinz on 2020-11-05
> Any interesting messages in /var/log/syslog?

Nothing interesting on the server side.
On the client side I found 

```
Nov  5 19:18:56 kubuntu-me nfsidmap[2180122]: nss_getpwnam: name 'squeezeboxserver' not found in domain 'localdomain'
Nov  5 19:18:57 kubuntu-me nfsidmap[2180124]: nss_getpwnam: name 'xyz' not found in domain 'localdomain'
```

---

