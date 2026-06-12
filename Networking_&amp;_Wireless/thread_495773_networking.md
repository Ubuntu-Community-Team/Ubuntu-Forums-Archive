---
title: "networking"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by alaskaman on 2007-07-08
can any one tell me how i can net work a ubuntu server and a xp computer togeter im trying to get it so i can view my linux server harddrive from xp

---

### Post by masterd on 2007-07-08
You need to enable file sharing under the Ubuntu server using a samba server. You can use the information at 

[http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/) 

as a starting point :-)

or if you want a faster solution

you can use the buildin SFTP functionality of the SSH server and access the harddrive of your linux server by only using the SSH protocol. You most probably have it already installed and working.
On your windows pc you can use [WinSCP]("http://winscp.net/eng/index.php") - it works quite stable and it is open source :-P

Hope this help you :-)

---

