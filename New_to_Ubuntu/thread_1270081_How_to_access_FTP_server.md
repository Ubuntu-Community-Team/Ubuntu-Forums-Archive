---
title: "How to access FTP server"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by arpalermo on 2009-09-19
Hello linux people,

Thanks to your help I was able to get an FTP server running (i think) on my ubuntu box using vsftpd. Now how do I access it from my windows machines to transfer files? The FTP folder is /home/ftp.

---

### Post by talsemgeest on 2009-09-19
Try [filezilla](http://filezilla-project.org/). It is a free piece of software, you type in the address of your ftp server, your username and password and it should connect for you.

---

### Post by arpalermo on 2009-09-19
How do i find the address of the FTP server?

---

### Post by talsemgeest on 2009-09-19
> **arpalermo said:**
> How do i find the address of the FTP server?
If you are trying to access it from another computer in the lan, go onto the server and type ```
sudo ifconfig
``` Look for a string of numbers, something like 192.168.1.2. That will be the address.

If you want to access it from a windows machine from the internet, things get a bit trickier. If you need to, make another post and I will explain.

---

### Post by arpalermo on 2009-09-19
SUCCESS! Thank you so much for your help!  MAN I LOVE MY UBUNTUBOX!!

---

### Post by talsemgeest on 2009-09-19
> **arpalermo said:**
> SUCCESS! Thank you so much for your help!  MAN I LOVE MY UBUNTUBOX!!
Brilliant, glad to help :)

---

### Post by hetx on 2009-09-19
If you want an FTP share to auto-mount as a drive in Windows on startup, try Netdrive. Just started playing around with it but it seems to work great. You install Netdrive on the Windows machine and add the information for your FTP. Easy alternative to a Samba share

---

