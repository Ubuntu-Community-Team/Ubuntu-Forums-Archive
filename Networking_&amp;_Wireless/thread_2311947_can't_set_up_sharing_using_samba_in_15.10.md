---
title: "can't set up sharing using samba in 15.10"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by AbhimanyuAryan on 2016-01-31
):P[COLOR=#111111][FONT=Ubuntu]I have installed samba and have set up samba with the below commands

[/FONT][/COLOR]```
# mkdir -p /srv/samba/share
# chown nobody.nogroup /srv/samba/share/
# restart smbd
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
# restart smb
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
# /etc/init.d/smbd start
[ ok ] Starting smbd (via systemctl): smbd.service.
# /etc/init.d/smbd restart 
[ ok ] Restarting smbd (via systemctl): smbd.service.
# service smbd status
&#9679; smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
   Loaded: loaded (/etc/init.d/smbd)
   Active: active (running) since Sun 2016-01-31 22:13:34 IST; 22s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 5883 ExecStop=/etc/init.d/smbd stop (code=exited, status=0/SUCCESS)
  Process: 5893 ExecStart=/etc/init.d/smbd start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/smbd.service
           &#9500;&#9472;5909 /usr/sbin/smbd -D
           &#9492;&#9472;5927 /usr/sbin/smbd -D

Jan 31 22:13:33 acer-ubuntu systemd[1]: Starting LSB: start Samba SMB/CIFS d....
Jan 31 22:13:34 acer-ubuntu smbd[5893]: * Starting SMB/CIFS daemon smbd
Jan 31 22:13:34 acer-ubuntu smbd[5908]: [2016/01/31 22:13:34.717634,  0] ../...)
Jan 31 22:13:34 acer-ubuntu smbd[5908]:   Ignoring unknown parameter "passwo..."
Jan 31 22:13:34 acer-ubuntu smbd[5908]: [2016/01/31 22:13:34.723980,  0] ../...)
Jan 31 22:13:34 acer-ubuntu smbd[5908]:   Ignoring unknown parameter "update..."
Jan 31 22:13:34 acer-ubuntu smbd[5893]: ...done.
Jan 31 22:13:34 acer-ubuntu systemd[1]: Started LSB: start Samba SMB/CIFS da....
Jan 31 22:13:34 acer-ubuntu smbd[5909]: [2016/01/31 22:13:34.884520,  0] ../...)
Hint: Some lines were ellipsized, use -l to show in full.
```


[COLOR=#111111][FONT=Ubuntu]Also,I have to much in my smb.conf file. I don't know where it came from. What I have set is the last [/FONT][/COLOR]```
[share]
```[COLOR=#111111][FONT=Ubuntu] at the end of the file

[/FONT][/COLOR]```
[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = Ubuntu
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
null passwords = no
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
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
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
guest ok = no
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


[share]
    comment = This Ubuntu File share Server
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
```

---

