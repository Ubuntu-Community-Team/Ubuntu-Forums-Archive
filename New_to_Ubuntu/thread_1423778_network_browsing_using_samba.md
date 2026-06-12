---
title: "network browsing using samba"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by dagobert39 on 2010-03-07
I am using the following configuration:

VMWare Fusion 3 on an Intel iMac with the guest system being Ubuntu. Networking is set "Bridged". My problem is using the network browser in switching between the host (Mac) and the guest (Ubuntu). I can ping between the two, I can call up the host from the guest or vice versa by using the respective IP numbers. However, whenever I try to communicate via the network browser I get as far as the workgroup name. Doubleclicking the workgroup name, takes endlessly long before the system reacts and at the end it says "cannot be mounted". Assume it is the samba configuration. I am including the smb.conf file for info.

Regards

[global]
    ; General server settings
    workgroup = arnold
    netbios name = Ubuntu
    server string =
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = lmhosts wins bcast host

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

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
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = helmut
    force group = arnold

---

