---
title: "Samba as domain &amp; local master browser?"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by bsh on 2007-10-31
Hi.
I am no expert in networking, so I'd like to ask for some advice.
I have 2 PCs on a router. One with WinXP (my main desktop), the other is a Ubuntu "server". It does not really meant to be a server, ie. i', not using it as a file server, mail server or anything. It just runs 24/7 and seeds torrents (mianly). After i got this working nicely, i thought i might install some server stuff on it, mainly for remote management, so it runs ssh, vsftp, vnc, ntpd, ddclient, etc. I can access the box from anywhere.
For convenience, I've installed Samba on it, so i can access the files on it easily from my windows pc. It works fine, i'm using it in a workgroup environment, not in domains.
However, i recently noticed some warnings and errors in the daenon.log files.
These were: samba did not find the local master browser when the xp pc was shut down, and it didn't automatically become the Local Master Browser (LMB). So I set it up to be always the LMB. After doing this, the logs have changed, and now it tells it's now the LMB, but could not find the Domain Master Browser.
I have no idea why does it need a DMB if i don't have domains?
But i just set samba to be the DMB too.
Now there are no more warnings in the log, seems to be working fine. (I wonder what happens when i get home and turn the windows pc on...? will it conflict?)

My question is: is it okay to have the Samba server as a DMB and LMB at the same time?

And another question:
> Samba server DURON is now a domain master browser for workgroup BSHNET on subnet 192.168.2.XXX
Samba name server DURON is now a local master browser for workgroup BSHNET on subnet 192.168.2.XXX

What does it mean, it is now the DMB and LMB on this subnet? Does it mean it is the LMB/DMB on the whole subnet of the router?

Thanks for any advice.

---

### Post by scrooge_74 on 2007-10-31
It should be ok, but you can post the smb.conf for others to check it.

Remember there is always a contest to see which PC becomes the Master Browser in the group.  At least you are not having problems with the netbios as is often the case.

I am no expert, but I had a similar setup for a linux box in my office network, but not anymore (no more XP weeehhh!)

---

### Post by bsh on 2007-10-31
smb.conf:
> [global]
    ; General server settings
    netbios name = DURON
    
    workgroup = BSHNET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = wins lmhosts hosts bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; BSH added:

    domain master = yes
    local master = yes
    os level = 255
    preferred master = yes

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

[SAMBA]
path = /media/hda4
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by scrooge_74 on 2007-10-31
Looks OK, but then again I hardly ever use SAMBA any more. just in case you get into troubles this links can be usefull to have at hand

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)
[http://ubuntuforums.org/showthread.php?&t=202605](http://ubuntuforums.org/showthread.php?&t=202605)
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://ubuntuforums.org/showthread.php?t=244620](http://ubuntuforums.org/showthread.php?t=244620)

---

