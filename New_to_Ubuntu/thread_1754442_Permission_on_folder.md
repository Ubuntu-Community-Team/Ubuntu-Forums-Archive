---
title: "Permission on folder"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Bendb on 2011-05-10
Hello,

I'm struggling about the permissions to go to a folder.
I have a user nagios that should be able to go into the folder "test"

drwxr-x------ 12 root bla 4096 Jul 29 2010 test

The user nagios is in my group bla, but it still doesn't let me get into the folder if i'm navigating with the user nagios ...

Thnx for the replies!

---

### Post by garvinrick4 on 2011-05-10
sudo chown -R nagios:blah /path to test

---

### Post by deconstrained on 2011-05-10
If the path is a filesystem's mountpoint, you may have to specify the mode/ownership in the mount options.

---

### Post by Bendb on 2011-05-10
Hai,

Thanks for the replies.
I wasn't allowed to set nagios as the user. But it's fixed now ;)

Forgot to log out and in again with nagios #-o
I can navigate to the map now.

Thanks!

---

