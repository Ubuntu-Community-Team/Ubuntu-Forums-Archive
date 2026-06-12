---
title: "Reinstall routing table?"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by QuickGold on 2008-04-17
Here's the situation.  While logged into my Apache box via webmin, I deleted a default gateway option which has royally messed up connecting to the box.  I want to set all my networking options back to default.  

How do I restore the routing table to it's default state? Or, how do I fix the issue?

---

### Post by SpaceTeddy on 2008-04-17
read the default gateway via webmin (there is an option for it), or reboot the system (if the settings have not been written yet.

on the system side, you need to edit your /etc/network/interfaces and add the entry gatway to the network card that connects to the internet.

entry should look like this
```
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        **gateway 192.168.0.254**
        broadcast 192.168.0.255

```

of course you will need to put the right default gateway in.

---

### Post by QuickGold on 2008-04-18
I looked in /etc/network/interfaces and the ethernet card has an entry for gateway listed there

---

### Post by Paris Heng on 2008-04-18
> **SpaceTeddy said:**
> read the default gateway via webmin (there is an option for it), or reboot the system (if the settings have not been written yet.

on the system side, you need to edit your /etc/network/interfaces and add the entry gatway to the network card that connects to the internet.

entry should look like this
```
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        **gateway 192.168.0.254**
        broadcast 192.168.0.255

```

of course you will need to put the right default gateway in.

Hi, use the command route to manipulate your kernel routing table. See, [http://linux.die.net/man/8/route]("http://linux.die.net/man/8/route")

---

