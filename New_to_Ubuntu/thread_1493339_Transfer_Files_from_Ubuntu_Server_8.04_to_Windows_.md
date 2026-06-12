---
title: "Transfer Files from Ubuntu Server 8.04 to Windows PC"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by jchurtado on 2010-05-25
Hi,
 
 
I'm new in Ubuntu. I use Ubuntu Server 8.04 minimal. In this server I run a webpage that is a Web Virtual Store. The problem that I have is that I need to transfer the "domian.csr" (the SSL Certificate of the store expired) file to windows so I can email it to the administrator to get the new SSL certificate. Any help will be appreciated. Thanks.

---

### Post by bodhi.zazen on 2010-05-25
If you have ssh installed you can use winscp.

If not, put it into a directory in your web root, download the file to windows / a web browser, then delete the file from your web root.

If you are new to Ubuntu, why not 10.04 ?

---

### Post by jchurtado on 2010-05-26
The server has already installed the SSH service but I don't know how to configure the winscp. I have enter the hostname, username, password but it does not connect. The user is new but the server was install about 1 year ago.

---

### Post by -humanaut- on 2010-05-26
If your running through a LAN you should be able to cd into smb://windows.ip.address 
then copy your files over with cp. (I'm assuming your not using a GUI correct?)

---

### Post by jchurtado on 2010-05-26
Yes the Ubuntu Server and the Windows PC are in the same lan but don't how to use that command you mention. The server does not use GUI just terminal. What are the command using cp to transfer the file??? I have downloaded some programs to access the server (FREEFTPD), WINSCP, FREESSH but I only succesfully connect to FREEFTPD when I use the scp -r command, the insert the password the I welcomes me to FREEFTPD but not know how to transfer the file.

---

### Post by -humanaut- on 2010-05-26
You could setup the regular ftp protocol on the windows machine and set the ubuntu machine as the server and download them directly from windows.

---

### Post by bodhi.zazen on 2010-05-26
> **jchurtado said:**
> The server has already installed the SSH service but I don't know how to configure the winscp. I have enter the hostname, username, password but it does not connect. The user is new but the server was install about 1 year ago.

That is all there is to it.

Try entering the IP address rather then the hostname.

---

### Post by jchurtado on 2010-05-26
How I do that. I create a network place and add "[ftp.domain.com]("ftp://ftp.domain.com")" and the try to enter???

---

### Post by jchurtado on 2010-05-26
I have try and enter already the IP address but refused the connection then I try to connect with the winscp to FTP because I discover that the port 21 is open and thr FTP server service is running (PROFTPD). But the connection timeout.

---

### Post by bodhi.zazen on 2010-05-26
Winscp should connect via ssh (scp == secure copy == transfer files over an ssh connection) files over ssh.

Do you know the ip address of your server ?

---

