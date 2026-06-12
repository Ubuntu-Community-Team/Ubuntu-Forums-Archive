---
title: "How can files be shared between users?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Orwell on 2010-01-30
Hey guys,

Having never done it before, I just set up a user-profile for my wife and notice that 'as-is' she can't access what I have stored on the computer up until now. How can I grant her profile access to various locations/folders so as to avoid having to duplicate files across the two profiles? Eg. how can I allow a pictures folder, for example, to be accessed by both her and myself?

cheers! :D

---

### Post by chewearn on 2010-01-30
One way, under:
System > Administration >  Users and Groups

Set up so both Users share a same Group.  With that, both users has read access to the other's directories and files.

---

### Post by Orwell on 2010-01-30
> **chewearn said:**
> One way, under:
System > Administration >  Users and Groups

Set up so both Users share a same Group.  With that, both users has read access to the other's directories and files.
Cool...I've just done this, how can I now access the files now that I have both accounts in the same group?

---

### Post by woodmaster on 2010-01-30
how bout write access?

---

### Post by chewearn on 2010-01-30
> **Orwell said:**
> Cool...I've just done this, how can I now access the files now that I have both accounts in the same group?

Can't you navigate into the directories?  Once they share the same group, the Users should be able to see each other files.

---

### Post by Orwell on 2010-01-30
sweet...thanks a lot!

---

### Post by chewearn on 2010-01-30
> **woodmaster said:**
> how bout write access?

For write access, you need to change the permission of the respective files and directories.  By default, directories and files have 755 and 644 permission, respectively.  To allow group members to write, this need to be changed to 775 and 664.

For existing directory change it by:
```
chmod 775 /path/to/directory
```For existing files:
```
chmod 664 /path/to/file
```You can also right-click on the directories/files, select "Properties"; go to "Permission" tab, change Group "Access" to: "Create and delete" or " Read and Write".

---

For directories and files to be created, you need to change the default by using "umask".  The default umask for Ubuntu/Debian is 022, but to allow group write, we need 002.

```
umask 002
```To affect only single user, add the "umask" to ".bashrc" (in the user's home directory).  For system wide change affecting all users, edit the umask line in "/etc/profile" (probably the last line in the file).

---

