---
title: "edgy server text firewall config"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by dguido on 2007-02-14
I'm using edgy server to host Samba, Apache, and SSH.  I'd like to set up some iptables rules to allow HTTP and SSH to be read from any IP address and for Samba to only be accessible to IPs on my subnet, not the entire Internet.  Is there a text-based utility that lets me define these properties?  I absolutely hate working in raw iptables commands.  Thanks!

---

### Post by dguido on 2007-02-17
Fedora has system-config-firewall or something that runs on the console.  You're telling me there's no way to easily configure a firewall from the command line?

---

