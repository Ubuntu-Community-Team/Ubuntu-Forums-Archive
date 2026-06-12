---
title: "Windows is doing better!"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by TironN on 2009-11-11
So I have finally set up a share using webmin & samba to get files from my 9.10 server to my windows computer, but now I don't know how to set it up to work with Linux!

So how would I get a fileshare of the same location (/home/public) on my Ubuntu workstation! I can use ssh if its easier!

Thanks guys, Fergus

---

### Post by jnorthr on 2009-11-11
this may help: [https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---

### Post by jbrown96 on 2009-11-11
If I understand you correctly, you have a Ubuntu server that is sharing files via Samba. Now you need to connect your Ubuntu desktop to it? 

In Places-->Connect to server, you can connect to a Samba server. Just put in the ip address, choose samba, and enter your login info. You can save the username and password, and create a link to it. Then you just have to double click on the link in the future; no need to type ip addresses or login stuff every time.

---

### Post by TironN on 2009-11-11
> **jbrown96 said:**
> If I understand you correctly, you have a Ubuntu server that is sharing files via Samba. Now you need to connect your Ubuntu desktop to it? 

In Places-->Connect to server, you can connect to a Samba server. Just put in the ip address, choose samba, and enter your login info. You can save the username and password, and create a link to it. Then you just have to double click on the link in the future; no need to type ip addresses or login stuff every time.

Ok I am doing connect to server but I don't see an option for samba. Where is it?

---

### Post by jbrown96 on 2009-11-11
There should be a drop-down menu where you select the type. It should be something like Windows Shares (Samba), Samba, or SMB/CFS.

---

### Post by TironN on 2009-11-11
Oh I got it going now! Ok so how would I go about networking my printer (a Fuji Xerox Phaser 3124) with samba so I could print from my Windows computer to the server.

---

