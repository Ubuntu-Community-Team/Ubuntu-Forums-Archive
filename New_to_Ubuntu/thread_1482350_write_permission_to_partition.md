---
title: "write permission to partition"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-13
Hi, I have three OS installed in my computer

Debian 5.0
Ubuntu 10.04
Windows XP

To created a /data partition so that I can access the linux files from either Debian or Ubuntu. and there is ofcourse the windows partition. Now as a normal user "sid" I am not able to write any files to either /data partition or /windows partition. It says I don't have write permissions. I am only able to do it as root. Can anyone help me

---

### Post by Midnighter on 2010-05-13
Is the partition mounted at /data? If so, open a console and run ```
sudo chown -R username:groupname /data
```. replacing username and groupname with your username (eg. I would use david:david instead). Now you have full read/write permissions to it for your user. :)

---

### Post by oaridus on 2010-05-13
ya, the partition is mounted as /data. How do I know my groupname? is there a command for that. I may use as u suggested that is
sudo chown sid:sid /data 

but it is better to check the groupname, in case. Also how to get write permission for my windows partition which is vfat partition.

---

### Post by ManiDhillon on 2010-05-13
The most easy way is to add the permission in "/etc/fstab" file which hold all mount information.

```
/dev/sda5   /data   vfat   defaults,umask=000
```

Where "/dev/sda5" is your partition and "/data" is your mount point for that specific partition.
"umask=000" will give the read,write,execute permission.

Ask if you need more details. See there is no need for you to find anything like groupnames.

---

### Post by oaridus on 2010-05-16
Midnighter solution worked. used

sudo chown -R sid:sid /data

---

