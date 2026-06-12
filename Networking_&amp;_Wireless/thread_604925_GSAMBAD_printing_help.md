---
title: "GSAMBAD printing help"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2007-11-06
I just installed Gutsy and I am trying to use GSAMBAD to use this computer as a print server to 2 XP computers.

right now I see nothin' from my XP computers when I try to add the printer. I don't even see the PDF printer. I have attached my smb.conf file to try to help.


Thanks for any and all help!
Willz06jw

Quote:
[global]
netbios name = willbuntu
server string = Ubuntu Printer Server
workgroup = NERDHOUSE
security = user
hosts allow = 127. 192.168.0.
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

---

### Post by momist on 2008-02-18
I'm struggling with Gsambad as well.  Did you ever resolve this?  Is so, how?
Please.
Pretty please.

---

### Post by psyburn on 2008-02-18
For the sharing part it's easier to set up a HTTP/IPP share using CUPS.

---

### Post by momist on 2008-02-18
Aha!  I found this:
 [http://ubuntuforums.org/showthread.php?t=202605&highlight=gsambad](http://ubuntuforums.org/showthread.php?t=202605&highlight=gsambad)
which has solved everything for me!  Never mind Sambad - back to the command line and edit the config file!

Yeah, I've fixed it.  And the HowTo worked OK for me, although I see others have issues.

---

