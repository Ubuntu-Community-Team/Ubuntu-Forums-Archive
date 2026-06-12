---
title: "[SOLVED] system drops previously static ip address"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by mcystems on 2008-06-27
Hi all!

[INDENT]Does anybody know why Ubuntu Hardy drops statically set ip address after a minute or two? NetworkManager was previously uninstalled so I use ifconfig to set ip address.[/INDENT]

thanks,
mcystems

---

### Post by plewisfdx on 2008-06-27
Not sure why it would drop it, but you should go to "System->Administration->Network" and put the correct values in the settings of that device.  

Then just check the box to enable/disable the connection.

This populates /etc/network/interfaces for you, and then the check box runs "ifup eth0" or whatever your interface is.

Having the info in /etc/network/interfaces may provide you with better consistency.

---

### Post by Iowan on 2008-06-27
Sounds like the kind of thing **dhclient** would do if it were running. You could try renaming **/etc/dhcp3/dhclient.conf** and restarting.

---

### Post by mcystems on 2008-07-03
thanks all, both ways are working

---

