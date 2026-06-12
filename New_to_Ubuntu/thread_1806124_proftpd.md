---
title: "proftpd"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by nevi1956 on 2011-07-17
Hi all
I'm new to unix and a bit out of my depth.
I have just installed Ubunta Server 11.04 "Natty" to play around with web server.
I install it as Guided- use entire disk with auto security updates , lamp, grub boot loader, got updates, all upgrades, telnet then got proftpd, edited  shells via Vi editor and added /bin/false to end of file saved and quit all ok.
added two web users, edited proftp via Vi editor and removed the # from the start of the default line so to lock in all ftp users into the home directory I also changed the server name to our family name.
 
so I tried to upload a index.html file to one of the web accounts but I could not connect and I tried Fileziller and Draemweaver, both of which failed to connect.
 
I can surf to the server web page also to both web accounts but can't connect via ftp.
I have also been able to install Webmin that works fine as as well as Webalizer
 
Any help would be great
 
Many Thanks
 
The newbee Nevi1956:popcorn:

---

### Post by Lars Noodén on 2011-07-17
Try using SFTP, it's part of the package openssh-server. Unlike FTP, it is secure. Filezilla and Dreamweaver, along with many others, support SFTP.

To set up a user for SFTP, just create a user on your system. Then it just works.

---

### Post by nevi1956 on 2011-07-18
Hi thanks for your response
 
But as a newbee to  linux how do I do that?
Do I have to uninstall FTPD ?
Do I need to install FSTP and when i di, will t see the two users I have already maid
 
Sorry for sounding so dumb but I know very little about this.
 
Many thanks
 
Nevi1956:popcorn:

---

### Post by nevi1956 on 2011-07-19
Hi once again
I found out how to install sftp by apt-get install openssh-server and I think it is running but I'm not sure, I have also attempted to uninstall proftpd, but I don't think that it worked.
I still  can not connect Ftp using Fileziller or Dreamweaver
 
I know when I type sftp 192.168.1.xxx I get a reply of Password and when I type in my root password i get sftp prompt, so that looks ok.
 
But when I type ftp 192.168.1.xxx i get connect: Connection failed, so am I correct in saying I have gotten rid of proftpd?
 
So I then went to Fileziller tried to connect with
 
Host:  192.168.1.xxx  User Name:  XXXXXXX  Password:  XXXXXXX  Port:  21
 
Clicked on connect and got 
 
[SIZE=1]Status: Connecting to 192.168.1.195:21...
Status: Connection attempt failed with "ECONNREFUSED - Connection refused by server".
 
Can some one help
I don't know if I' m able to aske for someone to help me over the phone
 
Nevi1956:(
 
[/SIZE]

---

