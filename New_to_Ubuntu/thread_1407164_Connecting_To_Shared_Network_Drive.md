---
title: "Connecting To Shared Network Drive"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by BarfBag on 2010-02-14
[https://help.ubuntu.com/9.10/internet/C/networking-shares.html](https://help.ubuntu.com/9.10/internet/C/networking-shares.html)

The instructions in the preceding link were used to share an external hard drive on my network.  I'm having trouble connecting to it from another Ubuntu PC on the network.  (Just for clarification: Both PC's are running Ubuntu 9.10.)  When I go to the network folder, I see it, but I get the error, "Unable to mount Windows drive."  Both computers have Samba installed.  Any suggestions?

---

### Post by BarfBag on 2010-02-15
Bump.

---

### Post by nothingspecial on 2010-02-15
You don`t need samba to share from Ubuntu to Ubuntu.

On both machines -```
 sudo apt-get install openssh-server openssh-client
```

One of them is installed by default but I can`t remember which one.

Then in your menu go Places > Connect to server

In the top box choose ssh

In the next one put user@ipaddress of the remote machine.

Put a check in the bookmark box and chooser a name for the bookmark.

Your other computers entire file system will now be accessible from your Places menu.

If you just want to mount a folder you can use sshfs

```
sudo apt-get install sshfs
```

On the machine you want to mount the network folder on 
```

sshfs -o idmap=user $USER@192.168.2.10:/media/music/ ~/music
```

This assumes you have the same username on both computers, if not change $USER for the other username

obviously change the paths and ipaddress to your ones.

---

### Post by Morbius1 on 2010-02-15
If the external drive is formatted in ntfs or fat32 then it's likely this isn't a samba problem but a linux permissions problem. There are a couple of ways to fix this problem. The easiest is to add the following line to the smb.conf file:

```
force user = your_ububntu_login_user_name
```Depending on which method you used to share the drive it will either be in the [global] section if you used Nautilus-share or in the share definition section if you used Classic samba. If you post the output of the following commands I can give you a better idea where to put it:

Open **Terminal**
Type **net usershare info**
Type** testparm -s**

---

