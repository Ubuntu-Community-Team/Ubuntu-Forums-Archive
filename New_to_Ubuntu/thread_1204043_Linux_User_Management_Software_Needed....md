---
title: "Linux User Management Software Needed..."
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-07-04
Hi

I am looking for a Linux User Management Software (can be web-based software like SWAT, CUPS web interface) which can make changes on remote Linux System.

I have a Linux data server without monitor. I need to work in that server only when I need to add or remove a user for which I need to connect a monitor everytime. If this job can be done remotely I will be happy :p

Thanks in advance

---

### Post by skillllllz on 2009-07-04
> **Guruprasad said:**
> Hi

I am looking for a Linux User Management Software (can be web-based software like SWAT, CUPS web interface) which can make changes on remote Linux System.

I have a Linux data server without monitor. I need to work in that server only when I need to add or remove a user for which I need to connect a monitor everytime. If this job can be done remotely I will be happy :p

Thanks in advance


You can use ebox or webmin for web-based manangement. You could also use VNC for remote desktop. If all you want is quick, secure access to the GUI for user management, it may be more practical to use SSH X forwarding to remotely access it. I highly recommend this method.

The terminal command would look like this (but with your server's IP):
```
ssh -X 192.168.1.50 users-admin
```

---

### Post by earthpigg on 2009-07-04
ssh?

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by skillllllz on 2009-07-04
Also, if you decide to use the X forwarding method, you will need to do the following on your server first:

Go to System -> Administration -> Authorizations -> freedesktop -> systemtoolsbackends -> Manage system configuration. Then click Edit, choose Yes for "Anyone", choose "Admin Authentication", and click modify.

That will allow you to click "Unlock" in the users-admin tool when using it remotely.

---

