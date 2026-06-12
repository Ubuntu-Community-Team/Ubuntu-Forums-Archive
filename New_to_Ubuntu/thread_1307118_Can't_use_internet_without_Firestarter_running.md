---
title: "Can't use internet without Firestarter running"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by foska on 2009-10-30
I have been having some trouble getting onto the Internet recently. I find that I have to have the Firestarter firewall program running to access the Internet.  I upgraded to 9.10 as soon as it was available but it did not help. Anyone have any ideas on how this could be resolved?

---

### Post by lovinglinux on 2009-10-30
First, completely remove Firestarter:

```
sudo apt-get purge firestarter
```

Then cleanup your firewall rules:

```

sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

This should clear all firewall rules. Reboot and test it just to make sure.

If you need to setup the firewall, install [gufw](apt:gufw). Is the graphical frontend for UFW (uncomplicated Firewall), which is installed by default, but not enabled.

---

### Post by foska on 2009-10-31
Thanks. I tried it and it worked.

---

