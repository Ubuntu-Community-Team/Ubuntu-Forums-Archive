---
title: "Mounting network drive?"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-07-25
I've got a laptop and desktop. Desktop is dual-boot WinXP and Ubuntu. Laptop is pure Ubuntu box.

If my desktop is booted as WinXP machine, I have no problem to mount a directory using 
```
sudo mount //10.0.0.11/wine /media/music
```, where wine is fat32 partition (Drive E in windows terms).

However, when my desktop is booted in Ubuntu and I want to mount the same, I cannot do it.

It says it the HOWTO that I should use something like this:

```
sudo mount //10.0.0.11/fat32/E/mp3 /media/music -o username=myusername,password=mypassword,dmask=777,fmask=777
``` 

If I try my username and my password I use to login in Ubuntu desktop, I have 
```
15196: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
``` 

Actually the HOWTO says that I should use the username and password of the computer. But I have no idea what are they. I just installed Samba and shared teh folders without assigning any username and password to my desktop.

Anyone to help me out, please?

---

### Post by foxy123 on 2005-07-25
well, I created a user in Samba, so I can mount the share. The problem is that I still not able to mount it as I need. Basically it is shared as a /windows directory called fat32. I can mount /10.0.0.11/fat32 without any problem. But if I try ```
mount /10.0.0.11/fat32/E/mp3
```  I've got 
```
9142: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
``` 

what I did wrong?

---

