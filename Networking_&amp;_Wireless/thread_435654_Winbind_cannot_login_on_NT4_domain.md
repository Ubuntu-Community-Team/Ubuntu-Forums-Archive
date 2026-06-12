---
title: "Winbind: cannot login on NT4 domain"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Kryben on 2007-05-07
Hi,

I want to log in onto a NT4 domain using Winbind, Samba and NSS.
Commands like wbinfo -u and wbinfo -a DOMAIN\\testuser%testpw are working fine, but when I'm on the login screen of GNOME, and when I try to login using following criterium:
[B]user: DOMAIN\\testuser
passwd: testpw[/B]
it just doesn't work.

Here is my set up:

**/etc/nsswitch.conf**
```
passwd:         files winbind
group:          files winbind
shadow:         files winbind

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


**/etc/samba/smb.conf**
```
[global]
   workgroup = DOMAIN
   server string = %h (Ubuntu, Samba)
   wins support = yes
   wins server = 10.20.150.12
   dns proxy = no
   name resolve order = lmhosts host wins bcast

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = domain
   encrypt passwords = true
   password server = PDC001
   passdb backend = tdbsam
   obey pam restrictions = yes

   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   winbind enum users = yes
   winbind enum groups = yes
   template homedir = /home/%U
   template shell = /bin/bash
```


**cat /etc/pam.d/samba**
```
@include common-auth
@include common-account
@include common-session
```


**/etc/pam.d/login**
```
auth       requisite  pam_securetty.so
auth    sufficient      /lib/security/pam_winbind.so
auth    sufficient      /lib/security/pam_unix.so use_first_pass
auth       requisite  pam_nologin.so
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth       optional   pam_group.so
session    required   pam_limits.so
session    optional   pam_lastlog.so
session    optional   pam_motd.so
session    optional   pam_mail.so standard

@include common-account
@include common-session
@include common-password

```


And finally, I also fixed the init.d script 'samba' so, that it also starts and stops winbind.

Now, as said before, commands like wbinfo -u outputs the domain users and wbinfo -a says that the plaintext verification went successfully. Thus, that works fine. But I can't login in.

Thanks in advance!

---

