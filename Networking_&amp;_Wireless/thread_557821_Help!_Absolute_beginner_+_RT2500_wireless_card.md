---
title: "Help! Absolute beginner + RT2500 wireless card"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by nedwells on 2007-09-23
Hi All,

I installed Ubuntu (6.06 LTS) for the very first time yesterday onto an old Compaq Presario 700. It's an old machine and the ethernet port is bust.

I bought an Asus WL-107g wireless card and am haiving difficulties getting it up and running. Lights are on, on the card, and it shows as 'active' in the network settings. But getting the drivers up and running is something else... for a newbee like me.

Can any one talk me through in very simple terms, what to do to get this card running?

Thanks!

---

### Post by patrickfromspain on 2007-09-23
this card probably won't work with network-manager, uninstall it, reboot, and use the gnome-network utility to make it work.

---

### Post by kevdog on 2007-09-23
Go to the terminal and please post the following:

lspci -nn
lshw -C network
cat /etc/network/interfaces
route -n

---

