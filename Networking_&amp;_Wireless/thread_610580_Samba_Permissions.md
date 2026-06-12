---
title: "Samba Permissions"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by renzokuken on 2007-11-12
Hi all....

i have feisty set up as a Domain controller and [homes] set up so everyone has their own private folder, as well as a universal "temp" folder that everyone has read/write access to.

my boss/supervisor though wants full read write access to all the home folders. i'm trying to set up a new share to /home in the smb.conf, but its not working. with my first effort he could see the /home directory but didnt have r/w access. i fiddled a bit to allow r/w and now he cant see /home at all.

what is the correct way to set this up in smb.conf. here is the share as it stands for a read only

```
[private]
   path = /home
   writable = no
   valid users = brian   
   browsable = no
   comment = Private Directories
```

right now he cant see it and even if he could obviously cant write to it.........what am i doing wrong?

thanks

---

