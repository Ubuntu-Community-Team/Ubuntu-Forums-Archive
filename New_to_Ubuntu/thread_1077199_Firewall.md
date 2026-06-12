---
title: "Firewall"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by rams123 on 2009-02-22
Which firewall is used in Ubuntu ?

---

### Post by brian_p on 2009-02-22
> **rams123 said:**
> Which firewall is used in Ubuntu ?

Choose one from the hundreds of hits you get when you search these forums.

---

### Post by rams123 on 2009-02-22
Is there any firewall pre-installed ? Sorry for n00b  question..

---

### Post by brian_p on 2009-02-22
> **rams123 said:**
> Is there any firewall pre-installed ? Sorry for n00b  question..

iptables (provided by the kernel) is available for packet filtering.

---

### Post by mcduck on 2009-02-22
All Linux firewall us iptables/netfilter which is a built-in feature of the Linux kernel. You just need some tool to set up rules for it to work with, and this can be done either by writing your own script to load the rules on boot, or by using some firewall configuration tool.

Ubuntu includes a command-line tool, ufw, for this purpose. For graphical tools I recommend Gufw. Firestarter is also popular but it's been unmaintained for a while now.

Anyway, the most important thing here is that by default you don't need a firewall at all. The default Ubuntu install doesn't have any running services that would listen for incoming network connections. You only need to set up a firewall if you install such software, like server programs. (even in that case a firewall isn't absolute necessity, usually proper configuration of the server itself is enough.)

---

### Post by binbash on 2009-02-22
Iptables

---

### Post by wangsuda on 2009-02-22
> **rams123 said:**
> Which firewall is used in Ubuntu ?Go to System>Administration>Synaptic Package Manager and search for gufw. When you find it, install it. It is the interface for the built-in Ubuntu firewall. Very user-friendly.

---

### Post by nkri on 2009-02-22
You could also try Firestarter...it's very easy to use for someone who knows nothing about firewalls (I dunno if that's you or not, but just the same, it's very easy to use and understand).  This is in Synaptic, or you could go into a Terminal (Applications>Accessories>Terminal) and type:
```
sudo apt-get install firestarter
```
Good luck!
-nkri

---

