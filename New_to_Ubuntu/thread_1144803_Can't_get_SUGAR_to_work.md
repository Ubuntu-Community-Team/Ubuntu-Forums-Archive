---
title: "Can't get SUGAR to work"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Angus77 on 2009-05-01
Trying to get Sugar set up for my kids on Jaunty.  Unfortunately, they're only allowed to enter their name, choose a colour scheme, and then they're automatically logged out.  After that, every time they log in, they're immediately logged out.

~/.xsession-errors gives this

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/lib/python2.6/dist-packages/jarabe/desktop/meshbox.py:19: DeprecationWarning: the sha module is deprecated; use the hashlib module ins\
tead
  import sha
/usr/lib/python2.6/dist-packages/jarabe/desktop/keydialog.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5

```

---

### Post by moosehadley on 2009-05-08
I'm having the same problem.
This is my output when I run sudo sugar-emulator.

```

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.644" is not allowed to own the service "org.x.config.display100" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.644" is not allowed to own the service "org.x.config.display100" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
matchbox: keyboard does not appear to have a <alt> key.
matchbox: ignoring key shortcut <Alt>return=fullscreen

/usr/lib/python2.6/dist-packages/jarabe/desktop/meshbox.py:19: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/usr/lib/python2.6/dist-packages/jarabe/desktop/keydialog.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5


```

---

