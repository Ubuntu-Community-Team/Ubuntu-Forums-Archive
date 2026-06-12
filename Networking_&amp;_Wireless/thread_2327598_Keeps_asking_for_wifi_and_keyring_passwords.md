---
title: "Keeps asking for wifi and keyring passwords"
date: 2016-06-12
forum: Networking &amp; Wireless
---

### Post by jacatone on 2016-06-12
I'm using Xubuntu 14.04. Lately, it keeps asking me for my wifi and a keyring password everytime I boot up. This has been an issue with XFCE for I don't know the last 20 years. Was there ever a fix for this?

---

### Post by jeremy31 on 2016-06-13
Is package gnome-keyring installed ```
dpkg -l | grep keyring
```

---

### Post by jacatone on 2016-06-13
This what I get with that command:

jacatone@4600:~$ dpkg -l | grep keyring
ii  gnome-keyring                              3.10.1-1ubuntu4.2                       i386         GNOME keyring services (daemon and tools)
ii  libgnome-keyring-common                    3.8.0-2                                 all          GNOME keyring services library - data files
ii  libgnome-keyring0:i386                     3.8.0-2                                 i386         GNOME keyring services library
ii  libp11-kit-gnome-keyring:i386              3.10.1-1ubuntu4.2                       i386         GNOME keyring module for the PKCS#11 module loading library
ii  libpam-gnome-keyring:i386                  3.10.1-1ubuntu4.2                       i386         PAM module to unlock the GNOME keyring upon login
ii  python-gnomekeyring                        2.32.0+dfsg-3                           i386         Python bindings for the GNOME keyring library
ii  ubuntu-keyring                             2012.05.19                              all          GnuPG keys of the Ubuntu archive
jacatone@4600:~$

---

### Post by jeremy31 on 2016-06-13
Are you using the auto login?

---

