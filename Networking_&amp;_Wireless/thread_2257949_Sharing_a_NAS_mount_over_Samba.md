---
title: "Sharing a NAS mount over Samba"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by rafael-alramos on 2014-12-23
I have a Drobo5N connected to my server but am unable to share it through Samba. I want the user control access to be made by my server, so i don't have to setup every user again, or make my employees connect to two differente network paths to access their files.

my fstab line:

//192.168.50.200/Drobo/servidor /home/SERVIDOR/drobo cifs ilha,uid=501,gid=501,username=~drobouser~,password=~drobopassword~,umask=0022,rw,file_mode=0777,dir_mode=0777 0 0

my samba share:

[drobo]
   comment= drobo
   browseable = yes
   path = /home/SERVIDOR/drobo
   read only = no

all the mounted files belong to the user ilha, so there are no file permission issues. thanks in advance for any help

---

