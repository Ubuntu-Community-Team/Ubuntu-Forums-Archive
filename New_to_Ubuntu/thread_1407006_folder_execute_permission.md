---
title: "folder execute permission"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by degarb on 2010-02-14
I am reading the ubutunu pocket guide.  At first I think I understand execute permissions:  set for allowing someone to modify file containing info on file permissions.    but then they go into something with ability to see files if not set.  This, I don't get.  So, I guess based on this manual's explanation, I don't get it.

I also don't get why I can delete a file that is read only.

---

### Post by audiomick on 2010-02-14
Hallo.
The permissions system in Linux is actually elegantly simple.
Have a look here
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
perhaps reading a different explanation will make it clearer for you.

---

### Post by degarb on 2010-02-15
> **audiomick said:**
> Hallo.
The permissions system in Linux is actually elegantly simple.
Have a look here
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
perhaps reading a different explanation will make it clearer for you.

I understand all except execute for folder permission.

That page doesn't say much about execute.   But without a linux machine to play with today,  a glance at that page, seems to imply if read is turned off a user can cd folder but only see a blank folder, if execute is turned off, then cd folder would deny even entry into the folder.  

Am I right?

---

### Post by degarb on 2010-02-15
Changing topic a little.   The sticky bit seems to me like one of the most important attribute any folder can have.  Yet, seems an after thought.

So, can Nautilist set these?

---

### Post by vanadium on 2010-02-15
> a glance at that page, seems to imply if read is turned off a user can cd folder but only see a blank folder, if execute is turned off, then cd folder would deny even entry into the folder.
Am I right?
That is correct!

---

### Post by mcduck on 2010-02-15
Most importantly, a person with read access to a directory can access files inside that directory, as long as he knows the exact path & name for the file. But, like already mentioned, actually listing the contents of a directory requires execute permissions. This, for example, allows you to add music files located in your own home directory to other user's library in Rhythmbox while still keeping your home directory hidden from them.

What comes to sticky bit, that's not really something one would need too often. Most of the time you'll only really need the control you can get by properly using the user/group permissions.

Nautilus can handle all SUID, SGID and Sticky bits if you just set Nautilus to show advanced permissions in the Propertes-dialog. You can do that through gconf-editor, just enable the apps/nautilus/preferences/show_advanced_permissions -key..

---

