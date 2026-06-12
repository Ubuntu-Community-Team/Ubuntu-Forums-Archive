---
title: "XP sees Ubuntu, Ubuntu doesn't see XP"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Nubers on 2008-02-05
Hi All,

I've seen many similar posts to what I'm about to say, but digging through those threads offers me no hope, perhaps because i'm an absolute networking nubester (on both xp and ubuntu) anyways here goes...

I want to share my media folder on the xp sp2 box with ubuntu 7.10.  I edited the samba config file and with some hair pulling was able to get the xp box to open the ubuntu share folder.  However, I cannot for the life of me figure out how to get the ubuntu box to see the windows share.

I tried the obvious, turn off xp firewall, but no luck.  If I google "What's my IP?" I can ping the xp box and it seems as though the communicate, but when I go to Places>Network I get the often quoted error message  "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: mtl_ntwk"."

My smb.conf contents are as follows:

[global]
    ; General server settings
    netbios name = sasquatch
    
    workgroup = MTL_NTWK
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
    path = /home/sasquatch
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = sasquatch
    force group = sasquatch
available = yes
browsable = yes
public = yes
writable = no


Can anyone help me?

Thanks a trillion!

---

