---
title: "How to runnunig smbd ?"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by saidbakr on 2009-09-11
How could I make smbd to be run?

From my post - [Click here to look at it]("http://ubuntuforums.org/showthread.php?p=7935015#post7935015") - I found that smbd does not run and this by execute the command :
/etc/init.d/samba status

which turned that nmbd is running but smbd is not running

---

### Post by cariboo on 2009-09-11
Open a terminal and type:

```
testparm
```

This will show you if your /etc/samba/smb.conf file has any errors.

---

### Post by saidbakr on 2009-09-12
I write my reply after removing samba-common and installing the share service again. The command you regarded works now and show fine results because the smb.conf is totally replaced. However, I still have not able to handle folders and file sahring.

It takes long time to be able get the WORKGROUP in Windows Network, after several Unable to mount location error message. After this time the workgroup computers in my LAN appear but the same message I get when trying to open the shared file from the remote computer.

---

