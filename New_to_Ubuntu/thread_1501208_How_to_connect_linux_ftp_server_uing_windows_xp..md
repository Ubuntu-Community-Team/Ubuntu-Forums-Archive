---
title: "How to connect linux ftp server uing windows xp."
date: 2010-06-04
forum: New to Ubuntu
---

### Post by honey_bee on 2010-06-04
Hi,
          I have created a ftp server in Linux.The client machine is also a linux machine and it can access the ftp server using user name and password. There is another client machine running windows xp.It ping to my linux ftp server but it can not connect to my ftp seerver using
 
c:\ftp 192.168.1.10
 
please help me that how can i connect my ftp server through windows xp.
 
thanks
honey

---

### Post by Soulcage on 2010-06-04
Open your browser on the xp machine and type in the address bar [ftp://192.168.1.10/]("ftp://192.168.1.10/")

---

### Post by honey_bee on 2010-06-04
thanks for the reply well when i write it show me following error
 
**c:\>[ftp://192.168.1.10](ftp://192.168.1.10)**
**'ftp' is not recognized as an internal oe external command,**
**operable program or batch file.**
 
The system can ping with Linux ftp server successfully but does't connect through ftp command.Please help me

---

### Post by Jakiejake on 2010-06-04
> **honey_bee said:**
> Hi,
          I have created a ftp server in Linux.The client machine is also a linux machine and it can access the ftp server using user name and password. There is another client machine running windows xp.It ping to my linux ftp server but it can not connect to my ftp seerver using
 
c:\ftp 192.168.1.10
 
please help me that how can i connect my ftp server through windows xp.
 
thanks
honey

Terminal
> ftp
o
(IP Address)

Or Download Firezilla from the software center

---

### Post by zipperback on 2010-06-04
> **honey_bee said:**
> thanks for the reply well when i write it show me following error
 
**c:\>[ftp://192.168.1.10](ftp://192.168.1.10)**
**'ftp' is not recognized as an internal oe external command,**
**operable program or batch file.**
 
The system can ping with Linux ftp server successfully but does't connect through ftp command.Please help me

Type it into the web browser address area, NOT the command line.


Or you can use an ftp application such as filezilla.

-= zipperback
:popcorn:

---

### Post by Jakiejake on 2010-06-04
> **zipperback said:**
> Type it into the web browser address area, NOT the command line.

-= zipperback
:popcorn:

:lolflag:

---

### Post by honey_bee on 2010-06-04
thanks a lot for the help.I can login through the browser as well filezela software. One thing I want to ask which is beyond the scop of this post that when i type 
 
[ftp://192.168.1.10](ftp://192.168.1.10) i can see a folder "pub" .Can you tell me that in linux where this folder exists. In /etc  or in vsftpd  ?
 
thanks a lot for a nice help

---

### Post by HermanAB on 2010-06-04
It is probably /var/ftp/pub

---

