---
title: "Network Manage/DBus problem? (Feisty)"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by W. James MacLean on 2007-07-12
I can't seem to get Network-Manager to run properly under Feisty. The 'nm-applet' icon shows in the panel, and it lists available wireless networks, but when I try to select one, nothing happens. The following error message does appear in /var/log/syslog:

[FONT="Courier New"]Jul 12 15:43:07 localhost NetworkManager: nm_ap_security_new_deserialize: assertion `dbus_message_iter_get_arg_type (iter) == DBUS_TYPE_INT32' failed
Jul 12 15:43:07 localhost NetworkManager: <WARNING>^I nm_dbus_nm_set_active_device (): nm-dbus-nm.c:288 (nm_dbus_nm_set_active_device): Invalid argument (wireless security info).
[/FONT]

Now, I don't think it's a hardware problem, as if I boot the same machine with the Feisty LiveCD, Network-Manager appears to work OK. I'm guessing it's a configuration problem, but other than /etc/network/interfaces, what else could be wrong?

Throughts?

James

---

