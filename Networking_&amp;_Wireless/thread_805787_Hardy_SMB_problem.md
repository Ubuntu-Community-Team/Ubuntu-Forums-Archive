---
title: "Hardy SMB problem"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Gone fishing on 2008-05-24
I can't connect to a  SAMBA share using the connect to server wizard, it just gives the error 

“Can't display location "smb://192.168.1.1/" No application is registered as handling this file” 

This is a problem in 8.04 it wasn't a problem in earlier versions and seems to be a reported bug anyone know a work round?

---

### Post by superprash2003 on 2008-05-24
192.168.1.1 normally is a router's ip.. but if you are sure its a pc ip. then firstly ensure that you are able to ping 192.168.1.1

---

### Post by Gone fishing on 2008-05-25
No it's the PC I can ping in fact I can Ftp into the box which is the work round I'm using - for some reason with 8.04 you cant connect to a SMB share with user level security. This was no problem with 7.10

---

### Post by SleeperGTP on 2008-06-09
I am having this issue also, I am able to ping the host, but unable to mount.

-Chris

---

### Post by Drengur on 2008-06-13
Same problem.

Bugs the hell out of me because I cannot use the network printer since Samba does not work at all.

Any solutions yet?

---

### Post by jimv on 2008-06-13
What if you do smb://your-server/your-share-name

And do this in the Nautilus address bar, not the wizard

---

### Post by kextyn on 2008-06-15
> **jimv said:**
> What if you do smb://your-server/your-share-name

And do this in the Nautilus address bar, not the wizard

I'm not sure how related my problem is.  I just installed Samba and created a share that appears to be configured correctly.  When connecting from a Windows PC it appeared to get past authentication and then it would say it couldn't connect.

I tried the smb://server/share from the server and it said it couldn't mount the Windows shawn.

---

