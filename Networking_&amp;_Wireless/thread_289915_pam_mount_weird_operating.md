---
title: "pam_mount weird operating"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by vm76 on 2006-10-31
I've a pam_mount problem : pam_mount is never executed or gdm ask me my password twice. 
I want to use the use_first_pass feature but it is ignored even if i've found a lot of web pages showing this type of conf :

auth optional pam_mount.so use_first_pass
session optional pam_mount.so use_first_pass

So i'm obliged to do stupid stuff i don't want to force the pam_mount.so working correctl ; my /etc/pam.d/gdm is

auth    requisite       pam_nologin.so
auth    required        pam_env.so
auth    sufficient      pam_usb.so allow_remote=1
auth    required        pam_mount.so
auth    sufficient      pam_winbind.so use_first_pass
auth    required        pam_unix.so use_first_pass
account sufficient      pam_winbind.so
account required        pam_unix.so
password sufficient     pam_unix.so obscure min=4 max=50 md5
session required        pam_limits.so
session required        pam_unix.so
session optional        pam_mount.so
session optional        pam_foreground.so

explanations:
1) if my usb key is plugged in i can login without a password
   -> but session pam_mount.so is still asking "reenter password" (i press enter or type anything and go)

else we go 2) pam_mount.so passes the authentification to pam_winbind
   -> if the samba account is valid i can login and pam_mount does the mounting stuff

else we go 3) unix local account authentification
   -> but session optional pam_mount.so is executed (cause pam_mount is the first module to ask for an auth) and i don't want this (pam_mount is only usefull with a winbind login)

I've tried this order
1) auth sufficient pam_unix.so
2) auth required pam_winbind.so use_first_pass
3) auth optional pam_mount.so use_first_pass
      -> 3.2) auth REQUIRED pam_mount.so use_first_pass
..) session optional pam_mount.so use_first_pass
In this case pam_mount.so is not mounting the samba shares...

So, do i have a solution ?? (maybe use another distrib ? ;)

---

### Post by abovett on 2007-05-14
I've got a similar problem. I'm using the separate common-auth and common-account files etc, but it's effectively the same thing. At the moment I have the following in my common-auth file:
```
auth    sufficient      pam_unix.so nullok_secure 
auth    optional        pam_mount.so try_first_pass
auth    sufficient      pam_winbind.so try_first_pass
auth    required        pam_deny.so

```
I know it's normal to have pam_winbind.so before pam_unix.so but that causes a problem with gksudo (see [_this thread_]("http://ubuntuforums.org/showthread.php?t=215791") and [_this thread_]("http://ubuntuforums.org/showthread.php?t=5409")).

Anyway, this mostly achieves what I want - I can log on with a local (administrative) account using pam_unix.so, and my non-admin users can log in via winbind to the server, and get the appropriate shares mounted via pam_mount.so.

The logons via winbind work fine - the user enters their username and password at the gdm prompts, logs in, and the appropriate shares are mounted. The problem comes when I log in with the local administerative account. I enter username and password, but then get a prompt on the gdm screen "pam_mount reenter password". It's not a major problem, I can reenter the password (probably anything would do) and I can then log in, but it's annoying. I _think_ it's because pam_mount is failing for the local user as that user isn't valid on the network (isn't meant to be) but I'd like to be able to stop it.

I found a sort of work-around - put "auth required pam_mount.so" first and then use "try_first_pass" for pam_unix.so and pam_winbind.so. This gets rid of the extra password prompt, _but_ it makes the gksudo problem come back - basically none of the admin menu irems work :(

So, I'm stuck with the extra password prompt at the moment. Not a disaster, but not right and I'd like to fix it. Any ideas, anyone?

Cheers

Andy B

---

### Post by naborcoj on 2007-07-27
At the *pam-mount *FAQ file there is an instruction that tells that no module above *pam_mount* in the PAM configuration stack should be configured as *sufficient*. The word sufficient tells pam to return if the this module is executed successfully. So, any module with sufficient above *pam_mount* that is executed successfully returns and, by that reason, *pam_mount* is never reached and executed in the stack.

In that case, the solution is to turn any module with sufficient above *pam_mount* to *required *or *optional*.

[]'s
Nabor

---

### Post by abovett on 2007-07-28
> **naborcoj said:**
> 
In that case, the solution is to turn any module with sufficient above *pam_mount* to *required *or *optional*.

Sorry - I think you're missing the point. If pam_unix succeeds, I don't _want_ the others to run, because if I log on as a local user then that username is not valid on the network and I don't want pam_mount or pam_winbind to take effect. It appears to me though that pam_mount is running even when pam_unix has been satisfied. In other words the problem is the opposite to what you are describing - pam_mount _does_ run when I don't want it to, rather than not running when I do.

Thanks

Andy

---

### Post by Yale Zhang on 2008-06-01
Hi. I was trying to solve the same problem and one solution is to put

session    sufficient pam_localuser.so

before the session action for pam_mount. I found this by luck by looking in the /lib/security directory.

---

