---
title: "Ubuntu 16.04 Samba Mounted to Windows Server Can't read Symbolic Links"
date: 2018-04-05
forum: Networking &amp; Wireless
---

### Post by achmann on 2018-04-05
I can't navigate symbolic links. The symbolic links were created in Windows Server 2008 R2. I can't access them. 
  The error I get is 

  [FONT=courier new]-bash: cd: 2011: No such file or directory
[/FONT]
  It does work in windows, no worries.
  It recognizes them as UNC links before I try and access them for  example here below. After I attempt to access them that will disappear  (see 2007)

  [[IMG]https://i.stack.imgur.com/K272L.png[/IMG]]("https://i.stack.imgur.com/K272L.png")
  Also here is the my smb.conf file 
  [FONT=courier new][global]
        obey pam restrictions = yes
        syslog = 0
        server role = standalone server
        max log size = 1000
        workgroup = WORKGROUP
        passwd program = /usr/bin/passwd %u
        pam password change = yes
        usershare allow guests = yes
        server string = %h server (Samba, Ubuntu)
        passdb backend = tdbsam
        os level = 20
        unix password sync = yes
        panic action = /usr/share/samba/panic-action %d
        map to guest = bad user
#       security = share
        log file = /var/log/samba/log.%m
        netbios name = Cloud
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        winbind use default domain = yes
        winbind trusted domains only = no
        dns proxy = no
        #My Extra Inputs
        allow insecure wide links = yes
        unix extensions = no

        #unix extensions = no

[share]
        path = /mnt/share
        follow symlinks = yes
        wide links = yes[/FONT]

  So I am not trying to create Symbolic links in Ubuntu and read them in Windows, I am trying to read Windows Server 2008 r2 symbolic links in ubunutu via Samba or Cifs. Is there something I am missing or is my googlfu  just off today and I have searched the wrong things.

---

