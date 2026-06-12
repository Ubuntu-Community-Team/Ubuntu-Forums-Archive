---
title: "samba/AD integration -Local users not found"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by gdsylvester on 2007-12-13
UBUNTU 7.10 
Samba  3.0.26a

Kerboros is working. I have joined our AD domain and while smb.conf is set to: security = user,
I can authenticate local user "test". (see below) 
#getent passwd works. (see below)

With smb.conf:
[global]
        security = user
        realm = OUR.DOMAIN.ORG
        workgroup = OUR_WG
        server string = %h
        unix charset = LOCALE
        smb ports = 139
        name resolve order = wins lmhosts hosts bcast
        dns proxy = yes
        preferred master = no
        wins server = "OUR_WINS_SERVERS
        invalid users = root bin daemon adm sync shutdown halt mail news uucp operator gopher
        log file = /var/log/samba/%m
        syslog = 0
        max log size = 500
        log level = 3
        strict locking = no
        write raw = no
        netbios name = "OUR_SERVER_HOSTNAME"
        password server = "OUR_PASSWORD_SERVER"
        idmap uid = 10000-90000
        idmap gid = 10000-90000
        winbind enum users = yes
        winbind enum groups = yes
        wins support = no
        winbind separator = +
        template shell = /bin/bash
        client use spnego = yes
        encrypt passwords = true
        include = /etc/samba/dhcp.conf
        domain master = No
        passdb backend = smbpasswd
        usershare max shares = 100
        winbind refresh tickets = yes
[test]
        comment = test
        valid users = @testgrp, test
        path = /home/test
        public = no
        writable = no

# /etc/nsswitch.conf
passwd:         files compat winbind
group:          files compat winbind
shadow:         compat
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis


# getent passwd|grep testfcc
test:x:36032:36032::/home/test:/bin/sh

From log:
[2007/12/12 14:13:26, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [test] -> [test] -> [test] succeeded

------------------------------------------------------------------------------------------------
When I change smb.conf to:
        security = ADS with all else the same, I can still #getent passwd for local and domain users, but I can only authenticate domain users.

root@MMP10:/etc/samba# getent passwd|grep test
test:x:36032:36032::/home/test:/bin/sh

root@MMP10:/etc/samba# getent passwd|grep gds
"OUR_DOMAIN"+gds:*:35596:10000:GDS:/home/"OUR_DONAIN/gds:/bin/bash

From log:
[2007/12/12 14:34:58, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [test] -> [test] FAILED with error NT_STATUS_NO_SUCH_USER
 ....
[2007/12/12 14:36:24, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [GDS] -> [GDS] -> ["OUR_DOMAIN+gds] succeeded

??????????????????????????

---

### Post by jonallport on 2007-12-14
That's correct; you are stating that you want to use ADS for security (authentication) and it is.

Is the issue that you want to authenticate EITHER as an ADS user or from the local list?

I'm not sure samba will handle that!

---

### Post by gdsylvester on 2007-12-14
I have had a slackware 10 box doing this for 2 years. Auths both domain and local users. Have tried many things, just wondering if anyone else has run into this on Ubuntu. Am checking in samba forums, also. 
Thanks

---

