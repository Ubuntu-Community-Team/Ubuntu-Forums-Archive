---
title: "Firewall by default?"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by gjtoth on 2007-05-06
I'm running Feisty and need to know if the firewall is set up and running by default.  How can I find out if it's up and running?

---

### Post by MRiGnS on 2007-05-06
Well, the firewall is built into the kernel and no ports are opened by default.

```
man iptables
```

for a manual on iptables

you also can install firestarter (gtk/gnome) or kmyfirewall (KDE) if you want a GUI.

---

### Post by gjtoth on 2007-05-06
> **MRiGnS said:**
> Well, the firewall is built into the kernel and no ports are opened by default.

```
man iptables
```

for a manual on iptables

you also can install firestarter (gtk/gnome) or kmyfirewall (KDE) if you want a GUI.

Many thanks for the quick response!

---

