---
title: "vsftpd ftp server best practice"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by akkad on 2009-06-17
am trying to build a LAMP server with ubuntu server 8.04, i installed vsftpd to be my ftp server, so am wondering how the best setup for the ftp server will look like taking in consideration security wise which needs your help guys.

the thing here is there will be multiple ftp users, all ftp users are going to upload files to the same ftp directory where this directory will be the php web directory under apache, so what are your suggestions? am not looking for anonymous login instead there will be user login.

please advise, and if you have good links for this issue please provide it too, thanks.

---

### Post by DGortze380 on 2009-06-17
> **akkad said:**
> am trying to build a LAMP server with ubuntu server 8.04, i installed vsftpd to be my ftp server, so am wondering how the best setup for the ftp server will look like taking in consideration security wise which needs your help guys.

the thing here is there will be multiple ftp users, all ftp users are going to upload files to the same ftp directory where this directory will be the php web directory under apache, so what are your suggestions? am not looking for anonymous login instead there will be user login.

please advise, and if you have good links for this issue please provide it too, thanks.

First piece of advice is to not do this.
Security wise, IMO, it's a bad idea to allow direct uploads to your php directory.

---

