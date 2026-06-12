---
title: "Access control NFS shares"
date: 2022-02-23
forum: Networking &amp; Wireless
---

### Post by zkab on 2022-02-23
I have mounted NFS Shares in my Ubuntu computer where the NFS server runs in a Synology NAS.
It works OK except for permissions.
Since Synology runs BSD they have a different view of user&group ID:s
When I checked the mounted shares from my Ubuntu they have following:

Ownership:
owner    group
1026     systemd-journal
1030     users

Access Cotrol:
View and modify foder content (owner, group)

Therefore I don't get write access since my Ubuntu users have the usual owner&group ... 1000&1000, 1001&1001 ...
What is the best solution ... I can't control the NAS.

---

### Post by TheFu on 2022-02-23
Actually, BSD and Unix and all Linux systems have exactly the same POSIX permissions model.  permissions, ownership and groups all work exactly the same.

A quick google says to use **synouidmod**.

What is likely different are the userids and groupids on each of the systems.  So, you'll need to make the uid/gid match across all the systems using NFS.

I find it very hard to believe that a NAS device has that limitation. Look up how the vendor says to solve this issue. I'd start with that.

If you cannot modify the NAS with admin control, the only option is to change your client-side uids/gids.  This is actually pretty easy for experienced admins who can work quickly from a non-GUI login.  Only a few file contents need to be modified.  The passwd db and group db need to be changed, unless you are using LDAP for centralized user control.  Modifications to those files are nearly immediate after write, so you'll want to make backups before starting. For example, sudo cp passwd passwd-before.  Do that for each of the files, respectively.  Then open a root shell (sudo -i) and create new files with the changes you want to the uid/gid as needed for both files. These are simple text files with manpages spelling out what each field means. Save the new files to temporary locations, since you'll want to activate all of them at the same time using a little cp script.  
cp /tmp/passwd /etc/passwd
cp /tmp/group  /etc/group

If you don't get the changes correct everywhere, things will break. Details matter.  Hopefully, you realize that the uid and gid matching in Ubuntu are purely coincidence, nothing more.

After making the changes, you'll need to find all the local files owned by each userid and do a chown to the new userid for them. May want to keep a list of those files for use in the gid change too, though I've left changing the group to the user's afterward.  The 'find' command has an option to locate files by uid. I'd use that and just work through all the impacted users.

There is no validation for any of these changes. If the admin gets something wrong, it could be bad or funny. Just depends on the error.

But I'd start with looking up what the NAS vendor says for how to handle this.  It is possible that they allow remote root control of files.  Eeeew.  I feel dirty just thinking about that, but for a NAS, there may not be much choice.

Owners of a directory can do anything to the permissions and groups for everything below. It may require copying things to gain access.

If you have some storage that you want multiple users to all share read-write access inside, then those userids need to be put into the same group and the group needs to be set on every directory with a setgid bit. This will keep the group for each new object created to the same as the directories.  Existing files/directories with other groups don't magically change, so if there is already files/directories there, the owner of the files will need to chgrp on everything and chmod g+s on all the directories.

---

### Post by zkab on 2022-02-23
Thanks for the exhaustive answer ... I will check what the NAS vendor says

---

