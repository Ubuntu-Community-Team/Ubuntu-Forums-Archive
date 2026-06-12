---
title: "/dev/null permissions changes on boot"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by kilometk on 2009-12-06
I can't log on with graphical interface
when I tun my coputer on I got this
[I]/dev/null: permission denied
/dev/null: permission denied
/dev/null: permission denied[/I]
Some program is changing the permission of **/dev/null** , leaving the permissions in this way
**0600** which is  ** -rw-r--r--   1   root   root   1, 3 **
and it needs to be
**0666** which is   **crw-rw-rw-   1   root   root   1, 3**
I tried to remake it, removing it  with    **rm /dev/null**
and recreting it with            **mknod -m 0666 /dev/null c 1 3**
and I check it  with    **ls  -l  /dev/null**   
and everything is fine 
but when I reboot the permission has changed
I seems to be a program with root permissions is changing it  when I reboot

is there a way to know which program is changing the permissions of /dev/null? 
or a way to solve this?

Note: this happend after update

---

