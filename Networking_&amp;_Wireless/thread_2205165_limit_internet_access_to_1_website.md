---
title: "limit internet access to 1 website"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by graham9 on 2014-02-12
Is there a way I can configure Xubuntu so that I can only access 1 website from it?

It will be connected to a small LAN in a shop but I would like the other pc's to be able to still access any website?

Thanks for any help
Xubuntu

Xubuntu
Xubuntu

---

### Post by aromo2 on 2014-02-12
In the firewall (iptables?), disable web access by default with one exception to the address that you want to allow.  Use man pages for specifics.

---

### Post by graham9 on 2014-02-13
> **aromo2 said:**
> In the firewall (iptables?), disable web access by default with one exception to the address that you want to allow.  Use man pages for specifics.

Is that within Xubuntu itself or on the router?

I dont want to do it on the router because I still want the other pc's to access the internet

---

### Post by SeijiSensei on 2014-02-13
On the PC itself you can use:

```

/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 80 -j REJECT
/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 443 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 443 -j REJECT

```

That allows HTTP and HTTPS traffic to ip.of.ok.site, but not anywhere else.  These rules do allow outbound traffic to other ports.  If you don't want that use this instead:

```

/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 443 --j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```

Given the application you intend, you may want some intermediate level of access.  For that, you'd need to spend some time learning about iptables rules.

If the machine has multiple interfaces, say one pointing to the Internet and another pointing to a local network, you probably should include the "-o eth0" parameter to limit the rule's application to the outbound interface. (If eth1 points to the Internet, use that instead of eth0.)  For instance

```

/sbin/iptables -A OUTPUT -o eth0 -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j REJECT

```

---

### Post by graham9 on 2014-02-13
> **SeijiSensei said:**
> On the PC itself you can use:

```

/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 80 -j REJECT
/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 443 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 443 -j REJECT

```

That allows HTTP and HTTPS traffic to ip.of.ok.site, but not anywhere else.  These rules do allow outbound traffic to other ports.  If you don't want that use this instead:

```

/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -d ip.of.ok.site --dport 443 --j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```

Given the application you intend, you may want some intermediate level of access.  For that, you'd need to spend some time learning about iptables rules.

If the machine has multiple interfaces, say one pointing to the Internet and another pointing to a local network, you probably should include the "-o eth0" parameter to limit the rule's application to the outbound interface. (If eth1 points to the Internet, use that instead of eth0.)  For instance

```

/sbin/iptables -A OUTPUT -o eth0 -p tcp -d ip.of.ok.site --dport 80 --j ACCEPT
/sbin/iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j REJECT

```

Thanks for that - will have a look at that tomorrow and hopefully I will be able to figure it out (:confused:)

---

