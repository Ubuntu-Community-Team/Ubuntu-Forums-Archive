---
title: "How do i share a printer installed on linux with a Windows XP machine"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by connel on 2007-06-28
Hi, my brother has a Windows XP based PC. I have a Kubuntu / Windows XP dual boot PC. However when my borther wants to print his home work for example i have to reboot into XP which is quite annoying. How can i share a printer that is connected to a Linux Machine with a XP machine. What packages do i need to install and how do i use them. Sorry you must have loads of questions like this but all the other guides i have seen have the printer connected to the windows machine. Thnx in advance Connel.

---

### Post by wjp.reg on 2007-06-28
This might help

[https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7]("https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7")

good luck

---

### Post by connel on 2007-06-28
where is smb.conf located?(thnxs for the fast reply btw)

---

### Post by wjp.reg on 2007-06-28
> **connel said:**
> where is smb.conf located?(thnxs for the fast reply btw)

gksudo gedit /etc/samba/smb.conf


good luck!

---

### Post by t4thfavor on 2007-06-28
Its really quite easy, the only problem  I ran into was the windows box not likeing the driver for the shared printer. So i ended up adding the printer as a unix printer (Cant remember how) and it worked fine. You may or may not have this problem. just thought you should know.

---

