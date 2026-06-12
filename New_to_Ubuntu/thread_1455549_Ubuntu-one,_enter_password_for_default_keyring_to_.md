---
title: "Ubuntu-one, enter password for default keyring to unlcock"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-16
I installed the gnome client for ubuntu one, and made a password for the keyring that is the same as root password. However now it annoyingly asks for this password every time i log on. I looked for solutions on the web, but all i found were solutions using gnome menus and options, that ofc i don't have (as i am using kubuntu). I just don't want to have to put my password in again, immediately after log on

---

### Post by Didius Falco on 2010-04-16
are you using auto-login or typing your password manually?

---

### Post by Falc7 on 2010-04-16
Typing it in manually

---

### Post by Didius Falco on 2010-04-16
Have a look through these two threads - one may have the solution for you:

[http://ubuntuforums.org/showthread.php?t=1286031](http://ubuntuforums.org/showthread.php?t=1286031)

[http://ubuntuforums.org/showthread.php?t=1455530](http://ubuntuforums.org/showthread.php?t=1455530)

I hope it solves it for you....

Regards,

Didius

---

### Post by Falc7 on 2010-04-16
Unfortunately not, the first solution is using a gnome only menu, and the 2nd one, i don't have the file present that i am supposed to edit

Perhaps this file could be relevant?
```
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password	[success=1 default=ignore]	pam_unix.so obscure sha512
# here's the fallback if no module succeeds
password	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
password	optional	pam_gnome_keyring.so 
password	optional	pam_ecryptfs.so 
# end of pam-auth-update config

```

---

### Post by Falc7 on 2010-04-16
Ah this seems to be working for me so far:
[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

---

