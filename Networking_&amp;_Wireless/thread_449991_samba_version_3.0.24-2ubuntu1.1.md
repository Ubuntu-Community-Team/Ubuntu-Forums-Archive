---
title: "samba version 3.0.24-2ubuntu1.1"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by ym4546 on 2007-05-20
I've been using Samba for two-way sharing between Windows XP and kubuntu since Dapper without problems. I simply followed this tutorial: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) and everything worked beautifully.

Lately, however, on May 16, 2007, Adept said that there was an update to samba available and I let it upgrade samba from version 3.0.24-2ubuntu1 to 3.0.24-2ubuntu1.1

After this update, samba broke in that the windows host could not access shares on my kubuntu machine. However, the kubuntu machine could still access the windows shares. Basically, I can see a list of the shares on the ubuntu machine, but when i try to access any share in particular, it says that the "network path could not be found". To solve this, i merely downgraded samba back to 3.0.24-2ubuntu1.

I'm wondering if this is some kind of bug that should be reported, and whether there's something wrong with my configuration. I am including my smb.conf below.

I'm running Kubuntu 7.04 with a CNET Pro 200WL network card.

BEGIN smb.conf:

[global]
    ; General server settings
    netbios name = yatin-desktop
    server string =
    workgroup = MSHOME
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
    path = /media/hda5/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = yatin
    force group = yatin

END smb.conf


THanks for any help you can provide.

---

### Post by ym4546 on 2007-05-22
This issue has been fixed in samba 3.0.24-2ubuntu1.2

Kudos to the ubuntu package team for getting that out fast.

---

### Post by kexodusc on 2007-05-23
> **ym4546 said:**
> This issue has been fixed in samba 3.0.24-2ubuntu1.2

Kudos to the ubuntu package team for getting that out fast.

Hey ym4546 - as you'll recall I had similar symptoms.  Any idea what the bug was specifically that caused this or how it was corrected?

---

