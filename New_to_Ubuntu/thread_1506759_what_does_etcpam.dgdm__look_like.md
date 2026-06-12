---
title: "what does /etc/pam.d/gdm  look like"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Periswell on 2010-06-10
Hello

I've been a bit of a twit and completely messed up my '/etc/pam.d/gdm' file without backing it up, and I don't remember what was in it. So I was wondering if anyone could tell me what is in the basic, lucid (10.04), non-edited, version of this file please. Thank you in advance.

-Joshua

---

### Post by flanagan on 2010-06-10
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

---

### Post by SlidingHorn on 2010-06-10
> **flanagan said:**
> ```
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

+1

mine's exactly the same as this...

---

### Post by sisco311 on 2010-06-10
You can run:
```
dpkg -S path/to/file
```
to find the package which provides the conffile.

Rename the file, then run:
```
sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install **package**
```
to force the package manager to reinstall the package and to install the missing conffile(s). 

NOTE: this will reinstall ALL the missing conffiles provided by the package.

---

### Post by Periswell on 2010-06-10
thank you, it seems to be fixed now

-joshua

---

### Post by atsor on 2011-08-06
> **sisco311 said:**
> You can run:
```
dpkg -S path/to/file
```
to find the package which provides the conffile.

Rename the file, then run:
```
sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install **package**
```
to force the package manager to reinstall the package and to install the missing conffile(s). 

NOTE: this will reinstall ALL the missing conffiles provided by the package.

Thak you very much. You saved me many hours of my life.
Only for bigger begginers "lamas" than me 

rosta@rosta-desktop:~$ dpkg -S etc/pam.d/gdm
gdm: /etc/pam.d/gdm-autologin
gdm: /etc/pam.d/gdm

the package name is gdm :D:D:D:D

---

### Post by sisco311 on 2011-08-06
> **atsor said:**
> Thak you very much. You saved me many hours of my life.
Only for bigger begginers "lamas" than me 

rosta@rosta-desktop:~$ dpkg -S etc/pam.d/gdm
gdm: /etc/pam.d/gdm-autologin
gdm: /etc/pam.d/gdm

the package name is gdm :D:D:D:D

You are welcome!

---

