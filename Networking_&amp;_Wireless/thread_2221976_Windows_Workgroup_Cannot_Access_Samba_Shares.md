---
title: "Windows Workgroup Cannot Access Samba Shares"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by Geoff_Robinson on 2014-05-04
Help me before I reinstall my old XP image.
I have an old pentium4 box that I have been using as a file server in a windows workgroup. When I used XP I had no issues accessing the three drives that are in this box and life was good. I installed Ubuntu 12.04 as a measure to get my 13 yr old son to start coding on his own, and to get familiar with command-line computing (unlike his dad) as a doorway to software engineering profieciency. 

I installed samba (samba4) and modified the smb.conf file as attached. At one point I could access one of the mounted drives along with its files (I suppose due to some long forgotten fiddling I did with the .conf file). The ubuntu ext4 image is on a 60g partition with a 10 gig swap where both reside on a 120 gig SSD in this old pentium box.

Here are my needs:
- Load samba and serve up the three mounted drives automatically every time this box is booted
- have all windows 7 boxes in my workgroup access the ubuntu mounted drives and their contents

i.e. I want this box to provide its previous utility while it existed as XP.

Thanks in advance for any help, counseling, or moral support.

Geoff

Here is the .conf (I could not figure out how to paste a scrolling table into this message)
```

[global]
    ; General server settings
    netbios name = ZOMBIE
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
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

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
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = adrian
    force group = adrian
    usershare owner only = false
```

---

### Post by squakie on 2014-05-04
I try it with guest ok = yes on your [MyFiles] share just to see if it's a permissions problem.  You may need to set up Samba users and passwords with guest ok = no - did you already do all of that as well?  What are the permissions on the file system at /media/samba ?  Also, I think Windows 7  uses something other than workgroup by default, and I think the default workgroup in Windows 7 isn't "workgroup" now.  You may need to change some of that.

I would try searching the forums - with the "Search" function - for:  samba windows 7  and see what you might get back.  I'd also try the following on a net search:

ubuntu samba shares not accessable in Windows 7

---

### Post by deadflowr on 2014-05-04
Thread Moved to Networking and wireless

Please use code tags when posting code
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by Geoff_Robinson on 2014-05-04
Thanks folks. The Linux Gods did not smite, and have smiled upon me. A command-line complete scouring and reinstall of samba server and client did the trick. and [this link]("http://bit.ly/Q43xvP") was of great help in additional tweaks to the smb.conf file.

Geoff

---

