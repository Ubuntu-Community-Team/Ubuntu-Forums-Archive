---
title: "Samba server not accessible though it shows up on network neighborhood"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by therrera1550 on 2015-02-14
Hi,

I accidentally deleted my samba server share called "workstations".  The server defaulted to "samba24".  I kept the name.  Samba24 can be pinged from a windows workstation and from a virtual windows workstation running on the Linux server.  However the share, though it shows up is not accessible and any attempt to make it accessible is met with the message "\\samba24 is not accessible,  You might not have permission to use this network resource.....etc. etc.

It has a share called "workstations" which dropped off the list of network neighborhood shares.  The virtual pc is the only machine that can see the the Samba server but the share is no longer visible on the virtual pc as well as on the workstations on the network.

It was working fine and then in an effort to assign a user to the server that had admin rights on a network PC I erased the share name.  Its when I recreated it that the problem occurred and I've double and tripled checked myself and can't find why it is not working.  Is it possible that re using the old share name that I deleted is a NO NO in Linux??

Anyone have an idea what has happened and how I go about fixing it?

Thanks,

Tony

---

### Post by TheFu on 2015-02-14
Perhaps if you posted the configuration files, someone could help? At this point, we haven't a clue.

Reusing a share name isn't any issue. There isn't some hidden, magical, binary settings file buried somewhere on Linux for this stuff.

---

### Post by therrera1550 on 2015-02-14
Hi,

here is the config file.  Thanks for any help.




[global]
netbios name = samba24
server string = Samba file and print server
workgroup = phoenix
security = user
hosts allow = 127.0.0.1 192.168.13.0/24
interfaces = 127.0.0.1/8 192.168.13.0/24
    bind interfaces only = yes
remote announce = 192.168.13.255
remote browse sync = 192.168.13.255
printcap name = cups
cups options = raw
log file = /var/log/samba/samba.log
max log size = 1000
username level = 6
password level = 6
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
dns proxy = no
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
follow symlinks = no
update encrypted = yes
passwd chat timeout = 120
username map = /etc/samba/smbusers
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
    Map to guest = Bad User

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    read only = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/lib/samba/profiles
    read only = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /var/lib/samba/pdf-documents
    comment = Converted PDF Documents
    admin users = %U
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

[workstations]
    path = /home/workstations
    comment = workstation backup location
    valid users = admin, backup, linda, root, tony
    write list = tony linda admin
    writeable = yes
;    available = yes
;    browseable = yes
;    printable = no
    locking = no
    strict locking = no

---

