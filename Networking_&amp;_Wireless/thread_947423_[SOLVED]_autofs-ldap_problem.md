---
title: "[SOLVED] autofs-ldap problem"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by karde on 2008-10-14
hi,

i have a running system with an ldap server and several clients with  ubuntu 7.04 and 7.10. now i would like to update on ubuntu 8.04. after some configuration the ldap client is working with 8.04 and im able to login with an ldap account. 
normaly there should be a /home and a /misc directory mounted, both with autofs. but only /misc is mounted and not /home. 
autofs gets the mount-maps from ldap. on the ldap server the nfs manages the exports.

the computer, on which im testing 8.04, has been added to the exports on the server.

```
/etc/init.d/autofs status
```

shows

```

Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=60 --ghost /home ldap ou=auto.home,dc=a,dc=b,dc=c 
/usr/sbin/automount --timeout=60 --ghost /misc ldap ou=auto.misc,dc=a,dc=b,dc=c 

Active Mount Points:
--------------------
/usr/sbin/automount --pid-file=/var/run/autofs/_misc.pid --timeout=60 --ghost /misc ldap ou=auto.misc,dc=a,dc=b,dc=c 

```

syslog:
```

automount[8179]: /home: mount failed!

```

/etc/ldap/ldap.conf
```

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

HOST    server1
BASE    dc=a,dc=b,dc=c 
URI     ldaps://server1
TLS_CACERT /etc/key/key.pem
TLS_REQCERT never

```

as mentioned, with ubuntu 7.04 and 7.10 everything works fine....just 8.04 is acting like this.:confused:


maybe i havent noticed some major changes in autofs from 7.XX to 8.04?
or is there some conf file in which i can activate the /home mountpoint? (although im quite shure that there is nothing like that!)

thanks in advantage for the oncoming replies.

best regards,
karde

---

### Post by karde on 2008-10-16
hi,

i have solved the problem.
the cause, why autofs refused to mount the home-directory was, that i hab an local user on the computer. so the home for this local user was mounted automaticily at boot.
to ensure that you can use local and ldap accounts:

if there are other local users than root, which you want to use, then copy their home to another directory on your drive. if you've done that, you have to change the path to the homedirectory of the user. for this, just change the path to the /home in passwd for the local users.

after changing the path for the home directories you have to edit the /etc/fstab. in the fstab file, you have to change the options for /home to noauto. now the /home directory wont be mounted on boot and autofs can work without problem (this problem/bug with autofs appeard with 8.04, i think).

if there are problems with the permissions of the home for local users just use:

```

sudo chown localuser:localuser ~localuser -R
sudo chmod -R u+rwX ~localuser
sudo chmod 600 ~localuser/.dmrc

```

after that reboot or restart nscd and autofs and everything should work!

regards,
karde

---

