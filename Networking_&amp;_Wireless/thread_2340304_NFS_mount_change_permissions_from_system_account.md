---
title: "NFS mount change permissions from system account"
date: 2016-10-17
forum: Networking &amp; Wireless
---

### Post by dragonflight on 2016-10-17
NFS on 14.04/16.04 seems to treat system accounts differently than user accounts wrt permissions on files.

It seams a daemon (system uid) cannot change permissions on a file even though it owns the file, though a user account can.

Specifically I'm trying to use deluged (UID debian-deluged) running in a virtualbox client to download a file to an NFS mount, execute a script which then changes the group (so others can access it) and then move the file.

This works fine if the file is not an NFS mount.

I verified the problem by logging into the system account (su -s /bin/bash debian-deluged) and sure enough I can't change the permissions on files it creates.
If i create a new non-system account it has no problem changing the group on files it creates.

Additionally it seams that NFS does not follow group permissions. i.e. the system account is a member of the group torrents and a directory  is owned by a random user, group torrents and permission 770 then the system account can't access the directory.
Only if the file is owned by the system account (or permission are 777) can the system account access the directory.

I can live with the second restraint (i.e. make all directories owned by debian-deluged), but can't seem to get around the first.
Is there a way to make this work other than making debian-deluged a non-system account?
Does anyone know what attribute of the account is NFS looking at (e.g. the uid or some other attribute)

thanks
mike

---

### Post by TheFu on 2016-10-17
Welcome to the forums.

If you want to shoot yourself in the head, no_root_squash is there for the nfs exports file.  It is usually (almost always) a bad idea to let root write to NFS storage, but feel free. The gun is there. Aim it and pull the trigger.

Running a bt program as root - foolish, IMHO.  Use any other account you like, just not root. Please. There are many reasons for this.

BTW, **man exports** explains more info on nfs export options.

---

### Post by dragonflight on 2016-10-18
I agree I do not want to run the daemon as root. In fact security ( a little) is the reason it is run as a user with no login. By default, and by convention, such things are run by "system accounts" with very few privileges.
I have not been able to find any reference to system accounts being treated differently by nfs, but they are and root_no_squash (which I do have enabled) only refers to root (I have no problem with root_no_squash as it is a mount that only temporarily stores partial and completed torrents)

I may have over complicated the question by saying why I wanted to change permission but perhaps the following is simpler.

Two users test (UID 1001) and debian-deluge (UID 116), both members of the group torrents, file system /torrents is exported with (in /etc/exports):
        /torrents    172.16.2.0/24(rw,sync,no_root_squash,crossmnt)
and mounted with (as described by mount):
       router3:/torrents on /x type nfs (rw,vers=4,addr=172.16.2.3,clientaddr=172.16.2.243)

```
root@m:/x/dir# ls -ld .
drwxrwxrwx 2 deluge deluge 30 Oct 18 09:03 .
root@m:/x/dir# su -s /bin/bash test
test@m:/x/dir$ groups
test torrents
test@m:/x/dir$ touch a
test@m:/x/dir$ chgrp torrents a
test@m:/x/dir$ exit
root@m:/x/dir# su -s /bin/bash debian-deluged
debian-deluged@m:/x/dir$ groups
debian-deluged torrents
debian-deluged@m:/x/dir$ touch b
debian-deluged@m:/x/dir$ chgrp torrents b
chgrp: changing group of ‘b’: Operation not permitted
debian-deluged@m:/x/dir$ ls -la
total 4
drwxrwxrwx  2 deluge         deluge           22 Oct 18 09:01 .
drwxrwxrwx 22 deluge         test           4096 Oct 18 08:51 ..
-rw-rw-r--  1 test           torrents          0 Oct 18 09:01 a
-rw-rw-r--  1 debian-deluged debian-deluged    0 Oct 18 09:01 b
debian-deluged@m:/x/dir$ echo hi >>a
bash: a: Permission denied
```

as you can see the system account couldn't change permissions of b, nor write to the file a even though it owned b and had group permissions on a, but the non-system user could

mike

---

### Post by TheFu on 2016-10-18
On both machines, run 'id' for both accounts and post the output, please.  That will be 4 commands total.

What is the diff between deluge and debian-deluged?

---

### Post by dragonflight on 2016-10-18
damn you're right

Last question first deluge is the primary user account and debian-deluged is the automatically created system account for the deluge daemon.

I had considered the problem with mismatched uids and had created the account test to be a unique uid - it isn't and it by chance was a member of the group torrents (which is the same across machines).
So (and I am only surmising) the surprising behaviour is because the NFS client doesn't do the authentication, so though debian-deluged is a member of torrents, the same uid (sshd as it turns out) is not.

I still don't understand if chgrp doen't work how did the NFS client create a file with the gid debian-deluged that doesn't exist on the server (and so sshd is not a member of it)

Anyway, now I have to pick a unique system id for deluged and change both system accounts (and files)

thanks
mike

---

### Post by TheFu on 2016-10-18
So you won't be posting the requested output?

---

### Post by dragonflight on 2016-10-18
Sorry, I didn't think it was necessary, and I'm not sure exactly what you want, but for what its worth:

machines@router3:/torrents/dir$ ls -ln .
total 4
-rw-rw-r-- 1 1001 1002 0 Oct 18 09:01 a
-rw-rw-r-- 1  116  125 0 Oct 18 09:01 b
-rw-rw-r-- 1  116  125 3 Oct 18 09:03 q


on the client
test1@m:/x/dir$ id test
uid=1001(test) gid=1001(test) groups=1001(test),1002(torrents)
test1@m:/x/dir$ id debian-deluged
uid=116(debian-deluged) gid=125(debian-deluged) groups=125(debian-deluged),1002(torrents)

on the server
machines@router3:/torrents/dir$ ls -l .
total 4
-rw-rw-r-- 1 machines torrents 0 Oct 18 09:01 a
-rw-rw-r-- 1 sshd     ntp      0 Oct 18 09:01 b
-rw-rw-r-- 1 sshd     ntp      3 Oct 18 09:03 q
machines@router3:/torrents/dir$ id debian-deluged
uid=121(debian-deluged) gid=1002(torrents) groups=1002(torrents)
machines@router3:/torrents/dir$ id machines
uid=1001(machines) gid=1001(machines) groups=1001(machines),128(vboxusers),1002(torrents)
machines@router3:/torrents/dir$ id sshd
uid=116(sshd) gid=65534(nogroup) groups=65534(nogroup)

also I did create a non-system user test1 that had no counterpart on the server and it behaved like the system account i.e. the problem had nothing to do with system accounts

---

