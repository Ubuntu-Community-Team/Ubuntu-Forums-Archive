---
title: "Help for opening FTP port"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Madley on 2007-05-30
Hi all,

i want to open my FTP port 21... I'm behind a router, and on my router I configured my port correctly. Now the problem is, how can I tell to my Feisty to open my 21 port?

Thanks all

---

### Post by spd106 on 2007-05-30
There's no firewall on Ubuntu by default, so there's no need to configure a port. Just start up the FTP server and make sure it's running on port 21, netstat will show you if it's up and running. 

If you have installed a firewall configuration app like firestarter or set up iptables manually, then you will have to open a port.

Some servers require inetd to be installed, which isn't by default on Ubuntu. So you may have to install it yourself, check the documentation of the FTP server.

---

### Post by Madley on 2007-05-31
Thanks for your reply.

I tried to connect by ftp to the site of my university, where I've a directory for my files.

Using FileZilla I get this message error:


```
Status:	Resolving IP-Address for ares.science.unitn.it
Status:	Connecting to 193.205.213.3:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.0.1)
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Command:	USER myuser
Status:	Verifying certificate...
Status:	TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS ******
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	211 End
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PORT 82,113,197,185,167,67
Response:	200 PORT command successful. Consider using PASV.
Command:	LIST
Response:	150 Here comes the directory listing.
Error:	Disconnected from server
Error:	Failed to retrieve directory listing
```

what's wrong?

---

### Post by Madley on 2007-06-01
up....

---

### Post by bsmith1051 on 2007-06-01
FYI
Here's the how-to on setting-up an FTP server,
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by spd106 on 2007-06-01
Might be worth having a look through the Filezilla forums to see if you can identify the issue.

---

