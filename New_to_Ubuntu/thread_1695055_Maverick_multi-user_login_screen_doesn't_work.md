---
title: "Maverick multi-user login screen doesn't work"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by CompBio on 2011-02-25
I posted on another thread some issues I was having with the Maverick (10.10) login splash screen.  Now it's becoming a more serious issue, as I've added an account for my wife but she can't log in.

If I edit /etc/gdm/custom.conf and change AutomaticLoginEnable to "false" (or modify the settings using System->Administration->Login Screen), I get the expected login splash screen.  But when I click either username, the splash screen flickers briefly, but that's it.  There is no opportunity to enter a password.

The only way to get back in again is to use Ctl-Alt-F1, sudo edit the /etc/gdm/custom.conf file to change AutomaticLoginEnable back to "true" and reboot.

Has anyone else ever seen this?  If so, were you able to fix it?

---

### Post by CompBio on 2011-03-02
This must be platform-specific.  I've tried multiple logins on an ASUS EEE netbook with both Ubuntu 10.10 Desktop and Ubuntu 10.10 Netbook.  No problems with multiuser on those.

Comparing the logins side-by-side it looks like it's having trouble expanding the login dialog to provide the password text-entry field.

This is on an Acer Aspire 5736z.

---

