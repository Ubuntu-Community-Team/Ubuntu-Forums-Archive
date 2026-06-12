---
title: "keyring nm-applet ANNOYING"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by hairyharry7 on 2008-04-10
i understand that this is a well covered topic but i'm still struggling with this....i've tried the two different methods that i've seen, both requiring you to append the /etc/pam.d/gdm file...with one method it says add this to the end:
```
@include common-pamkeyring
```
when i try this i can't login to ubuntu because at the login screen an error message keeps popping up that says login failed...
so i tried method 2-add this to the end of your gdm file:
```
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```
this did nothing...
here's what my gdm file looks like (with these two methods commented out...)
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so  auto_start
@include common-password

#METHOD 1
#@include common-pamkeyring

#METHOD 2
#auth optional pam_keyring.so try_first_pass
#session optional pam_keyring.so

```

thanks for any help...
-HH

---

