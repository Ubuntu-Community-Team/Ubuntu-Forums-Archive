---
title: "Samba - Ubuntu 6.06 to Windows XP"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by rippon on 2006-08-19
I am having some trouble with sharing folders between a Windows XP computer, and a Ubuntu 6.06 computer. The Ubuntu computer can see everything on the Windows box, and all is well. However, the Windows XP computer cannot access the supposedly 'shared' folder on the Ubuntu Machine. The Computers can both ping each other fine, it is just that when I try to access the certian shared folder through windows, I come to a screen which says "connect to local host," and then asks for a User name and password. Even if I try the username and password for the Ubuntu machine, it doesn't work.

How do I log into the Ubuntu machine? It just simply doesn't want to let me do it.

Thanks.

---

### Post by hopstah on 2006-08-19
you need to set up a samba password
```
sudo smbpasswd username
sudo smbpasswd -e username
```
that should do it.  you have to use the username of an account on the computer, and you don't have to make the samba password the same as your system password.  then use that to log into the ubuntu share.

there is also a way to eliminate the password thing, but i have found that to be flaky.

---

### Post by rippon on 2006-08-20
Sweet. Now I can check on F@H remotely. 
Thanks again.

---

