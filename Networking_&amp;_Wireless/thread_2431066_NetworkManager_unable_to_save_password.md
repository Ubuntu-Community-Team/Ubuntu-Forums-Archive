---
title: "NetworkManager unable to save password"
date: 2019-11-11
forum: Networking &amp; Wireless
---

### Post by Megagolgoth on 2019-11-11
Hi,

I upgraded from 19.04 to 19.10, and NetworkManager is unable to save user password for an OpenVPN connection. Seems to save-it in Keyring. When i just upgraded, i found that NetworkManager was unable to find the previously saved password.

I checked "journalctl -u NetworkManager", and there is no error/warning message. I tried to reinstall NetworkManager, this change nothing.

Any idea?

---

### Post by praseodym on 2019-11-11
Are you logging in automatically? In that case (old issue?!) the keyring is not encrypted, but it is if you login conservatively.

---

### Post by Megagolgoth on 2019-11-11
I'm not logging automatically.

The keyring open automatically. When I launch Seahorse, I see the keyring opened, no need to type a password.

---

### Post by Megagolgoth on 2019-11-12
It's working for "all user" not for my account. How Network Manager is working with keyring?

There is a daemon running at login:
> [FONT=courier new]$ ps -aux |grep keyring
dje       1618  0.0  0.0 242968  7288 ?        Sl   13:56   0:00 /usr/bin/gnome-keyring-daemon --daemonize --log[/FONT]

---

### Post by Megagolgoth on 2019-12-22
Bug report opened here : [https://gitlab.gnome.org/GNOME/network-manager-applet/issues/59](https://gitlab.gnome.org/GNOME/network-manager-applet/issues/59)

Solution seems to be found and was merged : [https://gitlab.gnome.org/GNOME/network-manager-applet/merge_requests/53](https://gitlab.gnome.org/GNOME/network-manager-applet/merge_requests/53)

So wait and see when the package will be updated in Ubuntu...

---

