---
title: "Samba Authentacation"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by md5hash on 2008-04-24
Hi, how can i share folders with/without authentication to windows/unix network?

thanks

---

### Post by md5hash on 2008-04-25
got it...

---

### Post by dmizer on 2008-04-25
i used the following howto as a model for all of my samba servers: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

for a samba server without authentication, i use the following smb.conf configuration in place of the one given in the howto (everything else remains the same, except adding windows accounts):
```
[global]
    ; General server settings
    netbios name = UBUNTU_HOSTNAME
    server string =
    workgroup = WINDOWS_WORKGROUP
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = UBUNTU_USERNAME
    force group = UBUNTU_USERNAME
```

edit:
hah!  i took too long to compose my post ;)

---

