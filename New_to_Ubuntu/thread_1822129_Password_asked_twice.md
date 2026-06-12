---
title: "Password asked twice"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by Yen-lo-wang on 2011-08-10
Hello Folks,

hope I'm right here. 

Recently, I updated my ubuntu version from 10.04 to 11.04. Basically everything went ok, but whenever I login I get asked for my password twice, now. Funny thing is, the first password entry can be anything at all (right, wrong, none, doesn't matter). The second has to be the right password, or the process starts all over again. 

When I try to login as sudo in terminal, same thing happens. It looks like that:

...$ sudo -i
Password: (Entry doesn't matter)
[sudo] Password for MYNAME: (has to be the right one)

It is not a big thing, but it annoys me. ;) So if someone has some thoughts on that, I'd be glad. :)

Best regards,
Yen

---

### Post by TeoBigusGeekus on 2011-08-10
Quite old, but it's the only thing I could find.
[http://ubuntuforums.org/showthread.php?t=503976]("http://ubuntuforums.org/showthread.php?t=503976")

---

### Post by Yen-lo-wang on 2011-08-11
Hey thanks. I read the post and seems the guy had quite the same problem. ;) Now my gdm file looks a bit different than his and I can't really figure out what the codelines do.

So if someone could take a look at this and tell me what to change, I am willing to do it. :P

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

---

