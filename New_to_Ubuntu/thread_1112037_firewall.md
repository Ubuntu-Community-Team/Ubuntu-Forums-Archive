---
title: "firewall"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-03-31
and security for Ubuntu 8.10?

---

### Post by sisco311 on 2009-03-31
[thread=510812]Ubuntu Security[/thread]

---

### Post by ibuclaw on 2009-03-31
Ontop top of that excellent howto by bodhi, you should look up **gufw**, and set **default deny** on it (It will by default deny all inbound traffic that you haven't asked for).

The Linux Firewall is built-in, and is persistent as a background process. You don't need to worry about the absence of an icon on your Desktop.

Regards
Iain

---

### Post by Bendihossan on 2009-03-31
Firestarter is a neat little firewall application for Ubuntu. You can find it in the Ubuntu repros. It's also configurable for certain features. Definitely worth trying out!

---

### Post by tarps87 on 2009-03-31
> **Bendihossan said:**
> Firestarter is a neat little firewall application for Ubuntu. You can find it in the Ubuntu repros. It's also configurable for certain features. Definitely worth trying out!

Thought I would make it clear that Firestarter is a gui configuration not the firewall is self (iptables is the firewall, which is installed by default) therefore does not need to be run on boot.

---

