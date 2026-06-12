---
title: "setting up static IP on ubuntu 16.04"
date: 2018-04-24
forum: Networking &amp; Wireless
---

### Post by fretagi on 2018-04-24
Hi

I am trying to setup a static IP address on a ubuntu 16.04 server running as guest on vmware player.
my configuration file ```
/etc/network/interfaces
``` has the following content:

```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens33
iface ens33 inet static
    address 10.100.32.251
    netmask 255.255.254.0
    gateway 10.100.32.254
iface ens33 inet dhcp 

```

the error I am getting when running ```
ifdown ens33
``` is the following:
```

/etc/network/interfaces:1: misplaced option
ifdown: couldn´t read interfaces file "/etc/network/interfaces"

```

Any ideas what could be wrong

---

### Post by fretagi on 2018-04-24
Hi
I did made a mistake on a letter, but now I have the following error:

```

ifdown ens33
ifdown: interface ens33 not configured

```

---

### Post by chili555 on 2018-04-24
Your interface shouldn’t be declared as static and dhcp at the same time. As well, if you expect to reach the internet, you need dns-nameservers.

---

