---
title: "mount samba: some do, some don't"
date: 2022-08-30
forum: Networking &amp; Wireless
---

### Post by dgermann on 2022-08-30
Friends--

Have been working all day on this puzzle and not getting my samba shares mounted.

Here is the /srv directory on bach:```

doug@bach:~$ ls -alh /srv
total 28K
drwxr-xr-x  7 root root     4.0K Aug 30 15:12 .
drwxr-xr-x 23 root root     4.0K Aug 12 13:20 ..
drwxr-xr-x  5 root root     4.0K Aug 26 14:52 apps
drwxr-xr-x 35 root root     4.0K Aug 29 19:45 backups1
drwxr-xr-x  4 root root     4.0K Aug  4 22:46 current
drwxrws--- 29 doug personal 4.0K May 23 21:22 personal
drwxr-xr-x  2 root root     4.0K Aug 30 15:12 test
doug@bach:~$ sudo lsattr /srv
[sudo] password for doug: 
--------------e------- /srv/current
--------------e------- /srv/apps
--------------e------- /srv/test
--------------e------- /srv/backups1
--------------e------- /srv/personal
```

I have tried to mount these shares from 4 different clients, two are 22.04.1, and two are 18.04.6. On each of these clients I can mount current and /apps, but not the other directories.
```
doug@wind:~$ sudo mount -vvv /sam/personal/
[sudo] password for doug: 
mount.cifs kernel mount options: ip=192.168.0.205,unc=\\bach\personal,nobrl,uid=1000,gid=1000,user=doug,pass=********
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

doug@wind:~$ sudo dmesg -T
[Tue Aug 30 17:48:56 2022] CIFS: Attempting to mount \\bach\personal
[Tue Aug 30 17:48:56 2022] CIFS: VFS:  BAD_NETWORK_NAME: \\bach\personal
[Tue Aug 30 17:48:56 2022] CIFS: VFS: cifs_mount failed w/return code = -2

root@wind:~# smbclient -L bach
Password for [WORKGROUP\root]:

	Sharename       Type      Comment
	---------       ----      -------
	apps            Disk      
	current         Disk      
	IPC$            IPC       IPC Service (bach server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available
```

The relevant part of the fstab look like this:
```
//bach/personal	/sam/personal	cifs	rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=doug	0	0
//bach/apps    /sam/apps       cifs    rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=apps	0	0
//bach/current    /sam/current       cifs    rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=data	0	0
```

Looking at these it appears to me the problem lies with the server. But I don't know what to do to mount these other shares.

What should I try next, please?

Thank you!

---

### Post by TheFu on 2022-08-30
Don't use ACLs. Use normal Unix permissions.  Those are displayed using 'ls -al'

What is the client and what is the server?  OS, samba versions?
Also, using root as the connection is something I've never, ever seen on Ubuntu or Linux.  Samba is end-user to Server storage connection. If you want system to system storage that can be shared by all users, use NFS instead.

If you want to access files in your HOME directory, use the [homes] stanza that is part of samba.  The HOME directory for each user needs to be owned by the user (not root).


On the samba server, /etc/samba/smb.conf contents look something like this:
```

... 
[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```

The default Global section settings should be fine.
And lastly, smbpasswd needs to be run to create samba useraccounts that map to the Unix usernames and set the password.
```
$ sudo smbpasswd -a thefu
```
Don't forget that part.

On the client side, almost any file manager can be used to connect to the //{hostname}.local/{username}.  If that doesn't work (avahi isn't running, use the DNS name or IP address of the server.


Looking at your mount options, "mand" isn't in the manpage for my mount.cifs. I've never seen it before.  What do the system logs say when you attempt to run "sudo mount -a"  I bet there are errors.

I've jumped all over. Sorry.  First, don't use root.  Ubuntu isn't meant to use root for stuff like this, except to restart daemons.  If you want storage to be available system-wide, use nfs.

---

### Post by dgermann on 2022-08-30
@TheFu--

TheFu has the clue! (As I have learned.)

Thank you! You gave me what I needed. When I added two stanzas to the server's /etc/samba/smb.conf file, one for [test] and one for [personal], and restarted samba thus:
```
sudo service smbd stop
sudo service nmbd stop
sudo service nmbd start
sudo service smbd start
```

Everything worked!

Thank you for allowing me to sleep tonight, TheFu!

---

### Post by TheFu on 2022-08-31
For sharing storage between Unix-like OSes (Unix, MacOS, Linux, BSD), use NFS on the LAN.  It is the native way and faster than CIFS. CIFS is a hack.

---

### Post by dgermann on 2022-08-31
@TheFu--

I know you prefer NFS. I started out with cifs in about 2006, so I have thousands of files on it, and am afraid I will break it all if I switch now. (One issue is file locking: if one person is editing a file, others are locked out from editing.)

Thanks!

---

### Post by TheFu on 2022-08-31
> **dgermann said:**
> @TheFu--

I know you prefer NFS. I started out with cifs in about 2006, so I have thousands of files on it, and am afraid I will break it all if I switch now. (One issue is file locking: if one person is editing a file, others are locked out from editing.)

Thanks!

NFS has flockd which can be controlled to provide exclusive access.
The way a file is shared on a network doesn't matter. Use both CIFS and NFS, if you like. No harm.  They are completely unrelated.
[https://www.rfc-editor.org/rfc/rfc7530.html#section-1.4.5](https://www.rfc-editor.org/rfc/rfc7530.html#section-1.4.5)
```
1.4.5.  File Locking

   With the NFSv4 protocol, the support for byte-range file locking is
   part of the NFS protocol.  The file locking support is structured so
   that an RPC callback mechanism is not required.  This is a departure
   from the previous versions of the NFS file locking protocol, Network
   Lock Manager (NLM) [RFC1813].  The state associated with file locks
   is maintained at the server under a lease-based model.  The server
   defines a single lease period for all state held by an NFS client.

   If the client does not renew its lease within the defined period, all
   state associated with the client's lease may be released by the
   server.  The client may renew its lease by use of the RENEW operation
   or implicitly by use of other operations (primarily READ).
```

But it is your system.

I like NFS over CIFS because it honors the native Unix permissions model and performance is good.  I've used samba and found it frustrating when permissions were on a 'mount' level, not file level.  But we all have different needs.

---

