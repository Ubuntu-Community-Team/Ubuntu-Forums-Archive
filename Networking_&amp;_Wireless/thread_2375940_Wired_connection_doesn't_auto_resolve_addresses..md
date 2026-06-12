---
title: "Wired connection doesn't auto resolve addresses."
date: 2017-10-28
forum: Networking &amp; Wireless
---

### Post by again? on 2017-10-28
Ubuntu-gnome 17.04
After a recent update my connection stopped auto resolving addresses when I rebooted.
I could ping **172.217.9.142** but not **google.com**.

The machine has been set to use a static LAN address with automatic DNS.
I have used this setting through reboots for months without problem and use the same setup in my 16.04 install on the same machine which still works.
[ATTACH=CONFIG]277321[/ATTACH]

Now, only resolves IP addresses if I turn off auto DNS and enter my ISP's DNS server.
[ATTACH=CONFIG]277322[/ATTACH]

_/var/log/apt/history.log_:
```
Start-Date: 2017-10-27  09:46:34
Commandline: apt upgrade
Requested-By: glen (1000)
Upgrade: libsystemd0:amd64 (232-21ubuntu5, 232-21ubuntu7.1), libsystemd0:i386 (232-21ubuntu5, 232-21ubuntu7.1), google-chrome-stable:amd64 (62.0.3202.62-1, 62.0.3202.75-1), udev:amd64 (232-21ubuntu5, 232-21ubuntu7.1), vivaldi-stable:amd64 (1.12.955.38-1, 1.12.955.42-1), libudev1:amd64 (232-21ubuntu5, 232-21ubuntu7.1), libudev1:i386 (232-21ubuntu5, 232-21ubuntu7.1), libudev-dev:amd64 (232-21ubuntu5, 232-21ubuntu7.1), **libnss-myhostname:amd64 (232-21ubuntu5, 232-21ubuntu7.1)**, systemd-sysv:amd64 (232-21ubuntu5, 232-21ubuntu7.1), libpam-systemd:amd64 (232-21ubuntu5, 232-21ubuntu7.1), systemd:amd64 (232-21ubuntu5, 232-21ubuntu7.1),** libnss-resolve:amd64 (232-21ubuntu5, 232-21ubuntu7.1)**, wget:amd64 (1.18-2ubuntu1, 1.18-2ubuntu1.1)
End-Date: 2017-10-27  09:47:12
```

Anyone know if there are related bugs for libnss-resolve or libnss-myhostname?

---

