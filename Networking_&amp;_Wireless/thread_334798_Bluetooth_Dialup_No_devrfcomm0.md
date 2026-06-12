---
title: "Bluetooth Dialup No /dev/rfcomm0"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by igb on 2007-01-09
I have used Bluetooth Dialup as described in the wiki with Dapper for some time. I recently installed Edgy (Kubuntu) from scratch and am trying to set it up again.

When I try to connect using pon BluetoothDialup I get the following error:

/usr/sbin/pppd: In file /etc/ppp/peers/BluetoothDialup: unrecognized option '/dev/rfcomm0'

It seems that /etc/init.d/bluetooth isn't creating /dev/rfcomm0. Any ideas why this is happening and how to fix it?

Ian.

---

### Post by Asix on 2007-01-11
Yeah I have the exact same problem, too. I don't know how to fix that. I only know that there's an error with init.d, because when I type ```
sudo /etc/init.d/bluez-utils restart
``` I get the following ```
sudo: /etc/init.d/bluez-utils: command not found
```
I don't know why it doesn't restart bluez-utils, because it should...

---

### Post by Epeli on 2007-06-24
I've got same problem with feisty. Any ideas?

---

### Post by xluryan on 2007-07-06
I would try "sudo /etc/init.d/bluetooth restart" instead.

---

