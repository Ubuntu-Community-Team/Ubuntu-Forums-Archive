---
title: "Users can acces  all files onces logged in on windows."
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by lousden on 2019-01-31
Im setting up a network between a Linux machine and Windows machine. But once a user logs in by using the windows security login, all files become accesable. even while i've configured it so it wont be posible. can someone help me out? 

this is for educational purpose , and im using virtualbox.

my smb.conf :
```
# smb.conf is the main Samba configuration file. You find a full commented# version at /usr/share/doc/packages/samba/examples/smb.conf.SUSE if the
# samba-doc package is installed.
[global]
    workgroup = WORKGROUP
    passdb backend = tdbsam
    printing = cups
    printcap name = cups
    printcap cache time = 750
    cups options = raw
    map to guest = Bad User
    include = /etc/samba/dhcp.conf
    logon path = \\%L\profiles\.msprofile
    logon home = \\%L\%U\.9xprofile
    logon drive = P:
    usershare allow guests = No
    wins support = No
    wins server = 
    security = user
[homes]
    comment = Home Directories
    valid users = %S, %D%w%S
    browseable = No
    read only = No
    inherit acls = Yes
[profiles]
    comment = Network Profiles Service
    path = %H
    read only = No
    store dos attributes = Yes
    create mask = 0600
    directory mask = 0700
[users]
    comment = All users
    path = /home
    read only = No
    inherit acls = Yes
    veto files = /aquota.user/groups/shares/
[groups]
    comment = All groups
    path = /home/groups
    read only = No
    inherit acls = Yes
[printers]
    comment = All Printers
    path = /var/tmp
    printable = Yes
    create mask = 0600
    browseable = No
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/drivers
    write list = @ntadmin root
    force group = ntadmin
    create mask = 0664
    directory mask = 0775


[Horizon_Purmerend]
    comment = testevenmaar
    inherit acls = Yes
    path = /home/charelison
    read only = No


[Toetsen]
    inherit acls = No
    path = /data/Toetsen
    read only = No
    force group = Docenten


[Huiswerk]
    comment = 
    force group = Leerlingen
    inherit acls = No
    path = /data/Huiswerk
    read only = no
[huis]
    comment = test
    force group = Docenten
    read only = no
    path = /data/Toetsen
    guest ok = no
    
```

my testparm :
```
linux-bo3r:/etc/samba # testparmLoad smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Can't find include file /etc/samba/dhcp.conf
Processing section "[homes]"
Processing section "[profiles]"
Processing section "[users]"
Processing section "[groups]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Horizon_Purmerend]"
Processing section "[Toetsen]"
Processing section "[Huiswerk]"
Processing section "[huis]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE 
```
excuse me for bad english.

---

### Post by lousden on 2019-02-03
Bump

---

