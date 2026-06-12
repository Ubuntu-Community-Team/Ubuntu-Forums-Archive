---
title: "Acessing Ubuntu's Samba share requires a password?"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Schalken on 2007-03-24
I just shared a folder via SMB from Nautilus with read+write permissions, however when I try to access the share from a Windows computer it asks for a username and password, with which neither my Ubuntu nor Windows username and password work.

How can I, without hassle, make it such it doesn't require a username and password to read/write (depending on my setting) files remotely?

Or as another option, where do I set the username and password that needs to be used?

This is a fresh install and I haven't touched /etc/samba/smb.conf.

---

### Post by i-Buntu-2 on 2007-03-24
Hello,

There's a great how to about Samba at the following location:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server)

I've used this as a guide on my install of Ubuntu Server 6.06 (Dapper) and everything is shared out fine

---

### Post by Schalken on 2007-03-25
The command "sudo smbpasswd -a me" worked and I can now read/write the shared folder by logging in with my system username and smb password, however It is still unclear what I have to change to make shares created with Nautilus's tool auomatically accessable without authentication.

---

### Post by al7kz on 2007-03-25
Try this:

$gksudo gedit /etc/samba/smb.conf

security=share

lemmeno if this helps

---

### Post by Schalken on 2007-03-25
With that, I can read, but not write. It doesn't ask me for a password.

---

