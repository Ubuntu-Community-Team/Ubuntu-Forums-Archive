---
title: "Shared folders option missing in Hardy - solution yet?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by wkoorts on 2008-09-18
Hi all,

Does anyone here know if a solid GUI solution has been created to address the missing "Shared Folders" option that was removed in Hardy?  It is described in the following thread:

[http://ubuntuforums.org/showthread.php?t=827101&highlight=share+folders+hardy](http://ubuntuforums.org/showthread.php?t=827101&highlight=share+folders+hardy)

If not then I'd like to create a GUI app to solve the sharing problem, via an app that can run into newer Ubuntu versions too.  I just don't want to spend the time on it if it's already been addressed in a generally accepted way.  I've done some searching here but couldn't find anything.

Would anyone vouch for such an app?  I'm thinking of a shared folder manager that will handle both SMB and NFS.

Regards,
Wayne Koorts
Registered Linux User #330079
[http://www.wkoorts.com](http://www.wkoorts.com)

---

### Post by rbc on 2008-09-18
In terminal, type shares-admin, or create a launcher with that command. That will give you Shared Folders. For an alternative, install system-config-samba. Then to use it, issue the command sudo system-config-samba. Oddly enough, it's a great way to set up shares, but unless I did something wrong, it will not show shares that were already created

---

### Post by wkoorts on 2008-09-18
So yes then.

-Wayne

---

### Post by rbc on 2008-09-18
Yeah. Sorry. I have had too much coffee today. Guess I could have simply said.....open terminal, type "shares-admin"

---

### Post by wkoorts on 2008-09-18
No worries, thanks for the reply :)

-Wayne

---

### Post by gregphil on 2008-09-19
Why not help them fix the long standing bug with ubuntu trying to browse authenticated Windows shares? (GUI browsing does not work in 8.04)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

In spite of the bug titles, the bug appears to apply to ALL authenticated shares from Windows machines, including basic peer-to-peer sharing.  

Smbtree and smbclient work fine, but GUI browsing such as the Nautilus network file browser fails.   kubuntu works just fine (it doesn't use the gnome gvfs library).  To be clear Nautilus CAN connect if you enter the entire path to the share, it just can't enumerate the shares available on the Windows machines if the shares require authentication (do not allow anonymous or "guest" access).

Someone needs to fix this......

---

