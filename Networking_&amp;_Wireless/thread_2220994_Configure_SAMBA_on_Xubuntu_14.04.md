---
title: "Configure SAMBA on Xubuntu 14.04"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2014-04-30
Hi all

Have a network with a mix of Windows boxes, and a Ubuntu 12.04 LTS server.

Also installed Xubuntu 14.04 on a Dell Dimension 2400, installed SAMBA and Nautilus, (now the default file manager), and modified the /etc/samba/smb.conf as follows:-```
[global]
    ; General server settings
    netbios name = DIMENSION-2400-XUBUNTU
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    security = user
    map to guest = Bad User
    ; guest account = nobody
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = yes
    printing = CUPS
    printcap name = CUPS
    syslog = 1
    syslog only = yes
    usershare owner only = false
    ; Added during setup
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
    ;path = /media/cdromFile: /etc/samba/smb.conf Page 2 of 3
    ;browseable = yes
    ;read only = yes
[Documents]
    path = /home/chris/Documents/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755

```...the code derived from the Ubuntu server.

SAMBA appears to be running correctly but the Xubuntu box does not show in the network.

So, the assumption that SAMBA would work in the same way as on the Ubuntu server seems naive.

Any ideas, please?

TIA

---

### Post by bab1 on 2014-04-30
> **ChrisRChamberlain said:**
> Hi all

Have a network with a mix of Windows boxes, and a Ubuntu 12.04 LTS server.

Also installed Xubuntu 14.04 on a Dell Dimension 2400, installed SAMBA and Nautilus, (now the default file manager), and modified the /etc/samba/smb.conf as follows:-```
[global]
    ; General server settings
    netbios name = DIMENSION-2400-XUBUNTU
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    security = user
    map to guest = Bad User
    ; guest account = nobody
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = yes
    printing = CUPS
    printcap name = CUPS
    syslog = 1
    syslog only = yes
    usershare owner only = false
    ; Added during setup
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
    ;path = /media/cdromFile: /etc/samba/smb.conf Page 2 of 3
    ;browseable = yes
    ;read only = yes
[Documents]
    path = /home/chris/Documents/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755

```...the code derived from the Ubuntu server.

SAMBA appears to be running correctly but the Xubuntu box does not show in the network.

So, the assumption that SAMBA would work in the same way as on the Ubuntu server seems naive.

Any ideas, please?

TIA

The NETBIOS name needs to be 15 characters or less.

You should uncomment:* guest account = nobody* if you ever want to make public (guest) shares available.  Look at your share definition closely again.

Samba runs exactly the same on Ubuntu server edition as it does on the desktop edition.  There is no difference between the server and destop editions other than the desktop itself (I.E. the Linux kernel is the same).

---

### Post by piotrasbl on 2014-04-30
when you set proper samba conf file, make sure you run in terminal: sudo service samba stop, than start
this will allow changes to be done. Remember that you need to create samba accounts as well:

sudo smbpasswd -a username

---

### Post by ChrisRChamberlain on 2014-05-01
bab1, piotrasbl 

Thank you both for your replies.

Renaming the computer to 'Dimension-2400' resolved the issue - was unaware the name length might be an issue.

Both your other comments have been noted.

Many thanks again.

---

