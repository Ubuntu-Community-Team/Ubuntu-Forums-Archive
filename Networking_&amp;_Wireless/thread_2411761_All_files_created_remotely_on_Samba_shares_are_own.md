---
title: "All files created remotely on Samba shares are owned by &quot;Nobody&quot;"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by jasonjason2 on 2019-02-03
good afternoon,

i am running Samba 4.7.6-Ubuntu on 18.04LTS.

goal is to have a single mounted drive, with users able to read/write/execute files within folders they own, and to have read only permissions for files in folders they do not own.

to accomplish this, i have a drive shared in the following *SMB.conf*

```
[public]
  comment = public anonymous access
  path = /media/media/
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes
```

this works correctly, except that every file created is assigned "nobody" as the owner. 

**how do i assign the connected user as the owner to remotely created files?**

following this advice : [URL="https://superuser.com/questions/562092/samba-files-written-to-public-share-belong-to-nobody"]https://superuser.com/questions/562092/samba-files-written-to-public-share-belong-to-nobody
[/URL]
i added
```
[global]
guest account = %u
```

samba would not restart after making the changes, so it must not be correct application of the %u variable

am i missing something on my conf file, or am i going about this the wrong way?

thanks.

---

