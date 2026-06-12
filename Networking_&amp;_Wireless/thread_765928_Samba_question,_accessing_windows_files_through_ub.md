---
title: "Samba question, accessing windows files through ubuntu"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by jazzman14 on 2008-04-24
Hi,

I have samba set up. I have win xp on my laptop, both on the same network. I can access the folder i set up with ubuntu on my xp computer, i just go to my computer and click on the network drive. Now, before I switched os's on my laptop, I used to be able to click places|network|laptop and i would be able to view all the contents of my laptop through ubuntu's file explorer, I can't do this any longer, how can I be able to do this again?

BTW, here's smb.conf:

```
[global]

    ; General server settings

    netbios name = kenny-desktop

    server string =

    workgroup = WORKGROUP

    ; General server settings

    netbios name = kenny

    server string =

    workgroup = WORKGROUP

    announce version = 5.0

    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192



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



[MyFiles]

    path = /home/samba

    browseable = yes

    read only = no

    guest ok = no

    create mask = 0644

    directory mask = 0755

    force user = kenny

    force group = kenny

    announce version = 5.0

    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192



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



[MyFiles]

    path = /home/samba

    browseable = yes

    read only = no

    guest ok = no

    create mask = 0644

    directory mask = 0755

    force user = kenny

    force group = kenny
```

---

### Post by jazzman14 on 2008-04-27
bump

---

### Post by Iowan on 2008-04-27
Probably not the issue - but did you notice that you have two (different) general server settings?

I may be confused about which machine has the new OS.  Was that new OS Hardy?  (Seems to be several threads about file sharing problems).

On further inspection, the file seems to have several duplicate sections - some general settings under the share...

Need a fresh copy?

---

