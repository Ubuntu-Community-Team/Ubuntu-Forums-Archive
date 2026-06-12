---
title: "ubuntu asks for password twice whenever authentication is needed"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by jetzhou on 2010-11-06
Hi all,

Whenever authentication is needed, Ubuntu asks for my password twice, on login screen when it first starts, on login when it wakes up, on sudo. And it's really strange that I can enter (the same) password on any of the two times, or both, and it just authenticates the same way. It's kind of a nuisance to alway type password and then hit enter key twice...

I've been having this problem for a while now, just I haven't had time to try to fix it, so I forgot when it exactly it happened and what updates I applied. I tried to search online for some solutions but couldn't find any applicable to my problem.

Here are the contents of the couple files that seem to be relevant:


~$ cat /etc/pam.d/common-account 
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# pre_auth-client-config # # here are the per-package modules (the "Primary" block)
# pre_auth-client-config # account	[success=1 new_authtok_reqd=done default=ignore]	pam_unix.so 
# pre_auth-client-config # # here's the fallback if no module succeeds
# pre_auth-client-config # account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
# pre_auth-client-config # account	required			pam_permit.so
# pre_auth-client-config # # and here are more per-package modules (the "Additional" block)
# pre_auth-client-config # account	required			pam_krb5.so minimum_uid=1000
# pre_auth-client-config # # end of pam-auth-update config
account sufficient      pam_krb5.so debug
account sufficient      pam_unix.so debug
account required        pam_permit.so



~$ cat /etc/pam.d/common-auth 
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# pre_auth-client-config # # here are the per-package modules (the "Primary" block)
# pre_auth-client-config # auth	[success=2 default=ignore]	pam_krb5.so minimum_uid=1000
# pre_auth-client-config # auth	[success=1 default=ignore]	pam_unix.so nullok_secure try_first_pass
# pre_auth-client-config # # here's the fallback if no module succeeds
# pre_auth-client-config # auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
# pre_auth-client-config # auth	required			pam_permit.so
# pre_auth-client-config # # and here are more per-package modules (the "Additional" block)
# pre_auth-client-config # # end of pam-auth-update config
auth    [authinfo_unavail=ignore success=1 default=2] pam_krb5.so use_first_pass ignore_root debug
auth    [success=done default=ignore]   pam_unix.so nullok_secure debug
auth    [default=done]  pam_ccreds.so action=validate use_first_pass
auth    [default=done]  pam_ccreds.so action=store
auth    [default=bad]   pam_ccreds.so action=update



~$ cat /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password




I thought that these two lines:
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale

could be causing the problem, so I tried to comment one out, but it didn't help.

Could someone advise me other things to try? Thanks a lot!

---

### Post by Gone fishing on 2010-11-06
They look modified to me - did you play with ldap authentication or something?

here are mine

common account
```
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# here are the per-package modules (the "Primary" block)
account	[success=1 new_authtok_reqd=done default=ignore]	pam_unix.so 
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

common auth
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

gdm
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

I'm using 10.04

---

### Post by jetzhou on 2010-11-06
hmmm, that does look very different. I never played with these files or any alternative authentication methods though, just the normal updates, I'm also running 10.04.

the gdm file is exactly the same though, which I thought was the most important file in the sequence control. Could I find documentations on what these files do and what the lines mean somewhere on the web?

Thanks!

---

### Post by Gone fishing on 2010-11-07
Why not boot from a live CD rename yours to common-account.old paste in mine and see if it works. If it doesn't you can always remove mine and and rename yours.

---

