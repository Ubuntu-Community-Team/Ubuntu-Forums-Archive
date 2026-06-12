---
title: "Vpn configuration does not appear in NetworkManager"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by toniocus on 2008-10-08
Hi,

I'm using ubuntu 7.10 (upgraded from 5.10), I'm trying to
configure my vpn, but the configuration option does not
appear in my NetworkManager.

All packages needed where installed (network-manager-pptp, pptp-linux),
networking disable/enabled, I rebooted, etc but it never appeared.

On the other side, in my laptop with ubuntu 8.04 (installed from scratch),
all things went right.

Any help (except reinstall from scratch),
will be greatly welcomed

thanks in advance
tonio

---

### Post by toniocus on 2008-10-10
I found it,

There is a known bug in gnome NetworkManager (found in internet), that
don't shows the VPN option if there is not at least one network adapter with
Roaming Mode enabled.

After doing it, all worked fine (with some extra manual configuration) but
it did.

Thanks for your attention
tonio

---

