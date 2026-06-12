---
title: "Creating multiple shares with different password settings in Samba"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by jimbobthehick on 2014-01-22
Hello all,

I am using Ubuntu server 12.04 and am trying to separate samba shares and accessibility for them.

For instance, some of my shares I want to be accessible without login, whereas some I want to be secured with a username and password.

Things I have tried:

My current settings (below) are almost what I need, they allow access to my shared files to anyone without logins being asked for, and a password is asked for by my protected directory, HOWEVER no logins work.
When I changed **[global] security = user ** it resulted in a single password being required to access my server (with all shares).  My login did work, but this isn't adequate as my shared files need to be accessible without a login, and I actually need to be able to log into (only) my protected directory.

My settings are below:

[Global]
workgroup = WORKGROUPNAME
server string = YADAYADA
netbios name = NAMEGOESHERE
hosts allow = 10.10.10.
smb passwd file = /etc/samba/smbpasswd
dns proxy = no
security = share
usershare allow guests = yes
hide files = /lost+found/

[Shared Files]
comment = Anyone is welcome
path = /path/to/files
available = yes
browseable = yes
guest ok = yes
read only = no
public = yes
writable = yes
create mask = 0777
directory mask = 0777

[Protected Files]
comment = password protected files
path = /another/path/to/files
available = yes
browsable = yes
guest ok = no
read only = no
public = no
writable = yes
create mask = 0777
directory mask = 0777

A developed solution or any readable (and understandable) resources would be appreciated.

---

