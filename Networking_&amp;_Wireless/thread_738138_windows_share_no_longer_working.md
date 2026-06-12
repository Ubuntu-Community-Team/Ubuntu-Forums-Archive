---
title: "windows share no longer working"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by gregstyles on 2008-03-28
Ubuntu 7.10.  Windows 2003 server, SNAP server

I have been able to smb mount windows shares from the server and workstation shares until recently.  I'm guessing one of the programs I installed recently is interfering.  All other networking is working fine,  I can "connect to server" for ftp mounts.  any suggestions?  

Thanks

---

### Post by Eiríkr on 2008-03-28
How are you trying to connect?  Try typing in:
```
smb://IP.ADD.RE.SS
```
in Nautilus's location bar (hit Ctrl+L or click View -> Location Bar to display it).  

HTH,

Eiríkr

---

### Post by Iowan on 2008-03-28
> **gregstyles said:**
>   I'm guessing one of the programs I installed recently is interfering.
Out of curiousity - which programs?

---

### Post by gregstyles on 2008-04-02
thanks,
ctrl-L smb://servername = after 30 seconds "folder contents could not be displayed"
crtl-L smb://ip adress = worked

So I can mount the share using the ip adress but not the server name.

---

### Post by A$h X on 2008-04-02
Join the club my friend, I've been banging my head against a brick wall for 2 days trying to sort out the same problem as yours. Out of interest, on the XP machines, does your ubuntu machine show up in "my network places"?

---

### Post by cb951303 on 2008-04-28
it's been the same for me. only ip address gives access to windows share.
to the post above: you should create a samba share if you want to see ubuntu from windows. to do that 

```
sudo apt-get install system-config-samba
sudo touch /etc/libuser.conf 
```

then System>Administration>Samba>Add .....

cheers:popcorn:

---

