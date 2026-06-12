---
title: "Network doesn't see Ubuntu Raring Ringtail or Windows 8 respectively"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by tXtnhFp on 2013-10-07
Hi, 

I'm new to Linux distros, pretty much brand new noob, but have gone through trying to get Win 8 and Ubuntu 13.04 to see each other with Samba to no avail. Samba is installed using the sudo apt-get install commands in terminal, i've gone through preferences to give it the same workgroup name as my Win 8 machine (for ease of use I've kept them as 'workgroup' until I get it working). Files and folders are shared on both machines in their respective ways, but although I can ping each machine's IP from the other, trying to connect to the other machine via the IP doesn't work. The linux machine is a dual boot machine with Win 8, but I wouldn't have thought that would affect matters? 

I've read the other threads on the forum pertaining to this but none of them have helped unfortunately.

My Ubuntu machine name is 'linux-M17x' and I've kept the netbios name the same.

When I start samba I get a warning that some files in the smb.conf couldn't be understood, not sure if this would be a problem? These are:

> 50:     enable spoolss = yes


54:     update encrypted = yes


smb.conf is as follows

> [global]
        netbios name = linux-M17x
        server string = Samba file and print server
        workgroup = workgroup
        security = user
        hosts allow = 127. 192.168.0.
        interfaces = 127.0.0.1/8 192.168.0.0/24
        bind interfaces only = yes
        remote announce = 192.168.0.255
        remote browse sync = 192.168.0.255
        printcap name = cups
;       load printers = yes
        cups options = raw
;       printing = cups
;       guest account = nobody
        log file = /var/log/samba/samba.log
        max log size = 1000
;       null passwords = no
        username level = 6
        password level = 6
;       encrypt passwords = yes
        unix password sync = yes
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
;       local master = yes
        domain master = no
;       preferred master = yes
;       domain logons = no
        os level = 33
        logon drive = m:
        logon home = \\%L\homes\%u
        logon path = \\%L\profiles\%u
        logon script = %G.bat
;       time server = no
        name resolve order = wins lmhosts bcast
;       wins support = no
;       wins proxy = no
        dns proxy = no
;       preserve case = yes
;       short preserve case = yes
        client use spnego = no
        client signing = no
        client schannel = no
;       server signing = no
        server schannel = no
;       nt pipe support = yes
;       nt status support = yes
        allow trusted domains = no
        obey pam restrictions = yes
        enable spoolss = yes
;       client plaintext auth = no
;       disable netbios = no
        follow symlinks = no
        update encrypted = yes
;       pam password change = no
        passwd chat timeout = 120
;       hostname lookups = no
        username map = /etc/samba/smbusers
;       passdb backend = tdbsam
        passwd program = /usr/bin/passwd '%u'
        logon script = %G.bat
;       time server = no
        name resolve order = wins lmhosts bcast
;       wins support = no
;       wins proxy = no
        dns proxy = no
;       preserve case = yes
;       short preserve case = yes
        client use spnego = no
        client signing = no
        client schannel = no
;       server signing = no
        server schannel = no
;       nt pipe support = yes
;       nt status support = yes
        allow trusted domains = no
        obey pam restrictions = yes
        enable spoolss = yes
;       client plaintext auth = no
;       disable netbios = no
        follow symlinks = no
        update encrypted = yes
;       pam password change = no
        passwd chat timeout = 120
;       hostname lookups = no
        username map = /etc/samba/smbusers
;       passdb backend = tdbsam
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
;       winbind refresh tickets = no
;       winbind offline logon = no
;       guest ok = no


[homes]
        comment = Home Directories
        path = /home
        valid users = %U
        read only = no
;       available = yes
;       browseable = yes
;       guest ok = no
;       printable = no
        locking = no
        strict locking = no


[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        read only = no
;       available = yes
;       browseable = yes
;       guest ok = no
;       printable = no
        locking = no
        strict locking = no


[profiles]
        comment = User Profiles
        path = /var/lib/samba/profiles
        read only = no
;       available = yes
;       browseable = yes
;       guest ok = no
;       printable = no
        create mode = 0600
        directory mask = 0700
        locking = no
        strict locking = no


[printers]
        comment = All Printers
        path = /var/spool/samba
;       browseable = yes
;       writable = No
;       guest ok = no
        printable = yes
        locking = no
        strict locking = no


[pdf-documents]
        path = /var/lib/samba/pdf-documents
        comment = Converted PDF Documents
        admin users = %U
;       available = yes
;       browseable = yes
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


Thanks for any help you guys could give!

---

