---
title: "pam_mounted cifs home directory =&gt; unusable..."
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by clavetika on 2008-11-21
Hi everyone,
    I've spent quite some time working on this problem now, and was wondering if anyone had seen it before / had any ideas as to how I could go about fixing it.
    Essentially, I have a Hardy box that enumerates non-local users with LDAP (pam_ldap), and then mounts their home directories off of a NAS via pam_mount. Everything's working great, except for the fact that there appears to be something wrong with the way pam_mount is mounting the directories. The NAS is mainly for serving Windows boxen, but has Samba (I'm using cifs as the fs type when mounting...). I have read and write access to the mounted directory, its contents are owned by me (I gave uid=%(USERNAME),gid=users in pam_mount.conf.xml ...). However, when logging in through GDM, Firefox's awesome bar doesn't work, neither does history. OpenOffice won't even start. Both of these would indicate to me that I didn't have write permissions, but I do... it's very confusing. Bash even highlights the directories and files in the mounted directory differently. 
     Hopefully I've made some sense in my description above... anybody have any ideas? Could it be the way Samba is configured on the NAS? Maybe I'm missing an option in the pam_mount config? I have no idea where these permissions problems could be coming from....

Thanks a lot :)

---

