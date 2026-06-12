---
title: "How to connect with WAN Miniport PPPoE"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by alket on 2008-12-28
Im using windows xp in my lap top
and I just installed Ubuntu in my PC
but i can't connect on the internet
All I need to do is
to change my ubuntus MAC Address and to connect through WAN Miniport PPPoE with Username And Password.

---

### Post by alket on 2008-12-28
please help me :confused::confused:

---

### Post by alket on 2008-12-28
> **babaroga said:**
> please help me :confused::confused:

i need it urgently :S:S

---

### Post by lswb on 2008-12-28
Substitute the correct interface name for eth0 and desired ethernet address where I have 01:23 ....

From the command line "sudo ifconfig eth0 hw ether 01:23:45:67:89:AB

or in put in /etc/network/interfaces:

auto eth0  
iface eth0
hwaddress ether 01:23:45:67:89:AB

You may not need the line "auto eth0" Note that the entry in /etc/network/interfaces may keep NetworkManager from using that interface.

---

### Post by alket on 2008-12-28
i used it, but when i restart my pc, it isnt saved.

what should i do

---

### Post by lswb on 2008-12-28
Putting the line in /etc/network/interfaces (which must be edited as root) will persist accross reboots. The ifconfig command will not but you could put it in /etc/rc.local or perhaps add it to /etc/ppp/pppoe_on_boot or a similar script if your setup uses one.

---

