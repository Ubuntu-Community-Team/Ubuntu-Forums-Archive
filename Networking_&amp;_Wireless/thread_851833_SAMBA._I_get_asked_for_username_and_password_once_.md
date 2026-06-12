---
title: "SAMBA. I get asked for username and password once again when I want to browse a share"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by BMOE on 2008-07-07
Hello everyone.

I'm using Ubuntu 8.04 Server Edition.
I'm using static IP to all my computers and they use WORKGROUP as worgroup name. 

I'm about to set up a fileserver at home using SAMBA and SWAT as GUI interface.

I have put in a new HDD as I have partitioned and mounted as /mnt/files and then CHMOD'ed /mnt/files to 777.

I have added a user called bmoe to linux, and samba with the exact sama password.

Now to my problem.
From my laptop with Windows XP at home I can see the server when I browse my Windows Network, and when I "double click" on it I can login using bmoe as login name and the password. Now I can see my shared folder, but when I "double click" it I get promted for a usernam and password once again but now i can't login.

Please help me.

This is what my smb.conf file looks like.

```
# Samba config file created using SWAT
# from 192.168.0.4 (192.168.0.4)
# Date: 2008/06/29 15:39:20

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supd$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        ldap ssl = no
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[Share /mnt/files]
        comment = Share /mnt/files
        path = /mnt/files
        valid users = bmoe
        read only = No
        guest ok = Yes

```

Regards
/Matias

---

### Post by Tarmael on 2008-07-07
This may sound trivial, but samba has a setting to allow for you to have no password.

smbpasswd -n *USERNAME*

Or something to that degree.

take a look at the smbpasswd -h if that doesn't quite work.

In fact, take a look at the smbpasswd anyway.

Hope this helps.

Bas.

---

