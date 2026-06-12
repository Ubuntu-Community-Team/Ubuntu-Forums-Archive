---
title: "Ubuntu 8 and Windows XP"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by danielgbr on 2008-09-04
well, i have quiet the unique problem (or not).
My windows XP can see my linux laptop on the network (only when i restart Samba in terminal : i get an error Failed to kill 4969: No such process..but isnt the case now) but my linux can only see the workgroup but not the windows pc in it... 

I have tried configureing, reconfiguring Samba and i have no idea whats the problem...

This is my smb.conf:

[global]
    ; General server settings
    netbios name = m3s-04
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0, wlan1
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = false
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
     browseable = yes
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/
     writable = yes

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
    force user = m3s-04
    force group = M3SSERVER

This is what i get when i type testparm:

[global]
	server string = 
	interfaces = lo, eth0, wlan1
	bind interfaces only = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	read only = No

[print$]
	path = /var/lib/samba/printers
	write list = root
	read only = Yes
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No

[MyFiles]
	path = /home/samba/
	force user = m3s-04
	force group = M3SSERVER
	create mask = 0644

Well, thats about it.. i am a total newb on Ubuntu. Please help? Ive been fighting with this for about a week

---

