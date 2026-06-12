---
title: "Wireless driver de-activated  after every reboot..."
date: 2009-04-10
forum: New to Ubuntu
---

### Post by jondgls on 2009-04-10
System info:
Wireless adaptor - Atheros AR5413 802.11abg NIC 
Driver - ath5k (compat-wireless)

This is where I obtained the drivers and instructions to get the wireless card working:
[http://wireless.kernel.org/en/users/Download#Wheretodownload]("http://wireless.kernel.org/en/users/Download#Wheretodownload")

Everything works fine, however, every time I reboot I have to manually go to System > Administration > Hardware Drivers and activate "Support for 5xxx series of Atheros 802.11 wireless LAN cards." with admin privileges.  

As you can imagine this = Really annoying.

Is any one aware of a fix or script for the issue? I read somewhere there might be a work around by adding a modprobe command into the /etc/rc file but this doesn't sound right. Can't find any other solutions.

Thank you in advance

---

### Post by mikewhatever on 2009-04-12
If you built the driver from source, there is no need to mess with the Hardware Drivers utility in Ubuntu. On the other hand, why build it, if it was avalable in the first place?

---

### Post by jondgls on 2009-04-12
> **mikewhatever said:**
> If you built the driver from source, there is no need to mess with the Hardware Drivers utility in Ubuntu. On the other hand, why build it, if it was avalable in the first place?

Ubuntu comes with the proprietary drivers "Support for Atheros 802.11 wireless LAN cards."

These drivers did not work with my Atheros AR5413 wireless card so I was forced to build new drivers. The problem is I can not get them to stay activated or at least activate them automatically on start up.

JonDgls

---

### Post by shad0w_walker on 2009-04-12
running this in a terminal:

```
gksu gedit /etc/modules
```

Should open the list of extra modules to load on boot. Try adding the name of your module on it's own line and saving. Next boot it should load up automatically.

---

### Post by jondgls on 2009-04-12
> **shad0w_walker said:**
> running this in a terminal:

```
gksu gedit /etc/modules
```

Should open the list of extra modules to load on boot. Try adding the name of your module on it's own line and saving. Next boot it should load up automatically.

How can I determine what the name of the module is?

Thank you,
JonDgls

---

### Post by shad0w_walker on 2009-04-13
From the look of your first post, I believe your driver module name is:

```
ath5k
```

---

