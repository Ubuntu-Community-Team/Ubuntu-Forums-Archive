---
title: "Samba only allows &quot;Guest&quot;?"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by Rocketeer on 2006-09-26
Ok, so far, so good. Finally I managed to configure Samba the way it should be....some open folders, some shared. Core idea is, that each "USER" has his own home/xyz folder shared (pass protected).

Now. Everything works, except that if I access a password protected folder, it requests a password, no user name - only a password. The password has to be correct, but in Windows, the user is uneditable and shows "Guest"...which confuses me. Why is that? Is there a way to force the people to enter their username?

Also if I connected to each folder (after entereing password) - the session seems to "store" the permission and I don't have to enter password again for a different user....

Strange.


Following the smb.conf file (dump)

> [global]
        workgroup = ROCKETNET
        server string = Die Rakete unter den Servern.
        security = SHARE
        null passwords = Yes
        passdb backend = tdbsam
        unix password sync = Yes
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[homes]
        valid users = %S
        read only = No
        create mask = 0600
        veto files = /*.{*}/.*/mail/bin/
        browseable = No

[oeffentlich]
        comment = Oeffentlicher Ordner
        path = /media/samba/public/
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[rocketdisk]
        comment = Backup Festplatte
        path = /media/rocketdisk/backup/
        valid users = rocketeer
        read only = No
        create mask = 0600


---

### Post by enopepsoo on 2006-09-26
Is it the windows machine that is asking for the guest account?

---

### Post by Rocketeer on 2006-09-27
Yes, sorry. Windows Machine is showing the "Guest" thing. I don't have a Linux machine to try (cause the only Linux thing is the server).

---

### Post by Rocketeer on 2006-09-28
(bump) -> sorry.

---

