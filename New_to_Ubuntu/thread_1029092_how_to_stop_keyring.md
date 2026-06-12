---
title: "how to stop keyring"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by wstay on 2009-01-03
I use evolution mail and whenever I want to send/receive mail, keyring pop-up and I have to enter a password for to unlock keyring. How can I stop keyring running in my computer?

---

### Post by efexD on 2009-01-03
This post should help you.

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

---

### Post by Scunnered on 2009-01-03
efeXor

I similarly experience a problem with my Wi-Fi connection as now and again it keeps asking for a password.

Looking at your link I note that both the logon and the keyring passwords must be the same.  As my broadband connection is the larger of the passwords I will have to change my logon to match. 

Doing this will it cause problems ?

I had attempted to avoid the need of a logon and having followed the instruction on this found that whilst all I had to do was power on the system regularly I was now being asked for a password to establish my Wi-Fi connection. Reverting to a logon reduced the password requests but not by very much.

I would much prefer automatically accessing the Wi-Fi every time without messing about with passwords. 

What would you suggest is the best option ?

---

### Post by wstay on 2009-01-17
> **efexD said:**
> This post should help you.

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

I follow the steps in the post above, but I still have to type in my keyring password (which is the same as my login password) each time I restart my computer and when I want to receive/send mails with evolution.

The following is my /etc/pam.d/gdm file:
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pamkeyring

May be there is a mistake in this file.
Please advise.

---

