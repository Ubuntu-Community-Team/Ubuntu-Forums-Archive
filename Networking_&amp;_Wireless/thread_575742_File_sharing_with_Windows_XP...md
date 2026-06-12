---
title: "File sharing with Windows XP.."
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by napoelon on 2007-10-14
So I'm fairly new at Ubuntu and I am having problems with my media server I just setup.

I installed Samba, and my two Linux machines share perfectly fine with it. It's only my Windows XP machine in which I am having issues with.

I go to Network places, and see that my media server is there, when I click on it, it asks me to login. I login, and it keeps on looping its self asking me for the username/pass. I know it's all right.

I attached my smb.conf file

> [global]
    ; General server settings
    netbios name = MEDIA
    
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes
    domain logon = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes


[Media]
path = /storage
available = yes
browsable = yes
public = yes
writable = yes

I followed a guide on how to set this up. ANy help is appreciated since I am trying to move over my media from my Windows machine to this new machine.

Thanks,
nap

---

