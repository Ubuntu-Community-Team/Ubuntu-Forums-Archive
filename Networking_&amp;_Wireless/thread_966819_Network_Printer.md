---
title: "Network Printer"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by jlabomb on 2008-11-01
I have a lexmark x1240 printer that I have connected to a XP machine. I have it there since it is a all in one so I can use the scanner. I have the machines networked together share files just fine. Now I am trying to share the printer. When I go through the steps I found to add a network printer nothing happens when I finish adding it. No new printer is added to the machine and no errors. I have also tried added a local printer and try changing it to a network printer but the settings I put in never stay. When I choose windows printer SMB it asks for the password for my workgroup then I select the machine it asks for the password for that computer. Then I am able to select the printer name in the drop down so I know it sees the printer i just can't get the settings to take effect. Any help is appreciated thanks. 

Here is my smb.conf in case that will help

> [global]
    ; General server settings
    netbios name = James-Desktop
    server string =
    workgroup = WORKGROUP
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
    path = /home/james/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = home
    force group = network

---

### Post by rhcm123 on 2008-11-01
> **jlabomb said:**
> 
[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

Is this right? This is the printers section from your smb.conf file, check the path to printer :).

EDIT: also, it states that your workgroup is WORKGROUP. Is this right? Check it. Set all workgroups to the same thing (all mine are USSR) or else you will not be able to connect.
Also, delete the server string line, or put a value there.
you can test for typos like that with the testparm command. (simply type testparm at a shell prompt)

---

### Post by jlabomb on 2008-11-01
Thanks for the quick reply. I took out that server string line like you suggested. It did not help the problem any. I am not sure how to check and see in the print path is the right place or not. I couldn't find any info about it. Thanks again.

---

### Post by jlabomb on 2008-11-09
Bump

---

