---
title: "removing nm-applet?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Psumi on 2009-11-22
How do I remove nm-applet without removing network-manager? Because nm-applet shows my wired network device as "device not managed" even though I clearly can browse the Internet.

---

### Post by RedSingularity on 2009-11-22
You will have to remove the area of the panel called "notification area".  Right click and remove.

---

### Post by gradinaruvasile on 2009-11-22
> **RedSingularity said:**
> You will have to remove the area of the panel called "notification area".  Right click and remove.

Thats a bit harsh. You will lose all tray icons.
Just go in the startup applications, uncheck nm-applet.

Check your /etc/network/interfaces file. What does it contain?

---

### Post by Psumi on 2009-11-22
> **gradinaruvasile said:**
> Thats a bit harsh. You will lose all tray icons.
Just go in the startup applications, uncheck nm-applet.

Check your /etc/network/interfaces file. What does it contain?

This is what it shows:
```
psumi:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by Ocxic on 2009-11-22
Edit /etc/network/interfaces to have a # in front of the last 2 lines, and then reboot. that should nm-applet working.

---

### Post by Psumi on 2009-11-22
> **Ocxic said:**
> Edit /etc/network/interfaces to have a # in front of the last 2 lines, and then reboot. that should nm-applet working.

That worked, thank you so much.

---

