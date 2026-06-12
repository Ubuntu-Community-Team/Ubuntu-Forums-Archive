---
title: "Configuring Samba"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by RockxLee on 2007-04-02
I used Stormbringer's guide to set up a network with Samba
[http://www.ubuntuforums.org/showthread.php?t=202605&page=1](http://www.ubuntuforums.org/showthread.php?t=202605&page=1)

I got to the point Where I should map a network drive in windows pointing to a shared folder on my linux box. I managed to add the folder through "add a network place" and it is called MyFiles. When I try to access it though it says I may not have the permissions to access it.

Myfiles path is /home/samba and I have chmodded it already.
Does anyone know why I cannot access the folder?

---

### Post by Swab on 2007-04-02
Post your Samba conf file..

---

### Post by RockxLee on 2007-04-02
[global]
    ; General server settings
    netbios name = tran-desktop

    workgroup = MSHOME
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
    path = /home/samba/

    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tran-desktop
    force group = MSHOME
available = no
browsable = yes
public = no
writable = no

[My Documents]
path = /home/tran/Desktop/My Documents
available = yes
browsable = yes
public = yes
writable = no

---

### Post by DennShin on 2007-04-03
> **RockxLee said:**
> 

[MyFiles]
    path = /home/samba/

    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tran-desktop
    force group = MSHOME
available = no
browsable = yes
public = no
writable = no


I followed the same howto over the weekend and the only difference I see is your force group is not the same as force user.  I belive in the guide they are listed as the same.  I also noticed that mapping the drive was optional.  Rebooting and viewing workgroups from the windows machines brought up the shared directorys.

```

[MyFiles]
    path = /home/samba/

    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tran-desktop
    force group = tran-desktop
available = no
browsable = yes
public = no
writable = no

```

---

### Post by RockxLee on 2007-04-03
Hey thanks for replying.
I did the changes you said to do. Changed force group to tran-desktop still no good.

---

### Post by dolphin_oracle on 2007-04-03
are you sure that you have set up BOTH samba accouts and ubuntu accounts for the login name you intend to use.  If you have a samba account but not a ubuntu user account, you will not be able to access the share.

As a check you can set your "public = no" to "public = yes".  That would eliminate the ubuntu user accounts from the issue, i think.

---

