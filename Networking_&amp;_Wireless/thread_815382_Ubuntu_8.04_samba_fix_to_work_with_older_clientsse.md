---
title: "Ubuntu 8.04 samba fix to work with older clients/servers"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by bentledr on 2008-06-01
Since upgrading to ubuntu 8.04 I have had problems accessing my LANDISK network storage box and the shared files on an old win98se laptop and also had problems accessing my shared HOME folder on my ubuntu 8.04 box.

So after quite a bit of searching on GOOGLE I have found a fix for my problem and it is as follows :-

Add the following to smb.conf just above the password encryption comments.

# Older servers may not support the higher level of default security for
# password negotiation and may require uncommenting the following line.
;   client lanman auth = yes

# Older clients may not support the higher level of default security for
# password negotiation and may require uncommenting the following line.
;   lanman auth = yes

NOTE If you uncomment lanman auth = yes you will need to re-create your
samba passwords if they have already been created.

Open a terminal and at the prompt type the following :-

sudo smbpasswd -a <sharename> 

Substituting <sharename> with the desired sharename.

I hope some people find this useful.

---

### Post by sanitycheck on 2009-02-15
Thanks for posting this fix Bentledr.  Unfortunately I found this post after I found the solution somewhere else.  I'll post a few more details to help others find this post.

This fix is also necessary for support of DOS (MSDOS) network boot disks, such as the [[COLOR="RoyalBlue"]Universal TCP/IP Network Boot Disk[/COLOR]]("http://www.netbootdisk.com").  These are used still today for some disk cloning or backup utilities such as Symantec Norton Ghost.

This fix is also necessary for Windows 3.1, or Windows for Workgroups 3.11.  This was actually how I first noticed the problem.  For fun I recently created a WFW 3.11 VM and was surprised it couldn't connect to the main Samba server.  Only later did I notice the DOS boot disks didn't work either.  I did my testing with a Windows 98 VM I had already.

Bentledr mentions the upgrade to 8.04.  I also upgraded from 8.04, from 7.10,  and that's what broke my DOS and Win9x support.  I upgraded to 8.04 this last month.

If you already have an account on the Samba server and you are logged in as that user, you only need to issue the *smbpasswd* command (without anything after it).  You will be prompted to enter your old and new passwords, with a second confirmation for the old.  You may enter the same password you had before.  This *smbpasswd* changing step, even if using the same password, is critical to re-enabling old MS client support after you make the changes to your smb.conf and re-start the samba services (*sudo /etc/init.d/samba restart*).

Do NOT enable support for older clients unless absolutely necessary.  There are good security reasons the Samba team disabled this support by default.

---

### Post by RealG187 on 2009-05-04
I think I got it!!

```
[global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    client lanman auth = yes
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

[incoming]
    path = /home/mpg/Desktop/Incoming
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = mpg
```

Upon changing it from "User" to "Share" I was able to view "\\MIKED6" (before it would ask for the password. I seen the name of the share "Incoming" but it asked when I double clicked. I then changed guest ok = no" to yes!!!

---

