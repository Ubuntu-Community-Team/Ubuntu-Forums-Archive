---
title: "Cannot setup Samba"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by bossy22 on 2008-06-06
Hi, 

I've the following Environment: 

A Ubuntu Box (8.04 Hardy Heron upgraded to ubuntu studio) and a macbook pro with leo. 

It's completely impossible for me to "see" leo from ubuntu or vice versa. 

I've tried a lot. 

I activated  shared Folders on Hardy. Samba and smbclient are installed of course. 

I added the leo user to ubuntu and so so on. I am not so new to this. I've set up some networks and everything worked under debian...

What is really is the following: 

I can see Leo from my vmware vista install on Hardy, and I can see that vista from leo!!

And I can reach Hardy from leo via ssh.
```

[global]
netbios name = dantooine
server string = digitalearbeit. Berlin
workgroup = ubuntu
security = share
hosts allow =
interfaces = 127.0.0.1/8 192.168.0.0/24
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = yes
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
#obey pam restrictions = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
#passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g$
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /d$
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no
map to guest = bad user

[homes]
comment = Home Directories
path = /home
read only = no
available = yeswritable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
writable = no
guest ok = no
public = yes
printable = no
share modes = no
locking = no
browsable = yes

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700
browsable = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
guest ok = yes
browsable = yes
public = no
writable = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u


[Ubuntu]
path = /home/dantooine
available = yes
browsable = yes
public = yes
writable = yes

```

I'm pretty stuck here..

thanx in advance

Bossy

---

