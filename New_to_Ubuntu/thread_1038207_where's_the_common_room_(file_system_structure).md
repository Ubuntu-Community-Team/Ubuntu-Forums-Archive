---
title: "where's the common room? (file system structure)"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by ibid49 on 2009-01-12
This is a "where should I" rather than a "where can I" question.  If I have a directory whose contents are intended to be shared by all users, where is the expected location for that?  /var?  /etc?

I'm coming from windows, and I'm just unfamiliar with the directory structure and what each top level directory is intended for.  I don't want to be creating a file server and storing all the miscellaneous files in with all the system files, for example.

I realize I could just create a directory in my own ~ directory and set permissions for anyone else, but that doesn't seem right as these files are not supposed to be designated as mine.  Is there a normal place for files that are shared by everyone?  There's gotta be, right?  Or is that windows thinking and I just need to change my mindset?

---

### Post by taurus on 2009-01-12
Most popular place/location is in /media, i.e. /media/share.  You can always mount it to /mnt--/mnt/share.

---

### Post by steveneddy on 2009-01-12
You also may look in the 

**/usr/share/**

folder. If you are trying to share program access, this is where I would look.

---

### Post by cmnorton on 2009-01-12
It's really up to you.

Using sudo (becoming root), you could create a sandbox area at the root directory. You would then need to give the appropriate permissions on that directory. like 777 or 755 (read only).

You could also create a user called sandbox, and let all your users have group write privs, but you would also have to protect /home/sandbox 775, so that group users could write files in this directory (/home/sandbox), unless this is a read-only area. And, you would have to make sure your users are added to the sandbox group.

---

