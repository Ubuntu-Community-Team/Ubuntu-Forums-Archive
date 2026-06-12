---
title: "smb password"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Challengerquay on 2009-07-12
Hi 
I have been trying to set the user and smb password on the SAMBA server, I have used:
sudo smbpasswd-name in a terminal to set the user ID on the SAMBA server, but this will not work. Do I have to set terminal with root permissions before this will work?](*,)

---

### Post by lisati on 2009-07-14
You might want to try something like this, replacing "your_username" with your choice of samba user name:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```


The first command adds a user to samba and prompts for a password. The second enables the user.

---

