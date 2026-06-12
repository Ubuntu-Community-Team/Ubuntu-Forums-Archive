---
title: "File server"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-23
I'm setting up a file server with ubuntu server. Firstly, what else do I need (apache)? and any other advice would be very very welcome!!

I've never done this before...but linux (and by proxy mr linus) has inspired me :-)

---

### Post by drdos2006 on 2010-10-23
Server software on one machine, client software on the other.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added /media/sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp MyGroupName  /media/sdb1/sdb1-shared
Added all the files into the shared directory.
//**
On the Client machine: Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles, mounted /media/sharedfiles from terminal as /media/sharedfiles with : 
sudo mount  <serverIPaddress>:/media/sharedfiles  /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

---

### Post by Hippytaff on 2010-10-23
Excellent..thanks for taking the time to share that. Just one question
> 
sudo mount  <serverIPaddress>:/media/sharedfiles  /media/sharedfiles 
do the ip addresses need to be static?

edit - Just realised you were on about mounting the server address on the pc's used.....ignore :-)

---

### Post by Rubi1200 on 2010-10-23
Some advice? Security!!

> **[SIZE=4]_Running Server(s)_[/SIZE]**

Part of setting up a server is reading/learning how to secure it. Common  servers include NFS, Samba, FTP, SSH, VNC, RDP, and HTTP. If the  "how-to" you are following does not review security, you need to keep  looking ...***"Desktops" become "Servers"*** if server software is installed.

_Questions to ask yourself include_:

[LIST=1]
[*]What port(s) or services does this software provide?
[*]Who will be able to connect to this? (i.e. is it restricted to a range of IP addresses Password protected?)
[*]What level of access will the visitor have to the system? (i.e. does  the server run under a restricted user, or the root acount? What can  this restricted user do in a worst case scenario?)
[*]Does this service expose any additional information that's useful to  a hacker? (i.e. does it allow users to transmit their passwords in  cleartext? Does it have a 'statistics' view that reveals logged-in  users, ip addresses, network configuration, or other potentially helpful  information?)
[*]What is the **security history** of this software? Does it have a history of vulnerability and patch after patch? Or has it had a relatively unmarred history?
[/LIST]

Examples :

[SSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")
[VNC]("https://help.ubuntu.com/community/VNCOverSSH")
[Apache]("http://www.howtoforge.com/apache_mod_security")
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Enjoy and good luck!

---

### Post by Hippytaff on 2010-10-23
> **Rubi1200 said:**
> Some advice? Security!!


[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Enjoy and good luck!

thank you...I thikn I'm looking at doing SSH, because it seems more secure...but the server will be a dedicated server and it will be internet facing, so we can access files from else where...so thank you for your advice! :-)

---

