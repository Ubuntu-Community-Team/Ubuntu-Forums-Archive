---
title: "Between ubuntu filesharing with samba"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Bobryuu on 2007-08-13
I've got Ubuntu installed on my pc and my laptop, and I'd like to be able to share videos between each.  I've got Samba set up on both, but I can't seem to find the machines.

this is my smb.conf

```
[global]
    ; General server settings
    netbios name = CHARON
    server string =
    workgroup = ELYSIUMFIELDS
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
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

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[CharonVideos]
    path = /home/bobryuu/Videos
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = boryuu
    force group = bobryuu
```

What should I do

---

### Post by pyronicte on 2007-08-25
Hi,

In this section uncomment the following:
[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    browseable = no
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

After that, you must create in the server the same user you access in client with adduser command, and assign a samba password with sudo smbpasswd -R your_client_username.

In order to mount automatically the folders as drives in your client, create an entry for each share in /media, and edit /etc/fstab and add these lines:

//SERVER_NAME/shared_folder /media/folder_you_create smbfs ip=your_server_ip,username=username_you_created,password=password_you_assigned,user,rw,noauto 0 0

run /etc/init.d/smb restart and you got it.

---

