---
title: "Samba (specifically nmbd) bombs system log"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by comintern on 2008-06-10
I seem to have an issue with my Samba configuration that I can't figure out.  I have 2 machines on the network, my wife's Windoze XP box and the Ubuntu box.  I thought I had everything configured correctly (at least all the shares showed up on each machine), but when the Windoze machine was turned off last night, it apparently started bombing my system log with lines of this:

> comintern@fidel:/var/log$ tail syslog
Jun 10 13:29:01 fidel nmbd[6508]:   reload_interfaces: No subnets to listen to. Waiting.. 
Jun 10 13:29:01 fidel nmbd[6508]: [2008/06/10 13:29:01, 0] nmbd/nmbd.c:reload_interfaces(239) 
Jun 10 13:29:01 fidel nmbd[6508]:   reload_interfaces: No subnets to listen to. Waiting.. 
Jun 10 13:29:01 fidel nmbd[6508]: [2008/06/10 13:29:01, 0] nmbd/nmbd.c:reload_interfaces(239) 
Jun 10 13:29:01 fidel nmbd[6508]:   reload_interfaces: No subnets to listen to. Waiting.. 
Jun 10 13:29:01 fidel nmbd[6508]: [2008/06/10 13:29:01, 0] nmbd/nmbd.c:reload_interfaces(239) 
Jun 10 13:29:01 fidel nmbd[6508]:   reload_interfaces: No subnets to listen to. Waiting.. 
Jun 10 13:29:01 fidel nmbd[6508]: [2008/06/10 13:29:01, 0] nmbd/nmbd.c:reload_interfaces(239) 
Jun 10 13:29:01 fidel nmbd[6508]:   reload_interfaces: No subnets to listen to. Waiting.. 

Didn't stop until the drive was full.  I get the same behavior any time that my machine is the only one running on the network.

> 
[global]
netbios name = [SNIP]
server string = [SNIP]
workgroup = [SNIP]
security = share
hosts allow = 127. 192.168.1.
interfaces = 127.0.0.1/8 192.168.1.0/24 
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = cups
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
local master = yes
domain master = no
preferred master = yes
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
guest ok = yes
public = yes
printable = yes
share modes = yes
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

The only other thing I noticed was this from the share log:

> comintern@fidel:/var/log/samba$ tail log.wb-FIDELSHARE
[2008/06/09 18:13:16, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
[2008/06/09 18:13:56, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
[2008/06/09 18:13:56, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
[2008/06/09 18:13:56, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
[2008/06/09 18:13:56, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend

I'm totally lost -- any hints or ideas?

---

### Post by sunbird on 2008-08-07
*Bump*

Having the same problem. 10GB of systemlogs in 10 minutes!!! Help!

---

### Post by bab1 on 2008-08-07
comintern,

Your problem appears to be a deadlock problem.  Deadlocks are where to processes are waiting on each other to complete before moving on.  See [[COLOR="DarkOrange"]this[/COLOR]]("http://linux.about.com/cs/linux101/g/deadlock.htm").

It also appears that your user database is at fault. See> Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
 It looks like it can't find users in the passdb.

I tried a simple google search on [[COLOR="darkorange"]linux samba deadlock[/COLOR]]("http://www.google.com/search?hl=en&q=linux+samba+deadlock") and found others with the same complaint.

I'm certainly no expert in this area, but I hope this helps.

sunbird,

You have to supply some info for someone to respond.  One can't diagnose without some logfiles to look at.

---

### Post by comintern on 2008-08-08
> **bab1 said:**
> comintern,

Your problem appears to be a deadlock problem.  Deadlocks are where to processes are waiting on each other to complete before moving on.  See [[COLOR="DarkOrange"]this[/COLOR]]("http://linux.about.com/cs/linux101/g/deadlock.htm").

It also appears that your user database is at fault. See It looks like it can't find users in the passdb.
Thanks.  I haven't run into any issues with it recently but still haven't figured out the cause.  I suspect that it has something to do with the fact that the XP machine doesn't require any credentials (I can't require a login on that machine because my 6 year old daughter also uses it).  I do have a workaround though -- I moved the samba logs to their own small partition so they can't fill my system partition.

---

