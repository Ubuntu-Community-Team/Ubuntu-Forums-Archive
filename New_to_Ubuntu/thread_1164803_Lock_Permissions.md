---
title: "Lock Permissions"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by shoaibi on 2009-05-20
How can i lock permissions on a dir so that every item created inside that dir has those perms, owner and group?

Explanation:

drwxr-xr-x 12 shoaibi staff 4096 2008-12-11 15:11 management

Now this is a public share on my system using NFS and samba. Users can create dirs and files inside it. What i want is that every file (coz dir is also a file) created under this subtree should always have 755 and owned by shoaibi:staff.

I know about setuid and setgid, but i want bit more than that. Any ideas what could help me here?

---

### Post by asmoore82 on 2009-05-20
> **shoaibi said:**
> How can i lock permissions on a dir so that every item created inside that dir has those perms, owner and group?

Explanation:

drwxr-xr-x 12 shoaibi staff 4096 2008-12-11 15:11 management

Now this is a public share on my system using NFS and samba. Users can create dirs and files inside it. What i want is that every file (coz dir is also a file) created under this subtree should always have 755 and owned by shoaibi:staff.

I know about setuid and setgid, but i want bit more than that. Any ideas what could help me here?

Your question is somewhat of paradox,
x should never be set on a file unless it is a binary executable or shell script

Another paradox: if 755 are the perms on the folder Users other than shoaibi
cannot create dirs and files inside it.
This paradox goes deeper, if 755 is to be automagically set on all folders created,
Users other than shoaibi will be unable to create dirs and files inside those subdirectories as well

I believe what may be closer to what you wish is a "sticky" rwxrwxr-x directory:
```
chmod 1775
```
this creates a more secure public area where users can create new files freely,
but users cannot mangle each others files.
Even then, though, files will still be owned by their creator.

I understand what you are seeking, but it is at odds
with the fundamental purpose of file ownership.

Keep in mind that he who is trusted to create files and subfolders
is able to delete them as well, unless "sticky" directories are enforced.

---

### Post by shoaibi on 2009-05-20
1st: 
okay for files let it be 664
2nd:
i thought one would understand that i am using squash all in nfs and guest account = shoaibi in samba.
 So anyone who can mount the share, do anything.
(yes, by squashing any files created any nix hosts will be under my name, but what about windows systems? specially a shortcut made using windows system has 000 permissions and root:root)

Plus i want everyone to add/edit/delete any files, think of it as a movie share.

---

