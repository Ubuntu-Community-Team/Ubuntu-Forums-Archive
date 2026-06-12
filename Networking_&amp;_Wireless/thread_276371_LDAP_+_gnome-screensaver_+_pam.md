---
title: "LDAP + gnome-screensaver + pam"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by bdwalton on 2006-10-12
Hi All,

I've been banging my head on this one for a while and can't seem to find a resolution.

I have a working ldap server (ldaps) that I can authenticate all of my services (gdm, ssh, tty login, apache basic, etc) against perfectly.  The only problem I have is with gnome-screensaver.  It always fails when unlocking the screen for an ldap-based account.  Standard passwd/shadow accounts work fine.

I've downloaded the source .deb and walked through much of the code without finding any real issues there.  The test-passwd program fails with the following output:
```
bwalton @ pinkfloyd : ~/temp/gnome-screensaver-2.14.3/src
$ ./test-passwd
gnome-screensaver-Message: priv initializing PAM passwords
gnome-screensaver-Message: priv initializing normal passwords
encrypted_user_password is FALSE. EUID is 1000
(process:26730): gnome-screensaver-WARNING **: priv initialization of normal passwords failed.
Returning from 'privileged_initialization ()'
gnome-screensaver-Message: initializing PAM passwords
Password:

name: bwalton

gnome-screensaver-Message: pam_start ("gnome-screensaver", "bwalton", ...) ==> 0 (Success)
gnome-screensaver-Message:    pam_set_item (p, PAM_TTY, ":0.0") ==> 0 (Success)

gnome-screensaver-Message:      PAM ECHO_OFF("Password: ") ==> password
gnome-screensaver-Message:    pam_authenticate (...) ==> 7 (Authentication failure)
gnome-screensaver-Message:    pam_set_item(p, PAM_USER, "root") ==> 0 (Success)
gnome-screensaver-Message:      PAM ECHO_OFF("Password: ") ==> password
gnome-screensaver-Message:    pam_authenticate (...) ==> 7 (Authentication failure)
gnome-screensaver-Message:  pam_end (...) ==> 0 (Success)
Incorrect

```

Has anyone else encountered this problem?  The googling I've done turns up a few vague references to similar issues and points out that the pam code in gnome-screensaver isn't all that hot (which I'd somewhat agree with), but nothing that has helped me.  I'm currently resorting to killing the screensaver from tty1 to unlock my screen (which also means I need to restart the screensaver process when I switch back to $DISPLAY).

Any and all help is welcome!

Thanks
-Ben

---

### Post by gnomeza on 2006-11-15
Possibly related, I've been unable to get either GDM or gnome-screensaver to work with two-factor authentication (using the pam_usb module). login and su work perfectly.

The only change I made was to add the pam_usb required line to pam.d/common-auth

:(

---

### Post by SgtPepperKSU on 2007-04-10
> **gnomeza said:**
> Possibly related, I've been unable to get either GDM or gnome-screensaver to work with two-factor authentication (using the pam_usb module). login and su work perfectly.

The only change I made was to add the pam_usb required line to pam.d/common-auth

:(

I am currently in the same place. ](*,) 

Did you ever get it working?

---

