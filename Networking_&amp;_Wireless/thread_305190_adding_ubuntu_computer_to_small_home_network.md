---
title: "adding ubuntu computer to small home network"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by JoeC21 on 2006-11-22
Hello all,

I am trying to network three computers in my house.  One windows XP, one Mepis 6.0, and now the ubuntu computer.  I am using samba to share the files between the windows computer and the mepis computer and that is working fine.  I would like to add my ubuntu computer now to that setup so I could share the files between all 3.

The network is probably very insecure but it is working nonetheless.  So far I copied the mepis /etc/samba/smb.conf file from mepis to my ubuntu computer and changed some values to mach this computer.

Here is my smb.conf file...

```
#************************section global**************************
[global]

panic action = /usr/share/samba/panic-action %d
printing = cups
workgroup = mepisgrp
server string = %h server (Samba %v)
hosts allow = 192.168.0. 127.
socket optins = IPTOS_LOWDELAY TCP_NODELAY
log level = 1
dead time = 15
wins support = yes
hide unreadable = yes
passdb backend = tdbsam guest
dns proxy = no
max log size = 1000
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto
oplocks = No
level2 oplocks = No
#************************section joe*******************
[joe]
comment = /home/joe
path = /home/joe
guest ok = yes
read only = no
#***************************section homes************
[homes]
comment = Home Directories
browseable = no
read only =no
*************************section printers******************
[printers]
comment = All printers
path = /tmp
browseable = no
printable = yes
guest ok = yes
create mode = 0700
  
```

I am not trying to share a printer, at least yet, but I added the section anyway.

I am able to ping between all the computers by ip and host name.  I am unable to see the ubuntu computer on the network the same way I can see the other two. Nor can I see either the xp or mepis computer from my ubuntu computer.

Any ideas on how to make this work?  Sorry for the long post but was trying to provide as much detail as possible.  If I was unclear or you need more info just ask and I'll clear up or provide anything you need.

Thanks,
Joe

---

### Post by JoeC21 on 2006-11-23
Nevermind guys, started from scratch and followed the guide here [http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")

and now it is working fine

Thanks anyways,
Joe

---

### Post by wfwoo on 2006-11-24
The url is usefull.
Thanks, Joe

---

