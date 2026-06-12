---
title: "extra hard drives with ubuntu server and home network"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by pcrat on 2009-11-25
OK,

Im installing Ubuntu 9.10 Desktop edition. Then im going to install Lamp.  That part i have figured out pretty much. But this will be on its own computer. I have 6 other hard drives i want installed in the tower. ive been searching around for this but cant find much of anything. I want to be able to browse any of the hard drives on the linux server from any computer in the house. ( or the internet ). 2 hard drives out of 6, are empty , 4 of them have data on them. all drives are NTFS format.

if anyone has any helpful information.

I want this a webserver AND home server.

Thanks

---

### Post by bodhi.zazen on 2009-11-25
I advise you use Samba.

[Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411") 

What do you need help with ?

---

### Post by pi.boy.travis on 2009-11-25
> **pcrat said:**
> OK,

Im installing Ubuntu 9.10 Desktop edition. Then im going to install Lamp.  That part i have figured out pretty much. But this will be on its own computer. I have 6 other hard drives i want installed in the tower. ive been searching around for this but cant find much of anything. I want to be able to browse any of the hard drives on the linux server from any computer in the house. ( or the internet ). 2 hard drives out of 6, are empty , 4 of them have data on them. all drives are NTFS format.

if anyone has any helpful information.

I want this a webserver AND home server.

Thanks

Samba is good for sharing over the local network, however, for access over the internet, I would advise using authenticated FTP with a dynamic domain name.  I have been doing this with vsftpd and DynDNS for years.  There are extensive instructions in the Ubuntu Server Guide.

---

### Post by pcrat on 2009-11-25
alright, yea ftp is good, i also use dyndns, 

Im new to Samba sharing, i used to use on my xbox, but will read through the guide.

Thanks,,

---

