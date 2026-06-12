---
title: "Sharing directory with Samba to Xbox - Help needed :("
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by Calyptratus on 2007-06-30
Hi all.

I'm at my wits' end here.

I need a server for my files, to share in my internal network.

So I installed Ubuntu for the first time yesterday, and even got Samba up and working after fidgeting with it for 6 hours straight. Whatever I did, I could not log in to the server from my pc running XP.
Finally it worked, after setting the correct name in the smbusers.
AND I could connect and stream movies from my Xbox (which is the reason I got this server up and running in the first place).

Then I did something to prevent the pc from restarting, and thought "I'll just reinstall, as I now know how to set it up properly"...

Smart move...

Got Ubuntu up again.
Set it to Static IP 10.0..0.30

Replaced the smb.conf with a conf-file I found online yesterday, and which is the file I tinkered with until it worked... 

Got Samba up again.
Added user to smbusers.
Created the password for the user.

My server show up in my workgroup on the pc, AND I can log into my shared directories and get access to the files. FROM my pc.

Not from my Xbox. No way.

If anyone can help, I'll be eternally grateful.

Here's my smb.conf:


```

[global]
    ; General server settings

    server string = UbuntuServer
    workgroup = aprod
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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

[Filmer]
    path = /mnt/lagring1/Filmer
    browseable = yes
    public = yes
    read only = no
    guest ok = yes
```


My xbox-shares are as follows:

```
<bookmark>
<name>Server - Filmer</name>
<path>smb://myusername:mypassword@10.0.0.30/Filmer</path>
</bookmark>
```

And ideas welcome...

---

