---
title: "network issue, eno1 not eth1 interface"
date: 2016-07-23
forum: Networking &amp; Wireless
---

### Post by rgsara on 2016-07-23
I have a new ubuntu 16.04 server install with an xubuntu desktop. The server is running avashi and smb and appears in the clients' finder window. I have ssh setup and working and I can use a remote terminal to access the server. I cannot find a way to remotely access the desktop in any usable way. The client computer(s) run OS X el Capitan (10.10 I think, I have lost track). The issue seems to be something to do with the network settings.
In OS X I can see the ubuntu box but not access it. It will not accept the (correct) password. I can log into the ubuntu box using nomachine from a client, but cannot connect to any of the OS X machines using ssh. The ethernet interface is called eno1 not eth1 as I expected. This seems to be the only part of the puzzle that is not what I expected. What am I missing and what do I need to do to fix it? Googling hasn't provided an answer, so any assistance will be appreciated.

---

### Post by grahammechanical on 2016-07-23
As regards the naming of the ethernet interface I think that is done to an init utility called systemd.

[https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20](https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Regards

---

### Post by rgsara on 2016-07-23
thanks, that explains eno1 but not why i can't get the network connections to work.

---

### Post by SeijiSensei on 2016-07-24
Post the results of the command "ifconfig" inside [noparse]```

```[/noparse] tags.  You don't need sudo for this.

---

