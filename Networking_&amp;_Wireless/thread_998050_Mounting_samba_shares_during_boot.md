---
title: "Mounting samba shares during boot"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by gmclachl on 2008-11-30
I am having weird permission problems mounting a samba share during boot/login. 

I am using the dispatcher scripts in NM to mount these with the following command

smbmount //192.168.0.101/Monkey /media/MonkeyDrive -o username=username,password=password

However when the file system is mounted the top level directories have the correct permissions, the sub diretories are owned by a group/uid of 1001, which doesn't even exist on the system. 

If I use sshfs then all the permissions are fine (but I can't use sshfs at boot so that's not an option.)

George

---

