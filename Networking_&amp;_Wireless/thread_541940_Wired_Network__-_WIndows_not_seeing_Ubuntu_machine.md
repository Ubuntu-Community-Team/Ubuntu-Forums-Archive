---
title: "Wired Network  - WIndows not seeing Ubuntu machine"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by jrgibb on 2007-09-03
HI,

I've got networking enabled on my Ubuntu machine (7.04 Feisty). I have shared drives on my Windows XP Pro laptop and by entering the IP address in the location box I'm able to sign into my laptop from my Ubuntu machine and copy files over (from Win to Ubuntu machine). 

I cannot drop files into the network directory that I can see on the Ubuntu machine (ie to copy files over to the Win machine). 

I cannot see the Ubuntu machine in Windows, nor can I see it using the fixed IP address of the Ubuntu machine. 

Any help welcome please ! 

Jason

---

### Post by darkwyrm on 2007-09-04
What say you post your /etc/smb.conf ? It sounds to me like a misconfigured Samba installation.

---

### Post by jrgibb on 2007-09-05
See below;

Where "DOMAIN" is my LAN domain and xxx.xxx is the IP of my WIn machine.

[global]
netbios name = Hal

workgroup = "DOMAIN"
hosts allow = 192.168.XXX.XXX
printcap name = /etc/printcap
load printers = yes
printing = cups
cups options = raw
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
security = user
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
smb passwd file = /etc/samba/smbpasswd
encrypt passwords = yes
unix password sync = no
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = no
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote browse sync = 192.168.0.255
remote announce = 192.168.0.255
local master = no
os level = 33
domain master = no
preferred master = no
time server = no
domain logons = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
wins support = no

wins proxy = no
dns proxy = no
preserve case = no
;  short preserve case = no
;  default case = lower
;  case sensitive = no
winbind use default domain = yes
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null


If you want specific sections please let me know.

J

---

### Post by darkwyrm on 2007-09-11
Wow. That's a doozy of a config file. Just out of a gut instinct, I have a feeling that you have more there than you need to specify. I guess the question would be what you want to be able to do. Pardon me if these questions sound condescending -- they're not intended that way.

1) Do you want anyone to be able to see the share?
2) Do you want people to have to log in to see the share?
3) Do you want to restrict access to just certain IP addresses?
4) Do you want to share printers, files, or both?

---

### Post by jrgibb on 2007-09-24
Hi,

Thanks for looking at this for me, in reply to your questions;

1) Yes anyone on my LAN
2) Yes
3) Yes, so might not want 2) if restricted IP deals with the security
4) Just file read and write, printer sharing note needed I have a print server.

Many thanks,

J

---

