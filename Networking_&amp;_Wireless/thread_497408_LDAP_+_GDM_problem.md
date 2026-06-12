---
title: "LDAP + GDM problem"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Max-B on 2007-07-10
Hi,
I configured my Ubuntu 7.04 to authenticate users over an LDAP server.

Here is a part of my /etc/nsswitch.conf
```
password:        compat ldap
group:              compat
shadow:           compat ldap
```

And here is what I changed in my /etc/pam.d/ files:
/etc/pam.d/common-auth:
```
auth    sufficient      pam_unix.so nullok_secure
auth    required        pam_ldap.so use_first_pass
```

/etc/pam.d/common-account:
```
account       sufficient   pam_unix.so likeauth nullok
account       required   pam_ldap.so use_first_pass
```

/etc/pam.d/common-session:
```
session required pam_mkhomedir.so skel=/etc/skel umask=0002
session required        pam_unix.so
```

The authentication works perfectly, but I have a problem with gdm. If I terminate the user's session the system show me a black screen. I can hear the bongo of the login window, but nothing appear. 

If I reboot the machine everythings works.
If I remove ldap in nsswitch.conf also I'm able to terminate the user's session without problems.

Could someone help me?
ciao,
Max-B

---

