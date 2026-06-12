---
title: "Trying to connect to other computers, login credentials keep failing."
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by rusty7600 on 2014-04-25
So I'm trying to get access to my windows 8 laptop from my desktop (running Ubuntu 14.04). I installed samba, after looking at a few guides. I can see my laptop on the file browser, but whenever I enter the credentials, it always fails. I don't get an error or anything, the login box just pops up again. I installed samba-config-tool, but I do not see any such tool when I type it in. I eventually saw a program on the Software center called Gadmin-Samba, and installed that to see if that would help. It didn't. It did give me an interface to configure samba with though.
Here's what the smb.conf file looks like. Gadmin Samba overwrote it, so it looks slightly different than what it looks like by default.
```



[global]
netbios name = Ubuntu
server string = Samba file and print server
workgroup = WORKGROUP
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = yes
username level = 6
password level = 6
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
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
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
passdb backend = tdbsam
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
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = no
printable = no
locking = no
strict locking = no


[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no


[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no


[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no


[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no


[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =
```

---

### Post by bab1 on 2014-04-25
> **rusty7600 said:**
> ...i'm trying to get access to my windows 8 laptop from my desktop (running Ubuntu 14.04). I installed samba...

There shouldn't be any need to install Samba server if all you are doing is using Samba as a client (your scenario above).  All the client routines are installed by default.
> 
 I installed samba-config-tool, but I do not see any such tool when I type it in. I eventually saw a program on the Software center called Gadmin-Samba, and installed that to see if that would help. It didn't. It did give me an interface to configure samba with though.
Here's what the smb.conf file looks like. Gadmin Samba overwrote it, so it looks slightly different than what it looks like by default.
[
Gadmin is definably not for what you want to do.  Gadmin is for Samba in a Active Directory environment.  I'd purge all of Gadmin and revert to the original /etc/samba/smb.conf file to start with.

If you are going to serve files from Ubuntu 14.04 be aware that this is the first version that uses Samba4 by default and most tutorials are all about creating an SD environment.  You can however use Samba4 to create a standalone server as a NAS if you wanted to.

---

