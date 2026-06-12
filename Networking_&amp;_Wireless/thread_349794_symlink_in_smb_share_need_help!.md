---
title: "symlink in smb share? need help!"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by pelle.k on 2007-01-30
Hi all. This little "issue" is driving me nuts. I've asked this question on several forums, and on several irc channels. It seems noone can answer me, and i'm afraid this time will be no diffrent. :( But anyway, here it goes:

I got one computer called "pelle1". on that computer i have this share;
```
/home/pelle/share/read_only
```
in this share, i have a symlink called "files" to /mnt/files which is btw also owned by me. So you understand, it points outside the share. This is possible according to samba doc.

My desktop comuter is called "pelle2". on this computer //pelle1/read_only is mounted at;
```
/mnt/network/pelle1/read_only
```
The trouble is, i can't access /mnt/network/pelle1/read_only/files/

The thing is, I _can_ access this symlink if i go via smb:// (that is smb://pelle1/read_only/files/) in konqueror or nautilus. I can even access it with windows via //pelle1/read_only/files/. Why, oh why, can't i access it through the mountpoint when i mount it with either smbfs or cifs?

i user "security = share" in smb.conf, and i access this share with guest option in mount.
Help me, before i tear my hair off!

---

### Post by p!=f on 2007-01-30
I'm not sure at all where trouble could be... 
Just a few questions you already may answered. How is the share mounted? I mean, any parameters? Can you access it as root? What are local permissions of the share and /mnt/files?

---

### Post by pelle.k on 2007-01-30
this is the share i'm talking about. Nothing special. I access it as guest/user/root whatever.
```
[read_only]
comment = read only
path = /home/pelle/share/read_only
public = yes
writable = no
force group = pelle
force user = pelle
```
the directory /home/pelle/share/read_only on "pelle1" is owned by me (same user,pass,uid,gid), and so is /mnt/files.
them symlink is also owned by me.

on "pelle2" i own the folder /mnt/network/pelle1
this is how i mount it```
//192.168.1.111/read_only /mnt/network/pelle2/read_only cifs guest,ro 0 0
```

I have no problems whatsoever accessing the share itself, just follow symlinks when it's mounted at my filesystem, with cifs/smbfs. Have you done this yourself, or can anyone confirm this should be working (following symlinks in mounted share)?

[edit]i can not resolve these symlinks even as root, since /mnt/files (which the symlink points to at "pelle1") obviously doesn't exist on my "pelle2" filesystem. the links should be "translated" by samba, and directories created in /mnt/network/pelle/read_only[/edit]

---

### Post by p!=f on 2007-01-31
I can't access our lab servers from here but googling a bit gave me:
/etc/samba/smb.conf
```

follow symlinks = yes
wide symlinks = yes
unix extensions = yes/no #in some cases works with yes

```

> 
Samba server does not allow symlinks that refer to files
outside of the share, so in Samba versions prior to 3.0.5, most symlinks to
files with absolute paths (ie beginning with slash) such as:
         ln -s /mnt/foo bar
would be forbidden. Samba 3.0.5 server or later includes the ability to create
such symlinks safely by converting unsafe symlinks (ie symlinks to server
files that are outside of the share) to a samba specific format on the server
that is ignored by local server applications and non-cifs clients and that will
not be traversed by the Samba server).  This is opaque to the Linux client
application using the cifs vfs. Absolute symlinks will work to Samba 3.0.5 or
later, but only for remote clients using the CIFS Unix extensions, and will
be invisbile to Windows clients and typically will not affect local
applications running on the same server as Samba.


Hope it helps or at least points you further.

---

### Post by pelle.k on 2007-01-31
thankyou for your reply. i did acctually know that., and it seems to nave no effect on my problem. I'v also tried to mount this share with "security = user", and use the same user who owns everything on that share, including what the symlink points to.

I've been at this problem about three (!) full days now. I'm not keen on giving up, but this time i'm really exhausted.

Just to be perfectly sure, does _anyone_ know if this really can be done. Is this really a feature that the cifs VFS can provide, or am I chasing a non existent rabbit?

---

### Post by pelle.k on 2007-02-07
Well, i found out how to do it. You have to set "unix extensions = no" in smb.conf. Strange, but it does work. (you loose all file owner/group/security setting though...) You'll have to set them manually when mounting the share, if you wan't some sort of masking.
I'm sooo the king of not giving up. :)

---

