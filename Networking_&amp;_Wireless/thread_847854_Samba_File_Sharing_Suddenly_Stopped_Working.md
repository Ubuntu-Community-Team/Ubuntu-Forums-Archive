---
title: "Samba File Sharing Suddenly Stopped Working"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by BlueNoteExpress on 2008-07-02
When I first started using Ubuntu, I followed [Stormbringer's "HOWTO: Setup Samba"]("http://ubuntuforums.org/showthread.php?t=202605") to get samba setup to allow me to access files from my other Windows PCs.

I'm still using Ubuntu 7.04 Feisty Fawn, and I've had this working fine for about a year now.  This has recently stopped working.  Feisty did update samba to version 3.0.24 a couple of days ago, but I'm not sure if this is what caused the problem.

Does anyone know why samba would suddenly stop allowing me to share files?  Any help getting this straightened out is much appreciated.

Here's what my smb.conf looks like:

```
[global]
    ; General server settings
    netbios name = FEISTY
    
    workgroup = MSHOME
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

[UbuntuShare]
    path = /home/nick/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = nick
    force group = nick
```

---

### Post by superprash2003 on 2008-07-03
ensure that samba is running.. type sudo /etc/init.d/samba start in the terminal .. and ensure that you are able to ping the samba pc from the network

---

### Post by BlueNoteExpress on 2008-07-03
> **superprash2003 said:**
> ensure that samba is running.. type sudo /etc/init.d/samba start in the terminal .. and ensure that you are able to ping the samba pc from the network

I know samba is running because I stopped and started it several times after I noticed that it had stopped working.

Also, I can see the shares from my Windows PCs.  I just can't open them any more.  It worked just fine for about a year, but has recently stopped, and I have no idea why.

---

### Post by superprash2003 on 2008-07-03
try reinstalling samba!!

---

### Post by mwasoft on 2008-07-16
This problem has happened to me last weekend, SAMBA has stopped using the username map. I can log on to samba shares using the unix user names but not the mapped ones.

The server is fully up-to-date Hardy 8.04 and I am sure I remember seeing a samba update being applied when a group of recommended updates were applied last weekend. Not other dhanges were made.

The following lines are also appearing the smb.log

[2008/07/16 11:46:09, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/07/16 11:46:09, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

repetitively.

It looks suspiciously like a recent samba update is broken.

Edit:

Just gone back and looked at the update log. The relevant change seems to have been an update to Winbind.

---

### Post by johpe on 2008-07-16
This seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)

I have the same problem that you have, if you do:
/etc/init.d/winbind stop

then the shares start working again.

---

### Post by peakshysteria on 2008-07-16
Doesn't work at my end.
```
smbclient -L (popcorn a100 media center ip) -U%
```gives me:
> Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

	Sharename       Type      Comment
	---------       ----      -------
	share           Disk      
	IPC$            IPC       IPC Service (SMP8634 Share)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

	Server                         Comment
	---------                      -------
	PCH-A100                       SMP8634 Share

	Workgroup                       Master
	---------                       -------
	WORKGROUP                       PCH-A100

But can't mount smb at all anymore.

---

### Post by jdavis on 2008-07-17
> **johpe said:**
> This seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)

I have the same problem that you have, if you do:
/etc/init.d/winbind stop

then the shares start working again.

Worked great for me, will keep my eyes on the bug tracker.

Tip: winbind can be switched off through [bum]("http://packages.ubuntu.com/hardy/admin/bum") for now!

---

### Post by zerubbabel on 2008-10-16
> **johpe said:**
> This seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)

I have the same problem that you have, if you do:
/etc/init.d/winbind stop

then the shares start working again.

This solved my problem also, when accessing samba shares suddenly stopped working after yesterday's system update. But why is this necessary? Apparently the update several months ago introduced this bug, but then it must have been fixed, because I've been accessing samba shares just fine until now, just after the latest system update... I don't really know what winbind does, but is it necessary for me to keep it from being started next time I reboot?

---

### Post by zerubbabel on 2008-10-16
Spoke too soon. After a reboot, still couldn't access samba shares, even after stopping winbind.

---

### Post by peakshysteria on 2008-10-17
Samba working again in my end after a clean install of Ubuntu Hardy 32-bit. Worked out of the box :popcorn:

---

### Post by Jeruvy on 2008-10-29
> **johpe said:**
> This seems like this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)

I have the same problem that you have, if you do:
/etc/init.d/winbind stop

then the shares start working again.


Does not work for me:

jeruvy@bustedmachine:~$ /etc/init.d/winbind stop
bash: /etc/init.d/winbind: No such file or directory

---

### Post by dmizer on 2008-10-29
Change this option:
wins support = yes
to
wins support = no

Also try removing the "force group = $$$" option.

---

