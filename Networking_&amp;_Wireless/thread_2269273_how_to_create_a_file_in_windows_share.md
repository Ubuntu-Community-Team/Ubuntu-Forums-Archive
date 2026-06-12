---
title: "how to create a file in windows share"
date: 2015-03-14
forum: Networking &amp; Wireless
---

### Post by davidtuti2 on 2015-03-14
Hi,
I have a windows share in my home but I can't create files inside. How could I fix it? To mount the windows share I do:
```
sudo mount -t cifs -o username=user,password=xxxxx//192.168.1.159/d windows/
```
Thanks

---

### Post by TheFu on 2015-03-14
First, you need to tell the cifs mount program which uid and gid to mount the storage under - or use the "users" option.
Second, you need to always use full paths to anything you use in a script.

```
#!/bin/sh

# Set these for your userid, locations, etc.
UID=1000
GID=1000
SOURCE="//192.168.1.159/d"
TARGET="/home/my-userid/windows"
CREDS_FILE=$HOME/.win_creds

MNT=/bin/mount
SUDO=/usr/bin/sudo

# Make certain the login credentials are readable for 1 userid
chmod 600 $CREDS_FILE

# all on 1 line (or with line extension) - put the Windows userid/password into the file.
# no spaces between the options!!!
$SUDO $MNT -t cifs $SOURCE     $TARGET \
      -o rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=$CREDS_FILE,users  

```
# - example credential file
username=your-windows-username
password=your-windows-password

Also, the **cifs-utils** package must be installed.

---

