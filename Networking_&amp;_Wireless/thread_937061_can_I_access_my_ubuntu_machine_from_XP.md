---
title: "can I access my ubuntu machine from XP"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by michael@cgl on 2008-10-03
Having had my last query solved :-)

can I now access my ubuntu machine through my xp desktop ?

michael

---

### Post by tonyh6243 on 2008-10-03
Absolutely,

You can create a Samba share that will allow access over a local network. 

Open a terminal and type sudo apt-get install samba

Refer to [http://us1.samba.org/samba/](http://us1.samba.org/samba/) for some help in configuring your samba configuration file which is located in /etc/samba/smb.conf

---

### Post by michael@cgl on 2008-10-03
i dont even know where to start RE configuringn the file, but I will look on the site and see if its obvious.
thanks for your help so far, I might be back for more :-) . . . . .

---

### Post by michael@cgl on 2008-10-03
ok ive got the smb.conf open and looking through it. I pretty much bummed my way through W****Ws, so Im not too hot on what this file is saying, though I am good at bumming

what kind of thing am i looking to change / setup within this file ?

M

---

### Post by iponeverything on 2008-10-03
Just copy the orginal to a backup for a reference and use stripped down config like this: -- Just change the name of directory that your sharing and interfaces line..  

# smb.conf ================================
[global]
   workgroup = Ubuntu
   server string = Yo (Samba, Ubuntu)
   dns proxy = no
   netbios name = Music
   interfaces = eth0
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   default = Music
   path = /music
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   guest account = nobody
   local master = yes
   domain master = yes
   preferred master = auto
   wins proxy = yes
   browseable = yes

[Music]
   comment = Music
   path = /music
   browseable = yes
   read only = yes
   guest ok = yes

---

### Post by howefield on 2008-10-03
iponeverything : Is the above the same as right clicking the folder to be shared and selecting sharing options ?

---

### Post by Iowan on 2008-10-03
You should get some good information from [this]("https://help.ubuntu.com/community/SettingUpSamba") page. [Here]("http://ubuntuforums.org/showthread.php?t=202605") is another good How-To.

---

