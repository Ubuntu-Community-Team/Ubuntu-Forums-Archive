---
title: "Unable to set permission to group for files and folder created from windows 7"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by najam2 on 2014-03-08
[COLOR=#333333][FONT=UbuntuRegular]I have configured samba share as follows on Ubuntu 12.04
[/FONT][/COLOR]
[PC1]
comment = Drive for PC 1
path = /home/meta/PC1
writeable = yes
valid users = meta, pcone
guest ok = no
read only = no
write list = @pcone
browseable = yes
create mask = 0775
directory mask = 0775
[COLOR=#333333][FONT=UbuntuRegular]
The user "meta" has admin access and while "pcone" is a standard user. There are two windows PC, admin and home. The admin PC logs in with "meta" credentials while the home windows PC logs in with "pcone" credential to access the share. They can easily access and write to the directory and can create new files/folders. However, the files/folders created from Windows 7 does not have "write" permissions for the group and set the ownership to meta for all the new files/folders. Please note that "meta" is also a member of "pcone" group. However, if sit on Ubuntu and logs in with "meta" and create a file/folder in the shared directory it has proper rw permissions for the group.[/FONT][/COLOR]

---

