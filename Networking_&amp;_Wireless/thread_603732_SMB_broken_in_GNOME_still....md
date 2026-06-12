---
title: "SMB broken in GNOME still..."
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by maybeway36 on 2007-11-05
I can use Places>Network to browse to Windows Network, then my workgroup, then a list of computers. However, when trying to access any computers, Nautilus sits doing nothing for a minute and then says "Sorry, could not display all the contents of [my computer name]". Couldn't this error message be a little more descriptive? To get to SMB on GNOME, I need to either use the fstab (which only works with static IP servers) or install Dolphin.

---

### Post by OoooMatron on 2007-11-05
i think your smb.conf file is up the duff. no problems here.

---

### Post by maybeway36 on 2007-11-05
I haven't changed my smb.conf since installation. Borwsing shares with Konqueror works fine.

---

### Post by maybeway36 on 2007-11-06
Does nobody else have this problem? Konqueror has always worked for me, while Nautilus never has. CIFS mounting works fine, but I need to enter the IP address, which is bad for computers with dynamic IPs on the LAN.

---

### Post by maybeway36 on 2007-11-11
It works when I type in the IP address, like:
```
smb:/192.168.1.2
```

---

### Post by Peter09 on 2007-11-11
Check if you can ping your machines by host name. Pinging does not use Samba. I have a problem with DHCP which I think many others have. It does not resolve host names so that anything you do which requires access by host name will not work.

---

### Post by HieroPosche on 2007-11-11
I had this problem for a long time, could browse to the computers, but couldn't access any of the files without Nautilus locking up.  

All changed once I set my Ubunutu pc to a static IP and set up my smb.conf properly.  You may not have changed it since install, but the smb.conf file you get with install is pretty much just a template.  I found a decent smb.conf file on a HOWTO that gave you the basics and showed you what you needed to fill in with your info to make it work. 

Google it and you ought to be able to find one that will work for ya.

Hope that helps.

---

### Post by maybeway36 on 2007-11-12
The problem was that there's really no DNS server in my network. So, I added the line to my smb.conf:
```
name resolve order = bcast
```
and it worked! Thanks!

---

