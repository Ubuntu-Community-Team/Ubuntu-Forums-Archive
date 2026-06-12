---
title: "Hide Password in wpa_supplicant.conf"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by staticsage on 2007-10-24
I use wpa_supplicant to connect to my university wired network. It requires 802.1X authentication, so my wpa_supplicant.conf looks like this:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=0
network={
key_mgmt=IEEE8021X
eap=PEAP
identity="username"
password="Password"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}
```

The password= shows the password in plain text. I was wondering if there is a way to hide it.

I know I can set the permissions so that only root can read the file, but on a dual boot system, Windows does not care about file permissions.

Is it possible to have the keyring take care of this password as it does for wireless networks? I think it would be good to include 802.1X for wired in NetworkManager, and it shouldn't be too hard to implement. Would this benefit enough other people to have it seriously considered? Is this something I should open a launchpad bug/blueprint on?

Thanks in advance.

---

### Post by staticsage on 2007-10-26
There is a bug open to include 802.1X for wired connections: [http://bugzilla.gnome.org/show_bug.cgi?id=434902](http://bugzilla.gnome.org/show_bug.cgi?id=434902)

---

