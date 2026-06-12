---
title: "Shared Drives on Windows Networks"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by jrenaud101 on 2007-07-09
Hi Guys,

Not sure if anyone can help me with this, but here's what I'm trying to do. I'm running the latest release of Ubuntu Server. I have NTFS-3G running to allow me to access my two file sharing drives (that are obviously formatted in NTFS). I have no problems reading and writing to those drives.

I'm trying to share them on my windows network so that windows clients can access the drives, and I'm completely stumped and don't even know where to start.

If it helps, this is the kind of setup I'm trying to achieve:

A local account that has full access over the drives (i.e. Root).
A local user group (networkusers) that has read, write, and execute permissions on the drives, and finally
A local user (guest) that has only read access to the drives.

If anyone can help me out, or at least help steer me in the right direction, I would greatly appreciate it. If you need more information, let me know and I'll post it ASAP.

Thanks in advance!

---

### Post by Norst on 2007-07-10
Although I'm no pro at this, I have had some luck. I'll point you here and this should at least get you started:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by dcolpitts on 2007-07-10
Try this as your smb.conf.  This allows full read/write access to your shared folders without having to log into the linux box with a username / password when browsing from Windows.

[COLOR="Red"]***NOTE*** use this at your own risk - I will not be held responsible for any security issues, etc that arise from the use of this smb.conf.[/COLOR]

```
#============================ Glocal Configuration ===========================
[global]
   workgroup = WORKGROUP
   netbios name = Ubuntu
   server string = Samba Server on Ubuntu
   printcap name = /etc/printcap
   load printers = yes
   printing = lprng
   guest account = root
   log file = /var/log/samba/%m.log
   max log size = 0
   security = share
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 

#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   guest ok = no
   printable = yes
   
[shared]
   path = /shared
   writable = yes
   guest ok = yes
   browseable = yes

```

---

### Post by jrenaud101 on 2007-07-14
Okay, thanks for your posts guys.

I've got this somewhat working, I can access the drives through the network on Windows machines without using a username and password. I'm going to do some more fiddling around to see if I can figure out exactly how to set it up with users and usergroups and maybe post some kind of tutorial.

---

