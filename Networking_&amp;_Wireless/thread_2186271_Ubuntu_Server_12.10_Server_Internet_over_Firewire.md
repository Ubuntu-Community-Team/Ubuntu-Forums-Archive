---
title: "Ubuntu Server 12.10 Server Internet over Firewire"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by kyleharryjohnson on 2013-11-06
I've been trying without success to get my PPC iBook G4 to use the firewire network connection to access the internet from my Mac OS X with sharing over firewire enable.

I do have a local connection as I can ssh into my server.

It must be able to access the internet because it used the firewire connection to set the system time and get updates during installation.

I have searched google to exhaustion without success.

this is what I have in interfaces:

```
# The primary network interface
auto firewire0
iface firewire0 inet static
        address 169.254.49.10
        netmask 255.255.0.0
        network 169.254.0.0
        broadcast 169.254.255.255
        gateway 169.254.49.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 169.254.49.3
        dns-search nt

```

Any suggestions welcome! many thanks!

---

