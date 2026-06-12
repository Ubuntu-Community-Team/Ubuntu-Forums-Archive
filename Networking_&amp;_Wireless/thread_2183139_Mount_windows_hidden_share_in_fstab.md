---
title: "Mount windows hidden share in fstab"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by Mautobu on 2013-10-23
I'm having an issue that is becoming a little frustrating. I've got domain admin on this machine, and the account has security clearance to connect to this share on the server.

My fstab entry attempts include:
```
//server/share\044 /destination                cifs    rw,credentials=/root/.smbcredentials,noauto 0 0
//server/share\$ /destination                cifs    rw,credentials=/root/.smbcredentials,noauto 0 0
```

Both means give the same error:
```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I assume that this is a big bad dirty configuration issue.

---

### Post by cybercity@localhost on 2013-10-27
try to mount that partition without adding an entry into fstab.
```
**# mkdir -p /mnt/tmp-mnt**
```

now cd into newly created directory and enter this command.
```
**# mount -t smbfs -o username=yoursharedusername,password=yoursharedpassword //server/directory /mnt/tmp-mnt**
```check if it worked...
```
**# cd /mnt/tmp-mnt**
```
if it still doesn't work i recommend you to have a loot at this site and also make sure that you have smbfs and cifs installed on your machine.
```
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
```

---

### Post by Mautobu on 2013-10-28
Thanks very much for the reply, I'll give this a shot in the office tomorrow.

---

### Post by Mautobu on 2013-10-29
Pro skills, very helpful, thanks mate!

---

