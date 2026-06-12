---
title: "Samba: Unable to Browse Win XP via Network"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by Erlander on 2007-04-01
This is a problem I have been unable to fix for some months.  Originally I had it on Edgy and now have the same problem on Feisty.

I am unable to browse my Win XP Home pc from my Ubuntu pc via the wired network but can browse it from another Win XP pc on the same network

I have used this guide [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) to set up my Samba network.  From the Windows Home pc I can then browse the shared folders on the Ubuntu pc but get the Access Denied message if I try to browse the shared windows folders from Ubuntu.

As a work around I have used this guide [http://www.ubuntuforums.org/showthread.php?t=288534&highlight=wins](http://www.ubuntuforums.org/showthread.php?t=288534&highlight=wins) to mount a shared folder from my Windows pc onto the Ubuntu desktop.  This also works.

What am I doing wrong?  I would like to just be able to Browse the shared Win XP folders.

My smb.conf follows.

Rob

```
[global]
    ; General server settings
    netbios name = Ubuntu
    
    workgroup = Erlander
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = Share
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
    path = /home/rob/mythtv-setup
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rob
    force group = rob
available = yes
browsable = yes
public = yes
writable = no

[Downloaded]
    path = /home/rob/downloaded
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rob
    force group = rob
available = yes
browsable = yes
public = yes
writable = no

[MythtvCapture]
    path = /var/lib/mythtv
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rob
    force group = rob
available = yes
browsable = yes
public = yes
writable = no
```

---

