---
title: "Whats wrong with my smb.conf file ???"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by jrgibb on 2007-09-19
My WIndows Pro laptop just can't see my Ubuntu machine, and from "PLaces" "Network" my Ubuntu machine cannot see other machines on my network. I have a connection to my laptop from the Ubuntu machine using smb://"ip address of laptop" and can copy files from the laptop but can't copy files to the laptop via this connection.

smb.conf file as follows;

[global]

netbios name = name
workgroup = name
server string = name
encrypt passwords = yes
security = user
smb passwd file = /etc/samba/smbpasswd
log file = /var/log/samba/samba.log
socket options = IPTOS_LOWDELAY TCP_NODELAY
domain master = yes
local master = yes
preferred master = yes
os level = 65
dns proxy = no
name resolve order = lmhosts wins bcast
hosts allow = ip address of laptop
printcap name = /etc/printcap
load printers = yes
printing = cups
cups options = raw
guest account = smbguest
max log size = 1000
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
unix password sync = no
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = no
interfaces = ip address of Ubuntu machine 
remote browse sync = 192.168.0.255
remote announce = 192.168.0.255
time server = no
domain logons = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
wins support = yes
wins proxy = no
preserve case = no
;  short preserve case = no
;  default case = lower
;  case sensitive = no
winbind use default domain = yes

Can post other sections if relevant. 

Thanks,

J

---

