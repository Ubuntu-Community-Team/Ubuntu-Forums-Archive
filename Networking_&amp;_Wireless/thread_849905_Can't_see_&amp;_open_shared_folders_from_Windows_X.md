---
title: "Can't see &amp; open shared folders from Windows XP"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by hsn09 on 2008-07-05
Hello All,
          I've installed ubuntu 8.04 (hardy) on my workstation. I'm using windows xp professional sp2 on my server. I've shared some folders on my server but i'm unable to browse those folders. Just my networked systems shown in network but when i open my server there is no folder shown.:confused::confused: please help me in this regard "How can i done this task?"


[www.loverpal.com](www.loverpal.com)

---

### Post by df6269 on 2008-07-05
Can you make sure these machines located in the same workgroup?
Did you check permission in your server for everyone?

---

### Post by hsn09 on 2008-07-05
my workgroup name is 'mshome' but i'm not sure which one is ubuntu's?

---

### Post by df6269 on 2008-07-05
You can check your /etc/hosts and /etc/samba/smb.conf file.
The detail information as below:
[http://itmanagement.earthweb.com/osrc/article.php/12068_3755176_1](http://itmanagement.earthweb.com/osrc/article.php/12068_3755176_1)

---

### Post by superprash2003 on 2008-07-05
go to places->computer and under location type smb://x.x.x.x where x.x.x.x is the ip of the windows xp machine

---

