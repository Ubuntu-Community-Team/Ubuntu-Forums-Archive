---
title: "how to disable network configuration and clock syn"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by mysurface on 2005-06-23
i Wanna disable network configuration and clock syn , coz it took me few minutes to boot up, damn irritating, did anyone know how?

---

### Post by elvis on 2005-06-24
The cheat's way to temporarily remove services is to change their init files to not be executable.

For instance, ntpdate is the service that runs to sync your clock with a remote server.  You can temporarily disable it by typing

```

sudo chmod 000 /etc/init.d/ntpdate

```

To set it back again, type

```

sudo chmod 755 /etc/init.d/ntpdate

```

Or alternatively, remove the package all together via apt-get or Synaptic.

```

sudo apt-get remove ntpdate

```

Be very careful which services you disable however.  If you turn off something vital, you may lose important functionality on reboot.

For networking, simply comment out the sections in your /etc/network/interfaces file that refer to any network adaptors.  If an adaptor is not defined in that file, it will not initialise on reboot.

---

### Post by mysurface on 2005-06-24
thankyou, i would like to disable it, coz it seriously slow down my booting.

---

