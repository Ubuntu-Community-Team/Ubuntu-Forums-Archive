---
title: "Can access samba folder, but not its subfolders"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by loldrup on 2007-12-30
I first followed this guide: [http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

and when it gave me the error described in the subject, I then tried this guide:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

But got exactly the same error. Both times I only enabled the guest account.

I access the share from my WinXP, it asks for username and passford, i supply "guest" and "my_password" and I get access to see the subfolders of /home/shares

Then I try to access the subfolder "my_Files" but Windows XP then gives me the message that this folder is not accessible.

The machine is a ubuntu 7.10 and this is my samba config file as it is now (I di restart the samba server after doing configuration changes):

The user 'guest' has the homedir /home/guest   while the samba share is /home/shares
could this be a problem?

this is my smb.conf file:

[global]
    ; General server settings
    netbios name = jon1		;
    server string =
    workgroup = EGMONT		;
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no		;

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

    interfaces = lo, eth0
    bind interfaces only = true

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
    path = /home/shares/	;!
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = guest
    force group = guest

---

