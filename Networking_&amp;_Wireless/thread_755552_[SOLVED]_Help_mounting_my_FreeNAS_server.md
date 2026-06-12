---
title: "[SOLVED] Help mounting my FreeNAS server"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by LieToPurify3 on 2008-04-14
I've been searching here trying to find an answer, but I can't get mine to work and dont really know how to piece together all the info in separate locations.  I have a freeNas server on my network and i need to know how to mount it.  On my XP machine, i have it set to mount as 192.168.1.105.  I can give you any other info that i'll need.  I just dont know what info i really need :(

---

### Post by LieToPurify3 on 2008-04-15
bump. come on this should be an easy answer. i just dont know what im doing lol

---

### Post by Iowan on 2008-04-15
[Here]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") is a link for mounting Samba shares - IF FreeNAS is setup as a Samba server.  I should point out that **smbfs** has been replaced with **cifs**.

---

### Post by him610 on 2008-04-15
Did you read the documentation and set it up as described in the documentation? It needs to be configured properly on the server itself (freenas); your WinXP machine will be the client. 
I have 'freenas' set up one one of my older machines.  I set it up exactly as the documentation said and I have had no problems accessing it from 4 WinXP machines and 4 _buntu machines.
Gotta' run, good luck!

---

### Post by LieToPurify3 on 2008-04-15
Thanks! I think the problem that I was having was I hadn't set up shares in my nas.  I mounted it to /home/user/Storage, but is there any way to mount this on my desktop as a drive?

EDIT:  I mounted it by just creating  a URL link shortcut on my desktop and using the file path as the url.  I guess thats good enough :)  Thank you again

---

