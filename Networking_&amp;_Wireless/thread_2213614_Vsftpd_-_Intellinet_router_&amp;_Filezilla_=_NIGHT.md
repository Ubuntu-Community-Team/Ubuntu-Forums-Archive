---
title: "Vsftpd - Intellinet router &amp; Filezilla = NIGHTMARE - I need help please"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by majik2 on 2014-03-27
These 3 ingredients have made my life a total mess for the past 4 days.

Can someone knowledgeable please explain to me in terms I can understand how to make these 3 work  together so I can have a working FTP ?

---

### Post by Lars Noodén on 2014-03-27
In general, it is past time to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  If you have a special use-case for FTP then we can look at that.  FileZilla and all the file managers (like Nautilus) support SFTP now.  To get SFTP support all you need is the package openssh-server installed on your target machine.  Then to get access from the outside, forward port 22 for SSH.  The settings for forwarding will vary depending on your router.  

There are other fine points like setting up key-based logins one you get basic connectivity settled.

---

### Post by majik2 on 2014-03-27
ok... I will uninstall Vsftpd  & take your advice and install openssh-server

At least this is a start in the right direction.  Thank you for taking the time Lars!

I will be back!

---

### Post by majik2 on 2014-03-27
This is the output I am receiving through Filezilla test. Does anyone understand what might be wrong here ?

Connecting to probe.filezilla-project.org
Response: 220 FZ router and firewall tester ready
USER FileZilla
Response: 331 Give any password.
PASS 3.5.3
Response: 230 logged on.
Checking for correct external IP address
IP 24.237.53.182 ce-cdh-fd-bic
Response: 200 OK
PREP 37793
Response: 200 Using port 37793, data token 247979422
PORT 24,237,53,182,147,161
Response: 200 PORT command successful
LIST
Response: 150 opening data connection
Response: 503 Failure of data connection.
Server sent unexpected reply.
Connection closed

---

### Post by majik2 on 2014-03-27
Waiting to retry...
Status:	Connecting to 24.237.53.182:53...
Status:	Connection established, waiting for welcome message...

then it  times out! ??  Any ideas ??

---

### Post by steeldriver on 2014-03-27
Where are you trying to connect **to **and **from**, and **how** exactly? your filezilla test output looks like some kind of passive ftp session rather than sftp

For sftp, it should just be a matter of entering your host name or IP, username, password, and port (the SSH port - i.e. 22 by default) into the filezilla GUI and pressing 'Quickconnect'

---

