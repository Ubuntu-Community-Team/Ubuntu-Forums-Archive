---
title: "Can't see XP and Ubuntu machines"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by hoisin on 2007-07-12
Hello everyone --

I've recently tried to set up my wireless network to share files through samba between my XP box and my Ubuntu box, but to no avail.  The even with a pure vanilla smb.conf, I still can't get XP to even see my Ubuntu machine and vice versa.  I can ping the XP machine from Ubuntu, as I've updated the /etc/hosts file to do so.  However, I can't ping my Ubuntu box from XP using its host name - pinging the ip address works just fine.

Just to confirm:  all machines are part of the same workgroup.  I've got all SMB related ports opened up on my Ubuntu machine and swat is working beautifully on localhost.

Here's my smb.conf.


[global]
workgroup = GANAMEDE
security = share
wins support = no
netbios name = jupiter

[homer]
path = /home/homer
available = yes
browseable = yes
public = yes
writable = yes


I've been racking my brains over this for two days now.  Please, help!


Thanks!


--hoisin

---

### Post by drhavanger on 2007-07-12
i had the same problem as you.  i couldn't find out what the daemon or service name was for samba with Ubuntu.  checked out top and system monitor, couldn't see anything closely related to samba.  my fix was to fire up my old computer and install fedora on it. now i can share files between my xp and Ubuntu computers with my fedora computer.  i realize this may not work for everyone.

---

### Post by davidsrsb on 2007-07-12
Are your netmasks the same, it should not matter but actually does

---

