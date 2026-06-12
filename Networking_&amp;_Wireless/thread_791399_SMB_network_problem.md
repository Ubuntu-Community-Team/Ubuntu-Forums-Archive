---
title: "SMB network problem"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by thun on 2008-05-12
Hi! Im back to linux after a 4 long break so sry for not being to updated, but my problem is when im trying to connect to my windows machine in the local network, i can see the computer but when i klick on it it dosnt ask for anny username or psw, so natrualy i cant connect and see anny folder. i can enter my ubuntu machine from xp with psw and username but not vice versa. hope u can help me just write if i have missed on telling annything.. 
sry for my poor english and hope i post this one in the right forum!

/Thun

---

### Post by bobblehat on 2008-05-12
It'd help to know what version of Ubuntu you're using but in the meantime in the Nautilus file manager you could try File -> Connect to Server -> fill out your details and see if that helps you.

---

### Post by Shiv Prakash on 2008-05-12
this seems to be quiet a common problem:mad:

i generally try smb://<windows system name>/ to access other systems on LAN...

**Places->Network just doesn't work**...as a matter of fact only a few times has ubuntu 8.04 detected other systems on LAN right after boot even though using **$sudo nbtscan** i can detect other machines (you should try this also just to be sure everything is working fine)

Another thing you can do is to uninstall Network manager which created a lot of mess...

---

