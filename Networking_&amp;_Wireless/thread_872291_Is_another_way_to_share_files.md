---
title: "Is another way to share files?"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by sightfire on 2008-07-27
Is there another way to share files between ubuntu 8.04(running on vmware server 1.06) and windows xp(my host os), beside using samba? If so how-to.

---

### Post by quantum-positron on 2008-07-27
Yes using nfs work great
[http://rotyyu.wordpress.com/2008/02/06/file-sharing-through-nfs/](http://rotyyu.wordpress.com/2008/02/06/file-sharing-through-nfs/) 

Edit:
Sorry didn't see the XP part first time around. I don't think this will work with XP but it might.

---

### Post by dmizer on 2008-07-27
Also, FTP works quite well between Windows and Ubuntu.

Here is a good howto: [http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by dietkinnie on 2008-07-28
Install apache and set the "shared directory" as the webroot

---

### Post by prototype_angel on 2008-07-28
Install an ftp server

I would recommend proftpd or pureftpd, which both have corresponding gui administrative systems

---

### Post by Iowan on 2008-07-28
SSH? (PuTTY)

---

