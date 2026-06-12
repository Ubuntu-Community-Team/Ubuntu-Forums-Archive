---
title: "Can't access windows network with Samba"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by The Judderman on 2007-11-24
Dear All,

I have previously had a samba network working beautifully... Unfortunately, I had to reinstall windoze on my PC, and since then I've lost my samba connection. 

I have re-installed and reconfigured samba on my linux box, and since then, I can access my linux data from my PC, but not the other way round!!!!! Here is my /etc/samba/smb.conf file:

[global]
    ; General server settings
    netbios name = LAPTOP
    
    workgroup = JUDNET
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

[MyFiles]
    path = /media/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = peter
    force group = peter
available = no
browsable = yes
public = no
writable = no

[documents]
path = /home/peter/documents
available = yes
browsable = yes
public = yes
writable = yes

Any ideas?

Cheers,

The Judderman

---

### Post by jetsam on 2007-11-24
Changing "wins support" from No to Yes might help.
  
Did you remember to set your workgroup name in XP to JUDNET when you re-installed?

Also check the workgroup name in Ubuntu under System-->Administration-->Shared Folders-->Genral Properties.  I'm not sure if it parses its value from the smb.conf or not.

---

