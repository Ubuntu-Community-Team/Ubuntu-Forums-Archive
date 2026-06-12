---
title: "SMB permissions - file owned by nobody"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by stephenjbarr on 2007-11-09
Hello,

I have a laptop and a desktop both running gutsy. I have smb working between them. However, when I am using the laptop, which is mounting a drive on the desktop, when I create a file on the share, from the perspective of the desktop, it is owned by nobody and I can't edit it.

How can I make it so when I create files on the laptop I can edit them immediately on the desktop machine?

thanks,
-Stephen

---

### Post by BoneKracker on 2007-11-10
You can have the system assign the files to a group to which the editing user belongs.

You can achieve this a couple of ways:

a) You can have samba create the file with world-writable permissions.  Depending on the nature of the files and your security situation, you may not want to do this.  As a rule of thumb, world-writable files are a bad thing.  As a practical matter, when access to them is otherwise limited to a single user or a trusted group of users, world-writable files are fine.  To have samba add files to the share with world-writable permissions, set the share up like this (in your smb.conf file):
```
[shared_local]
        comment = Shared Files (Local Windows Network)
        path = /srv/samba/shared
        read only = No
[B]        create mask = 0666
        directory mask = 0777[/B]
        guest only = Yes
        guest ok = Yes
        hide unreadable = Yes
```
The lines "create mask" and "directory mask" are the pertinent lines.  The rest of the configuration for the share depends how you are settng it up and are only provided for context.

Note: the default Samba create mask is 0744 (world-readable, but not writable).  That's why you couldn't edit the fle without using sudo.

b) You can do something similar, but have samba create the files so they're not world writable but only owner and group writable.  Do the same as above but the masks should be:
create mask = 0660
directory mask = 0770

Then, you need to make sure the user you want to be able to edit is either the owner or a member of the group.  A good way to do this is to have the files owned by root and some group to which you can assign your user (you can create a group called, for example, "docs" or you could use a preexisting group like "users").  

To force the system to apply this ownership, you make the directory "sticky".  Lets say your samba share is located at "/srv/samba/shared" for example:```
sudo **chown root:docs** /srv/samba/shared
sudo **chmod 1770** /srv/samba/shared
```
Now any file or directory created in /srv/samba/shared will be owned by root and assigned to group docs; and it will have permissions rw-rw---- (for files) and rwxrwx--- (for directories).  This technique is also commonly used to make sure that all files going into the /tmp directory of a Linux system are owned by root and are world-writable; to see if that's the case on your system, type "stat /tmp" at the command line and look for "Access: (1777/drwxrwxrwt)".  You can do the same to check if you successfully made your samba share "sticky".

c) If you're the only user of the share in question, you could do a variation of (b) but assign the editing username as the owner or the group (if on your system the username is also the user's primary groupname), or both.

---

