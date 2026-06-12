---
title: "Can't Print through Samba"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Drezliok on 2008-04-28
I have 3 computers.
One windows laptop
One duel Boot XP and Ubuntu [hardy]
And finally one Xubuntu [hardy] File/Print/Torrenting Server[It's really Xubuntu desktop install]

I used to be able to print from it but after a security update to the cups server back in gutsy it failed to wrok. I have tried and tried and tried to get it to work and then I did an upgrade hoping it would fix the issue. Although it did replace the Cups configuration it did not fix the pronblem.


Here is my Samba.conf
```

[global]
    ; General server settings
    netbios name = Slave
    
    workgroup = REKAB
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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

;[template]
    path = /home/master/template
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = master
    force group = master

[Torrent]
    path = /home/master/Torrent
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = master
    force group = master


[Slave Media]
    path = /home/master/slavemedia
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = master
    force group = master

```

I am using Stormbringers config only modified slightly  [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+cups+stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+cups+stormbringer)

---

### Post by Drezliok on 2008-04-28
Did I put this in the right forum?

---

### Post by Drezliok on 2008-04-28
> **Drezliok said:**
> Did I put this in the right forum?

No response...

---

