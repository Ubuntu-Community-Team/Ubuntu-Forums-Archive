---
title: "LDAP client: graphical login not possible"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by hanwurst123 on 2014-02-25
Hello,

I am using ubuntu server 13.10 and want to configure it as a ldap client.
I configured it as described in the server guide. Login on the terminal is possible, but it takes really long (1 minute or so).
Login graphically, with lightdm does not work.
/var/log/auth.log shows the error message
```
 pam_systemd(login:session): Failed to create session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security 
policy blocked the reply, the reply timeout expired, or the network connection was broken.
```
the systemd entry is in /etc/pam.d/common-session:
```
session optional        pam_systemd.so

```

After I deselect " Register user sessions in the systemd control group hierarchy" in pam-auth-update, login on terminal is faster, but graphical login does not work, since gnome, which I use, needs somehow systemd. Moreover the login manager lightdm freezes sometimes.

On ubuntu 12.04 the ldap client works great using the same ldap-server and the same configuration as in ubuntu 13.10. Ubuntu 12.04 does not use systemd.

Any ideas what I can do?
Thank's for help
Cheers

---

### Post by hanwurst123 on 2014-02-26
If nobody had the same problem as me before or has an idea how to solve my problem:

Has somebody running a ldap client using ubuntu 13.10 and can explain me how he configured it, please?

---

