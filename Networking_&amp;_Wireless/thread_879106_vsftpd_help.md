---
title: "vsftpd help"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by muted1987 on 2008-08-03
ok so i have setup vsftpd to my requirements but when i type in my internal ip address in another browser nothing comes up just a blank screen and im at a loss as to what im doing wrong


just got this from a command line ftp: connect: No route to host

---

### Post by tamoneya on 2008-08-03
on another machine please install nmap:```
sudo apt-get install nmap
```
Use it to port scan the other machine.

---

### Post by muted1987 on 2008-08-03
this is a problem i dont have another one lying around is there any other way i can check my ports?

although saying that when i type it in my opera browser i get port is disabled how do i enable it

---

### Post by superprash2003 on 2008-08-04
do you have firestarter or anything similar running?

---

### Post by linux6994 on 2008-08-04
Try to load filezilla, its a ftp client that works fine. Just hitting your port 21 with a browser will not pull up the required protocol. I have a ftp server and webserver running on mie. ftpis on port 21 and the web on 80. On most of the ftp servers, I use pureftp as you can see from the attachments.
 The way most ftp sever work is that you have port 21 running and the users are created via the regular System > Admin > Usera and Groups

---

