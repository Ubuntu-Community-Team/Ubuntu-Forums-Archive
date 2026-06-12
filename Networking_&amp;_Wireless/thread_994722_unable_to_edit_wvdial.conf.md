---
title: "unable to edit wvdial.conf"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by arunkumar413 on 2008-11-27
hi
I want to connect to internet. Am using Ubuntu 8.04 LTS.i ran the wvdial command.It has detected my modem.but am unable to edit the wvdial.conf file present in /etc folder.It returns an error "sorry you do not have necessary permission to edit this file".When I checked the properties of the wvdial.conf file,it is owned by root user.moreover iam unable to change the permissions of the file.help me please...

---

### Post by cariboo on 2008-11-27
You have to be root to edit the file. TO do this press Alt-F2 and enter:

```
gksu gedit /etc/wvdial.conf
```

Enter your password when asked, you can now edit the file. For editing any configuration file not in your home directory, or running prgrams form a terminal you need to be root. For eaxmple to run Synaptic Package Manager from a terminal type:

```
sudo synaptic
```

Have a look athis:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for a much better explantion than I can do. :)

Jim

---

### Post by prshah on 2008-11-27
> **arunkumar413 said:**
> When I checked the properties of the wvdial.conf file,it is owned by root user.

Prefix gksudo to whatever command you are using to edit the wvdial.conf file.

If you are trying to browse to it using the file manager, and then choosing to edit it, instead try:

Press ALt+F2,
and give the command```
gksudo gedit /etc/wvdial.conf
```

---

### Post by arunkumar413 on 2008-11-27
does this work even if i do not have permission to edit the file,because the file is owned by root user

---

