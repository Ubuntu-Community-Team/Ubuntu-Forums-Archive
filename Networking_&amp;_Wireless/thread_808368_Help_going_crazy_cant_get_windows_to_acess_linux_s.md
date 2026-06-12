---
title: "Help going crazy cant get windows to acess linux shares with samba!!!!!!!!!!"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by chrismitt2002 on 2008-05-26
here is my  samba.conf 

[B][global]
    ; General server settings
    netbios name = amd2200
    server string =
    workgroup = mshome
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



[share]
	path = /home/owner/share
	browseable = yes
	ready only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = owner
	force group = mshome



the only way i can acess linux shares from windows is to share them like u would in windows aka right click click share
going through the conf file it gives me this error
\\192.168.1.10\home not accessible you might not have permission to use this network resorce contact the administrator of this server to find out if uyou have access permission the group ne could not be found
it also does it with my ntfs shared hd as well

---

### Post by mapes12 on 2008-05-26
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

---

