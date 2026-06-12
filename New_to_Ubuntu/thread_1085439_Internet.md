---
title: "Internet"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-03
Problem connecting to internet resolved by going into 

gksudo gedit /etc/network/interfaces

and editing the code to read

auto eth0
iface eth0 inet dhcp

Now the issue is that the network icon in the notification area displays a cross and says that the wired network is unmanaged.

Right click the icon and selecting connection information I am told no valid connections found!

How can I correct this minor irritation?

---

### Post by msidhard on 2009-03-03
What is the os version u use.

---

### Post by gdn1947 on 2009-03-03
Sorry i forgot that, its 8.10

---

