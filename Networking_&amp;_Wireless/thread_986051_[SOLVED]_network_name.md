---
title: "[SOLVED] network name"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-11-18
is it possible to use a different Host Name other than the computer's name?

for e.g : my computer name is : goofy-laptop , when I connect to my router is see it like that under the 'DHCP Table' , but is it possbile to keep the computer name as is , and change the host name?

---

### Post by StOoZ on 2008-11-18
yes , sort of , check /etc/hostname file...:)

---

### Post by Iowan on 2008-11-18
You can configure /etc/dhcp3/dhclient.conf to send a different name to tor router via the **send host-name "my computer";** option.  I may be missing the distinction between "computername" and "hostname".

---

