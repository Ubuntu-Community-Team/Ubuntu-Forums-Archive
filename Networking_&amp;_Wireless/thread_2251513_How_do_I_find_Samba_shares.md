---
title: "How do I find Samba shares?"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by mtmigs on 2014-11-04
I made the mistake of upgrading from 10.04 to 12.04 and now samba does not configure. It works. Any directory that was previously shared before the upgrade is still shared and I can access it. However, I wanted to change the configuration of which directories are shared and I cannot find it. I had "system-config-samba" installed from 10.04 and was able to add a directory share. But then I tried removing samba and reinstalling it and it wanted that package removed. But there are personal user directories shared which I cannot change. They are not stored in the smb.conf file.

---

### Post by bab1 on 2014-11-05
> **mtmigs said:**
> ...I tried removing samba and reinstalling it and it wanted that package removed. But there are personal user directories shared which I cannot change. They are not stored in the smb.conf file.
The Samba usershares are stored at ```
/var/lib/samba/usershares
```

These shares are the ones created by a user via the GUI interface.  They are simple text files and can be deleted by the the root user if you want to eliminate the Samba usershare.  It does not delete the data that is shared.

---

