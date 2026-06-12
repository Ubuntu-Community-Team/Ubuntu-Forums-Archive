---
title: "How to understand 20.04 networking?"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by raoul-markus on 2020-09-26
Hi, 

I do linux since 25 years, but I am on the verge on giving up on Ubunutu 20.04.
- my router should do the DNS. Nevertheless, my Ubuntu is "discovering" machines by machinename-<counter>. I.e. the router has someserver.fritz.box, my Ubuntu discovers the printserver as someserver-5.fritz.box. Ping works both on someserver and on someserver-5. I did no-where add someserver-5.
- same for the printer. Printer shows up automatically, every time Ubuntu is launched with a different name, sometimes working, sometimes not. I can add a new printer in cups, but the other one keeps popping up.
I guess that dnssd and avahi are automatically misconfiguring my system, but I really don't have a clue which services are running locally. I would like to do the network config on my own with full control.

so please, where is precise info how that works in Ubuntu 20.04 desktop?

Thansk, & Best regards,

---

### Post by TheFu on 2020-09-26
if you  want control disable avahi, resolvconf, systemd.resolved, purge network manager and configure all the settings in /etc/netplan/ and resolv.conf manually.

Some things will stop working, but if your network is well-managed and dns knows about all the devices, it shouldn't matter too much.  Printer setup will be slightly harder, but still easy.  Jest be certain that static IPs are used for anything with a network service.

---

