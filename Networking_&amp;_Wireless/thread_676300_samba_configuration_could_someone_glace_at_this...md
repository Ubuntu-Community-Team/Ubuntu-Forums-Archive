---
title: "samba configuration could someone glace at this.."
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by vamp4life666 on 2008-01-23
I'm pretty new to Ubuntu, but I am coming along pretty quick whit samba.

I have created a directory   /users   that I am trying to share to my Win XP boxes.

I think my smb.conf file is a bit off and I'm not sure where. Anything I can cut out of here to simplify it would also be helpful...

[global]
security = share
log file = /var/log/samba/log.%m
guest account = michael
passwd chat = *Enter\snew\sUNIspassword:* %n\n *Retype  (this thing just keeps going...)
socket options = TCP_NODELAY
obey pam restrictions = yes
write list = michael, guest, @users, @adm,@admin,@guest
public = yes
passdbprogram = /usr/bin/passwd %u
passdb backend = tbdsam
dns proxy = no
writable = yes
path = /users
os level = 20
valid users = michael, guest, @adm, @admin, @michael
syslog = 0 
panic action = /usr/share/samba/panic-action %d
preferred master = no
max log size = 1000

; wins support = yes

; wins server = w.x.y.z

; name resolve order = lmhosts wins bcast

; interfaces = 127.0.0.0/8 eth0

; bind interfaces only = true

; security = user

; guest account = nobody

; unix password sync = no

; pam password change = no

; domain logons = yes

; logon path = \\%N\profiles|%U


I also have:

[homes]
[netlogon]
[profiles]
[printers]
[print$]
[cdrom]
[image]

---

### Post by vamp4life666 on 2008-01-23
sudo testpram /etc/samba/smb.conf

gave me Global parameter security in service section! 
if that helps any?

---

### Post by vamp4life666 on 2008-01-23
anybody.....?

---

### Post by swerdna on 2008-01-23
Hi: Change this:
> 
[global]
security = share
log file = /var/log/samba/log.%m
guest account = michael
passwd chat = *Enter\snew\sUNIspassword:* %n\n *Retype (this thing just keeps going...)
socket options = TCP_NODELAY
obey pam restrictions = yes
write list = michael, guest, @users, @adm,@admin,@guest
public = yes
passdbprogram = /usr/bin/passwd %u
passdb backend = tbdsam
dns proxy = no
writable = yes
path = /users
os level = 20
valid users = michael, guest, @adm, @admin, @michael
syslog = 0
panic action = /usr/share/samba/panic-action %d
preferred master = no
max log size = 1000
to this:
> [global]
workgroup = NAME_OF_WORKGROUP
netbios name = name_of_this_workstation
security = user
name resolve order = bcast lmhosts wins host
server string = ""
map to guest = Bad User
local master = yes
preferred master = yes
os level = 65

Replace  NAME_OF_WORKGROUP with the name of the windows workgroup as named in the windows machine/s, often but not necessarily either "WORKGROUP" or "MSHOME". Check in windows at R-click My Computer --> Properties --> Name/Identity or like that.

Replace  name_of_this_workstation with the name you want the computer to have in the network browser, recommend the same as the hostname that you see in a terminal after the ampersand at the prompt.

Notice that I've separated the share from the [global] parameters. Beneath/separate from the [global] paragraph you can define a share. There are many options. Here's a share  definition that shares michael's home folder/s. It's a roaming share so michael can log on from anywhere: make for it this paragraph:

> [homes]
comment = Home Directories
valid users = %S, %D%w%S
browseable = No
read only = No
inherit acls = Yes

In network browser windows goto \\netbiosname\michael
In Linux goto smb://netbiosname/michael
(instaed of netbiosname use the real netbios name spoke about that above)

Yopu will need to add michael to the Samba user database on Ubuntu. Use this command:
> sudo smbpasswd -a michael

reboot to hard wire.

If you prefer a different type of share, describe it and I will tailor-make one for you.

Swerdna

---

### Post by vamp4life666 on 2008-01-24
I got it working...   it read wirtable to my mac and my XP   but now i have a new problem I wanted to move the drive into a diffenent tower with a bigger processor and a more ram without having to reinstall the entire os and relive settign up samba....      and the eth) does not come up at all... i posted a more detailed bit of info here.... [http://ubuntuforums.org/showthread.php?t=677007](http://ubuntuforums.org/showthread.php?t=677007)

if you could give it a glance

---

