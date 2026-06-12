---
title: "Group permission problem"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by nkthomson on 2009-12-02
Hi,

I share a laptop with my gf and I've set up a folder /home/shared so we can share files.  It's owned by the shared group of which we are the only members.  However, when I create a test file in gedit it show as read-only in the group bit under Permissions.  I can set it manually but I thought files inherited the group permission when using SGID as I have done (see below)  Where am I going wrong?

drwxrws---  2 neil    shared  4096 2009-12-02 10:40 shared

---

### Post by ukripper on 2009-12-02
> **nkthomson said:**
> Hi,

I share a laptop with my gf and I've set up a folder /home/shared so we can share files.  It's owned by the shared group of which we are the only members.  However, when I create a test file in gedit it show as read-only in the group bit under Permissions.  I can set it manually but I thought files inherited the group permission when using SGID as I have done (see below)  Where am I going wrong?

drwxrws---  2 neil    shared  4096 2009-12-02 10:40 shared

 see these link [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

---

### Post by hardfire_avk on 2009-12-02
yup! write as line as umask=XXX at the end of your .bashrc file and it should work for you.

in your case XXX-> you may change it to 007, it may do the job. just check it out. if it works then add the same line to your gf's .bashrc file .

---

### Post by ukripper on 2009-12-02
i think better way for you to use ACL in this situation. See this thread [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

---

### Post by nkthomson on 2009-12-02
Thank you for your replies.  I'll work through them and let you know how I get on :-)

---

