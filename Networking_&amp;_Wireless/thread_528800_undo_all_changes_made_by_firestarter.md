---
title: "undo all changes made by firestarter?"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by NewWithoutClue on 2007-08-18
doesn't seem like apt-get removing it undid all the changes it made.. help.


Thanks,
Paul

---

### Post by ruibernardo on 2007-08-18
Try 

```
sudo apt-get remove --purge firestarter
```to remove the configuration files too. 

If iptables is still working with firestarter rules, flush them. You might have to put iptables chains in "ACCEPT":

```
sudo iptables -X
sudo iptables -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

```Or, more simpler, reboot Ubuntu after you uninstalled firestarter. :)

---

### Post by NewWithoutClue on 2007-08-18
awesome, thanks.

---

### Post by Fr@nKy on 2007-12-21
> **epimeteo said:**
> Try 

```
sudo apt-get remove --purge firestarter
```to remove the configuration files too. 

If iptables is still working with firestarter rules, flush them. You might have to put iptables chains in "ACCEPT":

```
sudo iptables -X
sudo iptables -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

```Or, more simpler, reboot Ubuntu after you uninstalled firestarter. :)

Puting iptables chains in accept is the same as the default after Ubuntu installation?? And does really a reboot do the same?

---

### Post by ruibernardo on 2007-12-24
Merry christmas Fr@nky,

yes, iptables in accept is the default behaviour of iptables in Ubuntu, when it is installed.

If you do remove Firestarter (or any other firewall script you have installed as firewall) and reboot (without any firewall script installed), iptables will be executed without any rule and should have the same behaviour as when Ubuntu was first installed. The scripts just execute some rules to iptables. Firestarter does it too, if it was correctly installed and configured. If you remove it and reboot, nothing will be executed.

---

