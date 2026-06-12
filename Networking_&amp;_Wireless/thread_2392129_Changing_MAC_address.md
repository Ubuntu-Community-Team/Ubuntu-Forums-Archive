---
title: "Changing MAC address"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by dave1122 on 2018-05-17
Hi I've changed the MAC address using the commands

sudo ifconfig en01 down
sudo ifconfig en01 hw ether 00:00:00:00:00
sudo ifconfig en01 up

When I do ifconfig afterwards it has applied the changed.  However if I open the 'Wired Network' window it still has the orginal values, likewise if I click on the 'Edit' button it still shows the orginal details.  I've tried adding the new MAC address into the 'Cloned MAC address' variable but it still makes no difference.

Why dont they all match up?

Also, it always reset the MAC address everytime the system reboots, is there anyway of forcing it to keep the value?

Thanks.

---

