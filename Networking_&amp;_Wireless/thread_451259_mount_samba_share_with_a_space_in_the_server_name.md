---
title: "mount samba share with a space in the server name"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2007-05-22
hi
im trying to connect to mount a samba share with a space (%20) in the server name.

my fstab line reads 

```
//file server/User_folders /mnt/file_server smbfs username=,password= 0 0
```

but this doesnt work.

so now i saw a suggestion at [http://forums.fedoraforum.org/showthread.php?p=299787](http://forums.fedoraforum.org/showthread.php?p=299787) to use **smb4k**, but this installs 50 Mb of kubuntu software, and i dont want to destroy my system... so, is it safe?

thanks

---

### Post by dmizer on 2007-05-22
> **Mujaheiden said:**
> hi
im trying to connect to mount a samba share with a space (%20) in the server name.

my fstab line reads 

```
//file server/User_folders /mnt/file_server smbfs username=,password= 0 0
```

but this doesnt work.

so now i saw a suggestion at [http://forums.fedoraforum.org/showthread.php?p=299787](http://forums.fedoraforum.org/showthread.php?p=299787) to use **smb4k**, but this installs 50 Mb of kubuntu software, and i dont want to destroy my system... so, is it safe?

thanks

try this:
```
//file\040server/User_folders /mnt/file_server smbfs username=,password= 0 0
```

---

### Post by Mujaheiden on 2007-05-22
brilliant!

---

### Post by pswartout on 2007-07-10
This also works (using \040) to overcome share names with spaces in. Many thanks!:lolflag:

---

