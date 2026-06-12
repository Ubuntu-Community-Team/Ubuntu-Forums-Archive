---
title: "Valid User not working properly - Samba"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by pellanda on 2018-01-16
Hi! I am trying to change a Samba Server from a Debian to my Ubuntu Server (Ubuntu 14.04.3 LTS) and it is already installed and configured.

My user is working correctly, I can access all folders that are created in smb.conf, but I cannot connect to it using another valid user, I don't know more what to do.

User: Bruno can access all folders, user comercial cannot access shared folder COMERCIAL and user cobranca cannot access folder COBRANCA

this is my smb.conf:

```

# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        interfaces = lo em1
        bind interfaces only = Yes
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No


[Cobranca]
        comment = Compartilhamento Seipa
        path = /var/servipa/COBRANCA
        valid users = cobranca bruno comercial
        read only = No


[Comercial]
        comment = Compartilhamento Seipa
        path = /var/servipa/COMERCIAL
        valid users = comercial bruno
        read only = No


[Servipa]
        comment = Compartilhamento Servipa
        path = /var/servipa
        valid users = bruno
        read only = No

```

this is my ls -lah in the folder:

```

root@central:/var/servipa# ls -lah
total 3,8M
drwxrwx---  9 root root 4,0K Jan 11 17:21 .
drwxr-xr-x 15 root root           4,0K Jan 10 10:48 ..
drwxr-xr-x 22 root root           4,0K Set 29 16:54 ADMINISTRACAO
-rwxrwxrwx  1 root root           129K Jul 27 17:32 agendaANA.csv
-rwxrwxrwx  1 root root           437K Set 14 14:01 ANALISE 1 SEMESTRE.xlsx
-rwxrwxrwx  1 root root            23K Out  8  2015 Analise Score Tidas.xlsx
drwxr-xr-x 31 root root           4,0K Jan  9 09:43 COBRANCA
drwxr-xr-x 19 root root           4,0K Jan 11 09:41 COMERCIAL
drwxr-xr-x 13 root root           4,0K Jan 11 11:38 FINANCEIRO
drwxr-xr-x  2 root root           4,0K Dez 14 12:42 GERENCIAL
drwxr-xr-x 30 root root           4,0K Jun  2  2017 MILTON
-rwxrwxrwx  1 root root           2,7M Mai 20  2015 Planilha Maringa.xlsx
-rwxrwxrwx  1 root root           537K Jan  9  2014 Projeto Meu Crediário.pptx
drwxr-xr-x  3 root root           4,0K Set  1  2016 SUPORTE

```

and I've checked that both users are included in smbpasswd -a and have the same password

cat /etc/passwd:

```

bruno:x:1000:1000:bruno,,,:/home/bruno:/bin/bash
cobranca:x:1002:1003:,,,:/home/cobranca:/bin/bash
comercial:x:1003:1004:,,,:/home/comercial:/bin/bash

```

the samba users:

```
root@central:/var/servipa# pdbedit -L -v | grep username
Unix username:        bruno
NT username:
Unix username:        comercial
NT username:
Unix username:        cobranca
NT username:

```


I really apreciate any help to make this work.

---

