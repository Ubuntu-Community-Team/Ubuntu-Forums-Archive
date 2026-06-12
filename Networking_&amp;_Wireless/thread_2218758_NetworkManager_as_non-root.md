---
title: "NetworkManager as non-root"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by alexclifford47 on 2014-04-21
After installing Ubuntu 14.04 I can't seem to use the NetworkManager (nm-applet) as a non-root user. I get a bunch of authorisation messages.
If I log directly in as root I can create new connections, connect ot Wifi, create VPNs etc, all fine. As any other admin user all VPN options are greyed out, I cannot create new ones and I cannot touch existing Wifi connections.
Is there something different with the account permissions in 14.04 that I need to add other users into so they can manage NetworkManager?
I tried adding a non-root admin user into netdev group as suggested on an arch forum topic about nm-applet too without any change. I've also tried the /etc/NetworkManager/NetworkManager.conf managed=true fix suggested on other forum posts and I've tried killing nm-applet when logged in and re-launching it.

---

### Post by alexclifford47 on 2014-04-22
The issue is caused by /etc/pam.d/account-* changes to allow sssd ldap login to work. I had puppet automatically changing the default Ubuntu 14.04 install. But I've removed all puppet classes and added one at a time to find out which one broke the funcitonality. I've attached a screenshot showing the greyed out and disabled options in the NetworkManager after the following changes are made.

If the pam.d/common-* files have their Ubuntu 14.04 defaults then the NetworkManager works for a non-root local user just fine. Adding these changes (which then allows ldap sssd login to work) breaks the Network Manager for the local user (as well as all other non-root users). Obviously I'm looking to make sssd ldap logins work but also to keep the NetworkManager working. I'm playing around with these options to find out which one breaks this but if anyone knows or can point me in the right direction that would be appreciated.

/etc/pam.d/common-account:
```
account    required                    pam_unix.so
account    sufficient                    pam_localuser.so
account    sufficient                    pam_succeed_if.so uid < 500 quiet
account [default=bad success=ok user_unknown=ignore]    pam_sss.so
account    required                    pam_permit.so
```

/etc/pam.d/common-auth:
```
auth    [success=3 default=ignore]    pam_unix.so nullok_secure try_first_pass
auth    requisite            pam_succeed_if.so uid >= 500 quiet
auth    [success=1 default=ignore]    pam_sss.so use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so
auth    optional            pam_group.so use_first_pass
```

/etc/pam.d/common-password:
```
password    sufficient    pam_unix.so obscure sha512
password    sufficient    pam_sss.so use_authtok
password    required    pam_deny.so
```

/etc/pam.d/common-session:
```
session    required            pam_mkhomedir.so skel=/etc/skel/ umask=0077
session    optional            pam_keyinit.so revoke
session    required            pam_limits.so
session    [success=1 default=ignore]    pam_sss.so
session    required            pam_unix.so
```

---

### Post by alexclifford47 on 2014-04-23
If I change the files back to the following a local user works again (can use NetworkManager just fine etc) but obviously sssd/ldap login is then disabled.

common-account:
```
account    [success=1 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    requisite            pam_deny.so
account    required            pam_permit.so
```
common-auth:
```
auth    [success=1 default=ignore]  pam_unix.so nullok_secure
auth    requisite           pam_deny.so
auth    required            pam_permit.so
auth    optional            pam_cap.so
```
common-password:
```
password    [success=1 default=ignore]  pam_unix.so obscure sha512
password    requisite           pam_deny.so
password    required            pam_permit.so
password    optional    pam_gnome_keyring.so
```
common-session:
```
session [default=1]         pam_permit.so
session requisite           pam_deny.so
session required            pam_permit.so
session optional            pam_umask.so
session required    pam_unix.so 
session optional    pam_systemd.so
```

---

### Post by alexclifford47 on 2014-04-23
It sound like bug [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=743159](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=743159). I will try to see if I can manually build this on Ubuntu 14.04 to test if that works with my configuration alongside sssd/ldap logins. If I make any progress I'll post an update.

---

### Post by alexclifford47 on 2014-04-23
No further progress yet. If anyone has any ideas of what can be configured in /etc/pam.d/common-* files to make sssd/ldap work without breaking nm-applet for non-root users that would be appreicated.

Thanks

---

### Post by alexclifford47 on 2014-04-23
The same puppet configuration for pam.d/common-* works fine on Ubuntu 13.04 (allowing nm-applet to work for non-root users and also have sssd/ldap logins working). Could it be a ConsoleKit/dbus thing?

---

