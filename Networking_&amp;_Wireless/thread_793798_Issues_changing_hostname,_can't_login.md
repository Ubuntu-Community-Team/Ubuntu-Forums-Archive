---
title: "Issues changing hostname, can't login"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by miser872 on 2008-05-14
I am using Xubuntu hardy.  I have tried the GUI as well as the command line hostname to change my computer's name.  I have tried manually editing /etc/hostname and /etc/hosts.  No matter what I do I get an error after login that kicks me right back to the welcome screen.  It works again if I change it back to the hostname I assigned it at install time.

here is what the message box refers me to:

.xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-AqdkIe5800/agent.5800
```

---

### Post by hermes0710 on 2008-05-14
Are there any other entries like ssh-????? in the tmp folder?

---

