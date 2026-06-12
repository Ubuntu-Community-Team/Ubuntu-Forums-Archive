---
title: "How to FTP (specific user)"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by marc.morcos on 2008-05-27
Hey guys, just a quick question.

This is what i want to do.

I want to ftp into to a specific computer at home with a specific user.

I tried

ftp user@hostname
ftp computer_name@hostname

I don't know how to include both user and computer name

Thx

---

### Post by marc.morcos on 2008-05-27
bump

---

### Post by Nepherte on 2008-05-27
```
ftp hostname portnumber
```
This command applied to ftp.belnet.be, where the ftp server is listening on the default ftp port 21:
```
ftp ftp.belnet.be 21
```
Afterwards it will ask you for a username, you fill that in and press enter. Now it will ask you for a password.

If you want information on a command (ftp for example), try entering:
```
man ftp
```

---

