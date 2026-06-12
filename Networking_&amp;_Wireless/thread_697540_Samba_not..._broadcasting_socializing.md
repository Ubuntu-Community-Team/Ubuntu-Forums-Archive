---
title: "Samba not... broadcasting? socializing?"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2008-02-15
I have set up a file/print server with Samba using the most recent Ubuntu server....
I think I have it configured properly, but I can't see it anywhere else on the network. Do I have to say "go" somewhere?
I am using SMB4K to browse the network. (recommend any thing better?)

here is my samba.conf
```

[global]
netbios name = Solomon-Samba
server string = Jones Family File Server
workgroup = COM-CENTER
security = user
hosts allow = 192.168.15.0
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote announce = 192.168.15.255
remote browse sync = 192.168.15.255
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
wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = no
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
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

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
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
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

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
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

[files]
path = /home/files
comment = Group accessed files
valid users = allan, laura, paul, daniela, jr
write list = allan, laura, paul, daniela, jr
admin users = allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[allanfiles]
path = /home/allan
comment = Allan's Files
valid users = allan
write list = allan
admin users = allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[laurafiles]
path = /home/laura
comment = Laura's Files
valid users = laura, allan
write list = laura, allan
admin users = laura, allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no


[danielafiles]
path = /home/daniela
comment = Daniela's Files
valid users = daniela, allan
write list = daniela, allan
admin users = daniela, allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[jrfiles]
path = /home/jr
comment = JR's Files
valid users = jr, allan
write list = jr, allan
admin users = jr, allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[paulfiles]
path = /home/paul
comment = Paul's Files
valid users = paul, allan
write list = paul, allan
admin users = paul, allan
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no


```
[B][U]
Weird things I did that might factor in.[/U][/B]
1. installed Ubuntu server normally... 
2. installed xubuntu desktop afterwards (some apps still won't run off gui... must fix...)
3. saw that my filesystem is still fat32 for some reason... must fix...)
4. Am using GSAMBAD to config samba

Any help would be appreciated.

---

### Post by Iowan on 2008-02-15
I'm certainly no expert (and continue to prove it).  A couple of things I wonder about:  **Hosts allow=** *might* allow the whole subnet - or only IP 192.168.15.0 (an option *might* be **hosts allow = 192.168.15.** to allow the subnet.)  Wish I could check my server, but I'm not where it is.  The other thing I wonder about is whether or not there is a master browser on your network.  Ordinarily the machines all get together (so to speak) and elect one.  Another possible source of problems is firewalling - either on the windows machines or the Samba server.

---

