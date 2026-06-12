---
title: "Lost XP Connectivity After Upgrade"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by mpierce on 2007-10-20
Upgrade Feisty to Gutsy (minor problems upgrading). Feisty had no previous problems. Backed everything up prior to upgrade. 

Linux server using 2 network cards:
   eth0 192.168.1.250 (dhcp assigned)   #alias "desktop"
   eth1 192.168.1.10 (static)                  #alias "mother"

XP laptop can no longer connect to server access being denied. 

Linux to XP working after editing /etc/network/interfaces file to give eth1 a static address. (Don't understand why this was necessary as it should get it's address from dhcp as desktop does - could be part of the problem... Hmmm)

XP can ping server using IP or alias. Server can ping XP. 

Tkdiff used to compare: hosts, hosts.allow, hosts.deny, smb.conf - no change has occurred. 

/etc/exports has nothing in it and never has. 

Anyone with thoughts/solution as to what is causing this problem appreciated.

---

### Post by mpierce on 2007-10-20
How stupid of me, the upgrade completely wiped out samba. Restoring the smb.conf file from backup has brought connectivity back to life. 

However, I've had to refer to drives using IP address instead of alias.

Does anyone know what the problem is with the alias Mother - eth1 not getting its IP address from dhcp?

---

