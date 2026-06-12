---
title: "Samba only works in 1 direction"
date: 2016-08-10
forum: Networking &amp; Wireless
---

### Post by dms-audio on 2016-08-10
I have a clean install of 16.04 on a laptop with wireless and a 14.04.4 upgrade to 16.04 on a desktop wired.

The i5 laptop can see the i7 desktop and connect fine to shares but the desktop does not see the laptop at all.
i7 is desktop, i5 is laptop. I only need basic browsable file share between 2 pc's.






smbtree
    \\ASUS-I7                asus-i7
        \\ASUS-I7\IPC$               IPC Service (asus-i7)
        \\ASUS-I7\david              
    \\ASUS-I5                asus-i5


The smb.conf is pretty much the same for both pc's apart from the server string. I have set the hostname and hosts to match the same name for the

[global]

        workgroup = workgroup
        server string = asus-i7

        name resolve order = bcast host lmhosts wins
;       wins support = yes

;       interfaces = 127.0.0.0/8 eth0
;       bind interfaces only = yes
        max log size = 500
        syslog = 0

;       panic action = /usr/share/samba/panic-action %d
;       server role = standalone server
;       obey pam restrictions = yes
;       unix password sync = yes

        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        pam password change = yes
        map to guest = bad user

        usershare allow guests = yes
        security = user
        encrypt passwords = yes
        guest ok = yes
        guest account = david
        username map = /etc/samba/smbusers

        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes


[david]
        path = /home/david

---

### Post by dms-audio on 2016-08-11
OK... I give up with samba. Rarely have I got it to work 100% over the years no matter how much I read and tweak. 

Installed SSH server on both PC's and use gigolo to mount the shares which just works first time and so easy compared to samba config. I guess linux to linux NFS would be better also.

---

