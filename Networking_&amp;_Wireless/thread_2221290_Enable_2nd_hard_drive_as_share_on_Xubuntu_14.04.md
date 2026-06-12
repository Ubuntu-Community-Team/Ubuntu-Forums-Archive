---
title: "Enable 2nd hard drive as share on Xubuntu 14.04"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2014-05-01
Hi all

Following on to this thread, [http://ubuntuforums.org/showthread.php?t=2220994]("http://ubuntuforums.org/showthread.php?t=2220994"), another share has been added in /etc/samba/smb.conf as follows:-```
[global]
    ; General server settings
    netbios name = DIMENSION-2400
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    security = user
    map to guest = Bad User
    ; guest account = nobody
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = yes
    printing = CUPS
    printcap name = CUPS
    syslog = 1
    syslog only = yes
    usershare owner only = false
    ; Added during setup
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
    ;path = /media/cdromFile/
    ;browseable = yes
    ;read only = yes
[Documents]
    path = /home/chris/Documents/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
[Drive_D]
    path = /media/chris/Drive_D/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755

```
Having resolved required permissions, [Documents] behaves as expected.

[Drive_D] path for this share was taken from the Disks utility, drive is mounted, and ownership is 'chris', permissions as per [Documents].

While the share shows on the network, access is denied.

Ideas please?

TIA

---

### Post by ChrisRChamberlain on 2014-05-02
By way of background, the Ubuntu 12.04 LTS server also has a second hard drive, 'Drive_D', accessible as expected.

The server path is ```
 path = /media/Drive_D/
```as opposed the the Xubuntu pc's path of ```
 path = /media/chris/Drive_D/
```HTH

---

### Post by ChrisRChamberlain on 2014-05-03
Resolved the access issue by unmounting the second drive, then Settings > Disks and select the second drive.

Select 'More actions > Edit Mount Options...'

Turn 'Automatic Mount Options' off.

Stop SAMBA

Copy and paste 'Mount Point' value into relevant section in /etc/samba/smb.conf as the 'path' to the device.

Restart SAMBA and drive is accessible.

Yet to resolve how to auto mount the drive but main objective achieved.

Hope this might help someone else.

---

### Post by ChrisRChamberlain on 2014-05-03
The drive is now auto mounted by checking 'Mount at startup' in 'Mount Options' dialog, found at Settings > Disks and select the second drive.

Select 'More actions > Edit Mount Options...'

---

