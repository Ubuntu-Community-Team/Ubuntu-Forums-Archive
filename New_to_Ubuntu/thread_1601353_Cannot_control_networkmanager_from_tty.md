---
title: "Cannot control networkmanager from tty"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by dimoftheyard on 2010-10-20
Hello there,

I am using Kubuntu 10.10, but lately I wanted to use networkmanager without having Xorg running. I tried with nmcli, but "nmcli con" says

```
** (process:11521): WARNING **: fetch_connections_done: error fetching user connections: (2) The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files.
```

It only displayes the wired connection, but no wlan networks. When KDE is running there is no problem, both nmcli and the plasma-applet find the wlan networks.
Is there any service I have to start to get org.freedesktop.NetworkManagerUserSettings or should that not be necessary? I would appreciate any hint on that.
Thanks :)

---

### Post by ubudog on 2010-10-21
Iwconfig?  

```
man iwconfig
```

---

### Post by matgates on 2010-12-04
I have the same issue.  I would like to use nmcli to start network manager connections from within the awesome wm, but it gives the error the OP gave above.

IIRC network manager is necessary when handling WPA connections, so iwconfig is no good.  Perhaps this information is out of fate though (last time I used iwconfig was a while ago).

---

### Post by matgates on 2010-12-04
Installing the package network-manager-gnome made it work...  not only does the nm-applet program itself work, but it also fixes nmcli.

I sense a missing dependency to network-manager-gnome.  However this seems undesirable in kubuntu, so maybe it should be filed as a bug.

---

