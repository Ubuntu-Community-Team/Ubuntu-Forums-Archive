---
title: "pam_mount, pam_ldap and screen unlocking"
date: 2015-09-16
forum: Networking &amp; Wireless
---

### Post by Chris_82 on 2015-09-16
Hi all,

I am having trouble getting these three components to work in an ldap environment:
- authenticate the ldap user 
- mount a folder (type cifs) on login using pam_mount
- be able to unlock the screen once it is locked by gnome-screensaver

When it comes to the mounting and unlocking, I never get both, only one at a time.

/etc/pam.d/common-auth
mount: ok
screen unlocking: not ok
```
auth	required	pam_env.so
auth	optional	pam_mount.so
auth  sufficient    pam_ldap.so use_first_pass
auth	sufficient	pam_unix.so nullok_secure use_first_pass
auth	required	pam_group.so use_first_pass
auth	required	pam_deny.so

```


/etc/pam.d/common-auth
mount: not ok
screen unlocking: ok
```
auth	required	pam_env.so
auth  sufficient    pam_ldap.so
auth	sufficient	pam_unix.so nullok_secure use_first_pass
auth	optional	pam_mount.so use_first_pass
auth	required	pam_group.so use_first_pass
auth	required	pam_deny.so

```

I invested quite some time already without a full success.
Any help is appreciated.

Client setup is: Ubuntu 14.04 with lightdm

---

