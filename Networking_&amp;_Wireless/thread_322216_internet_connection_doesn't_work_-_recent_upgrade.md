---
title: "internet connection doesn't work - recent upgrade"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by aleksanteri on 2006-12-20
So I recently upgraded from Kubuntu Dapper to Edgy, but in that upgrade i lost my internet connection, which worked fine on Dapper.

Usually it's my interfaces. But now when I tell it to enable the eth0 interface it says "Can't modify, you have to modify manually". I have used commands like ifconfig, ifup, ifdown and no sign has worked. The interface can be enabled but no connection stil... :confused:

---

### Post by n00b@linux on 2006-12-20
I'm speculating but maybe the Edgy kernel modules differ from those in Dapper.
Has the kernel module for your ethernet's chipset been loaded properly?
 
Do you get the same problem after a restart (sudo /etc/init.d/networking restart)?
Also check your configuration file (/etc/network/interfaces)

---

### Post by aleksanteri on 2006-12-20
> Do you get the same problem after a restart (sudo /etc/init.d/networking restart)?

I tried it but i get "Permission Denied" errors and "network down" errors in the console :| perhaps it's this?

---

### Post by n00b@linux on 2006-12-20
Permission denied?  You DID type the command exactly as I put it - prefixed with 'sudo' - didn't you?

---

### Post by aleksanteri on 2006-12-20
Ye, and that's the weird part :|

Note that the command WAS accepted by bash. It's the command that says permission denied :confused:

---

