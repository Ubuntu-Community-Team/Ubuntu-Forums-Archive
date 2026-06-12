---
title: "FTP server user error"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by blacappuccino on 2008-05-02
Heys guys i'm using Ubuntu 7.10, i trying to share files in FTP i ran the command

>  sudo apt-get install vsftpd 

after that typed in the browser 

> [ftp://192.168.1.65](ftp://192.168.1.65)

 for example, i mean my IP, i can connect but it ask me a password and username. but i don't know which password and and username i must use to have access.

I tried the anonymous mode editing the file 

> /etc/vsftpd.conf

to
> 
anonymous_enable=YES
#local_enable=YES
#write_enable=YES
#anon_upload_enable=YES


So how i can do to manage my user in FTP, i mean a need a interface that allow me to do that. Is it possible?

I found this steps in this link for 6.06 LTS:

> [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

Cheers

---

