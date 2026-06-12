---
title: "Windows XP - Samba authentication: NO, Windows 7 &amp; 8: YES"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by Sanif_Sentosa on 2014-05-13
Hi guys, I'm using Ubuntu 14.04 and set it as samba file server to serve my windows users. Problem I found is, Windows 7 and 8 could connect and share files without problem, but not for some Windows XP users. When I try to access \\sambaserver\sharefolder from Windows XP, it would keep asking me for username and password.
P.S: smbpasswd has been done properly for the appropriate users.

here's my smb.conf global section:
[FONT=courier new][global]
        workgroup = WORKGROUP
        netbios name = sambaserver
        log file = /var/log/samba/log.%m
        wins support = yes
        server string = File Server for all
        max log size = 1000
        syslog = 0
        usershare owner only = false
        panic action = /usr/share/samba/panic-action %d
        server role = standalone server
        dns proxy = no
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        map to guest = bad user
        passdb backend = tdbsam
        obey pam restrictions = yes
        passwd program = /usr/bin/passwd %u
        pam password change = yes
        ntlm auth = no
        lanman auth = no
        client ntlmv2 auth = yes
        security = user[/FONT]

anything wrong with my configuration? or any other possible problems and solutions?
thanks a million for your kind help.

---

### Post by dannyboy79 on 2014-05-13
the users on the windows xp machine are the same username as the win7 and win8 boxes which are also on the samba server? if not you can always use the username map option and file.

---

### Post by Sanif_Sentosa on 2014-05-26
yes, all is the same, the strange thing is using the same username and password, using win 7 and 8 are ok, but when using it for login from windows xp, the prompt dialog box is keep on appearing and just won't log me in. My guess is the authentication perform with winxp and win7 or 8 is different.

---

