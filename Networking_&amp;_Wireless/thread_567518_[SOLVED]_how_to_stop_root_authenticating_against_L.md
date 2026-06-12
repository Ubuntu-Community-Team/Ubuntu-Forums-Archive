---
title: "[SOLVED] how to stop root authenticating against LDAP"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by brenth on 2007-10-04
Hey all, I have been trying to get LDAP working with a apple OpenLDAP server, and while things are now working, another issue has popped up. It seems that when I try and su to root it is trying to authenticate root via the ldap server.

administrator@ws-047:~$ su
Password:
You are required to change your LDAP password immediately.
Enter login(LDAP) password:

nsswitch.conf

```

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
common-account
```

account sufficient     pam_ldap.so 
account required        pam_unix.so use_first_pass
```

common-auth

```
auth    sufficient      pam_ldap.so 
auth    required        pam_unix.so use_first_pass
```

common-passwd
```

password        sufficient      pam_ldap.so 
password        required        pam_unix.so

```
common-session
```

session required        pam_unix.so use_first_pass
session optional        pam_ldap.so

```
what am I doing wrong?

---

### Post by brenth on 2007-10-04
fixed, sort of. I followed the setting in this post [http://ubuntuforums.org/showthread.php?t=195908](http://ubuntuforums.org/showthread.php?t=195908) and I am up and running.. Only issue, is administrators sudo isn't working correctly, but the sudos file and /etc/groups are all correct. When I type sudo command, and enter my pass, it just goes back to the prompt.

---

### Post by kamazu on 2007-11-20
This might be because of the admin group. If in your sudoers file has the line
```
%admin ALL=(ALL) ALL
```
and
```
getent group admin
```

doesn't return you as member, then you either add yourself to the admin group locally or you create an admin group in ldap and you delete the local group.

Hope this helps

all the best
Manu

---

