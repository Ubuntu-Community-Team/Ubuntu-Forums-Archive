---
title: "Mumble mumble....... SAMBA"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by The_Apprentice on 2007-12-02
I am really sorry, but here is another Samba "driving me up the 'kin wall" issue.

For starters, here is my config:

```

[global]
    ; General server settings
    netbios name = Ubuntu
    
    workgroup = WORKGROUP
    domain=workgroup
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    interfaces = 127.0.0.1, 192.168.0.9/16
    bind interfaces only = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
server string = Ubuntu
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/
    writeable = yes

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
;    path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775

[printers]
 ;   path = /tmp
 ;   printable = yes
 ;   guest ok = yes
 ;   browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[htdocs]
path = /opt/lampp/htdocs
available = yes
browseable = yes
public = yes
writable = yes

[Share]
path = /Share
force group = users
read only = No
writable = yes
directory mask = 0775
directory security mask = 00
force directory security mode = 0777
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

```

I can see the shares on the ubuntu box, via Places-Network Servers-Windows Network-Ubuntu

The problem is:
1.  Ubuntu is not visible on the windows network
2.  When I map a drive to it I keep getting prompted for a username/password.

I have added and enabled a user called Sean and one called transfer.
The share called "Share" is 777

I can map a drive from the ubuntu server to an XP box.
I can not view files on a Vista box, even though everyone has full control to the share, but that something I am not particularly worried about.

It used to work really easy, but I had a hard drive die on me and I had to re-install the server.  I have never been able to get it to work since.

So, where am I going wrong?

---

### Post by The_Apprentice on 2007-12-03
<tumbleweed enter stage left/>

:-\"

---

