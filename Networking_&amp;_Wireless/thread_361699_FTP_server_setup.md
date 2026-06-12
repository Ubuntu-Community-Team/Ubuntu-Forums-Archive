---
title: "FTP server setup"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by ian471 on 2007-02-14
I have installed the 6.06 server version of Ubuntu, and HTTP and PHP work great.  However, I would like to edit my PHP code on another machine and upload it to the server machine for testing via FTP.  It does not appear that the OS I have installed has a working FTP server already, so I've been trying to find how to install one.  I have found several instructions to type: "sudo apt-get install proftpd".  When I type this, I get "package not found".

What is apt-get?  Does it connect to the internet to download things? If so, through what port and protocol?  Does this mean that the 6.06 *SERVER EDITION*does not come with any form of FTP server whatsoever?  That seems very strange.

Any help will be appreciated.

---

### Post by gradedcheese on 2007-02-14
sudo apt-get install openssh-server

This gets you ssh and sftp, do **not** use plain FTP, it's a security risk.  You can actually ssh in and edit you code there, or you can use sftp the way you'd use ftp before.

> 
Does this mean that the 6.06 SERVER EDITIONdoes not come with any form of FTP server whatsoever?


it's for your own safety that they don't ship FTP with it... ;) however the server edition might already have openssh installed?

---

### Post by danielprice on 2007-02-15
We just installed vsftpd on our system here, it works a treat and it's real easy to set up.

---

### Post by dmizer on 2007-02-15
i've been meaning to try my hand at openssh-server.

however, i've found proftpd to be adequate for my needs.  the third link in my sig is a fantastic howto for fairly restrictive (but still useful) ftp server settings using proftpd.

---

