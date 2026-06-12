---
title: "gconftool-2 problem"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by nikonfrz on 2009-03-23
when i run this

```
gconftool-2 --get /apps/nautilus/preferences/show_desktop
```

i get this

```
vpkeebs@vpkeebs-laptop:~$ su
Password: 
root@vpkeebs-laptop:/home/vpkeebs# gconftool-2 --get /apps/nautilus/preferences/show_desktop
Failed to get value for `/apps/nautilus/preferences/show_desktop': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
root@vpkeebs-laptop:/home/vpkeebs#
```

can anyone help me find out whats wrong?

---

### Post by drs305 on 2009-03-23
Edit: I noticed you didn't provide the value, but then saw you were using *-get* and not *-set*. So you aren't trying to change or establish a new setting but just trying to return the value? I may have jumped in too quickly here.

---

### Post by nikonfrz on 2009-03-23
no luck

```
vpkeebs@vpkeebs-laptop:~$ su
Password: 
root@vpkeebs-laptop:/home/vpkeebs# gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
root@vpkeebs-laptop:/home/vpkeebs# 

```

---

