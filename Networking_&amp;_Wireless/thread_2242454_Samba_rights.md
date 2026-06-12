---
title: "Samba rights"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by edlapoignee on 2014-09-01
hi,I've set up a group with 3 users inside it.
I'm trying to set up samba so that all the users can read the files and create some in the share but I don't want them to be able to have write permission if they are not the owner of the file.
my smb.conf[COLOR=#000000][FONT=Arial]
#======================= Global Settings =======================
[global]
### Names ###
    workgroup = 202Cargill
    netbios name = Server
    server string = serveur %h (Samba %v, Debian)
### Wins Server ###    
    wins support = yes
    wins server = 192.168.20.4
### DNS ###
    dns proxy = no
#### Networking ####
    interfaces = 127.0.0.0/8 eth0
    bind interfaces only = yes
    local master = Yes
    os level = 65
### Debugging/Accounting ###
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
### Authentication ###
    security = USER
    valid users = @sambausers
    server role = standalone server
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user    
### Misc ###
    usershare allow guests = no[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#======================= Share Definitions ===================
[Downloads]
    path = /home/server/Downloads
    comment = In progress
    read only = no
    create mask = 0660
    directory mask = 0770
    valid users = @sambausers
======================================================================================================[/FONT][/COLOR]

but it doesnt work, the users can access/create/modify all the files even if they are not the owner.
Is there any way to do that?
Thanks in advance

---

